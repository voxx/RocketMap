# VSnipe README

A quick guide on using VSnipe to determine CP and Level for players 30 and above.

## Table of Contents

- [Installation](#installation)
- [Configuration](#configuration)
- [Usage](#usage)
- [Support](#support)
- [Contributing](#contributing)

## Installation

Install Requirements
```sh
cd <RocketMap Directory>/Tools/vsnipe/
sudo -H pip install -r requirements.txt
```

VSnipe also requires voxx PokeAlarm fork. (https://github.com/voxx/PokeAlarm)

## Configuration

Copy the example config to config.json
```sh
cd <RocketMap Directory>/Tools/vsnipe/
cp ./config/config.json.example ./config/config.json
```

Set the following values in config/config.json
1) Server "host" - The ip address or host name the VSnipe service will listen on.
2) Server "port" - The unique port that VSnipe service will listen on.

  Ex:
```json
"host":"127.0.0.1",
"port":"14441"
```

3) Hash Key "enabled" - True or False to enable one or more hash keys.
4) Hash Key "key" - The PF Hash key value.

  Ex:
```json
{ "enabled":"True", "key":"HASHKEY1" },
{ "enabled":"False", "key":"HASHKEY2" }
```

VSnipe requires a minimum of 1:10 ratio of low level:level 30+ accounts to work.
You may need to increase this ratio if you are covering large distances or alarm on lots of stuff.

1) Create a new csv file at <RocketMap Directory>/workers/vsnipe.csv
2) Load it with level 30+ accounts in csv format.

Ex:
```csv
ptc,username1,password
ptc,username2,password
```

PokeAlarm Configuration
1) Update your alarms.json templates to include VSnipe dynamic text replacements.

```
<level><cp>
```

## Usage

Start the VSnipe Server
```sh
cd <RocketMap Directory>
python ./Tools/vsnipe/server.py
```

You may optionally specify a custom location for the accounts using the -csv flag.
```sh
cd <RocketMap Directory>
python ./Tools/vsnipe/server.py -csv workers/vsnipe-accounts.csv
```

Start PokeAlarm with the -vsnipe flag to enable updating alarms with CP and level.
```sh
cd <RocketMap Directory>
python ./Tools/PokeAlarm/start-pokealarm.py -vsnipe
```

## Support

VOXX Discord (https://discord.gg/4fNqfa5)

## Contributing

VOXX Github (https://github.com/voxx/RocketMap/)
