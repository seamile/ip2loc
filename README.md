# ip2loc

A CLI tool for querying IP geographical locations, supporting IPv4, IPv6 and domain names.


## Installation

```bash
cargo install ip2loc
```

## Usage

**ip2loc** depends on [Maxmind GeoLite City Database](https://dev.maxmind.com/geoip/geolite2-free-geolocation-data/). You'll need to [create an account](https://support.maxmind.com/knowledge-base/articles/create-a-maxmind-account) and [generate a license key](https://support.maxmind.com/knowledge-base/articles/generate-a-maxmind-license-key) before using it.

1. Initialize

    ```bash
    ip2loc --init
    ```

    During initialization, enter the ID and Key as prompted. The database will be downloaded and stored in `~/.ip2loc/`.

2. Query IP or Domain locations

    **ip2loc** can query multiple addresses at once, including IPv4, IPv6, and domain names.

    ```bash
    ip2loc 192.168.1.1 1.1.1.1 8.8.8.8 maxmind.com

    192.168.1.1                                 -  / - / -
    1.1.1.1                                     HK / Hong Kong / Hong Kong
    8.8.8.8                                     US / California / Mountain View
    maxmind.com -> 162.159.134.22               US / California / San Francisco
    maxmind.com -> 162.159.135.22               US / California / San Francisco
    maxmind.com -> 2606:4700:7::a29f:8616       US / California / San Francisco
    maxmind.com -> 2606:4700:7::a29f:8716       US / California / San Francisco
    ```

    Optional arguments:

    - `-h`: Show help message.
    - `-f`: Output format, default is `table`, options are `table`, `json`.
    - `-l`: Language, default is `en`, options are `en`, `zh`, `es`, `pt`, `ru`, `ja`, `fr`, `de`.

3. Update database

    Maxmind GeoLite City Database is [updated every Tuesday and Friday](https://support.maxmind.com/knowledge-base/articles/download-and-update-maxmind-databases#update-schedule). You can update the database manually by running the following command:

    ```bash
    ip2loc --update
    ```
