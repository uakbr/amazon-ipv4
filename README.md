# Amazon Web Services IPV4 Count
Simple script that counts the number of IP4 addresses owned by AWS.
* Copy, paste, and run:

```py
import urllib.request
import json

with urllib.request.urlopen(' https://ip-ranges.amazonaws.com/ip-ranges.json') as f:
    j = json.loads(f.read().decode('utf-8'))

print('All keys', j.keys())

print('IPV4 prefixes', len(j['prefixes']))

ips = 0
for prefix in j['prefixes']:
    cidr = int(prefix['ip_prefix'].split('/')[1])
    ips += 2**(32-cidr)

print('# IPS', ips)
```
<p align="left"> <a href="" target=""> <img src="https://i.imgur.com/FP6ky07.png" alt="Amazon IPs" /> </a>
  
* This is only possible because Amazon [publishes](https://ip-ranges.amazonaws.com/ip-ranges.json) their entire set of IP addresses as JSON.

* Given this file, we download the JSON -> convert the CIDR blocks to individual IP #'s -> arrive at our grand total of: **109,847,486** IPV4 addresses owned by AWS! 

* Given that there are a total of **4,294,967,296** IPV4 addresses possible; this comes out to **2.55%** of all IPV4 addresses.

The below data is provided by: [IPV4 Market](https://ipv4marketgroup.com/ipv4-pricing/)
Disclaimer: I have not had the time to yet corroborate IPV4 Market's market data itself; I am not saying it is wrong but I would also seek multiple sources if possible.

## How much are AWS IPV4's worth cumulatively? 

Price variations over time and by deal size

<p align="left"> <a href="" target=""> <img src="https://i.imgur.com/8nWpvhO.png" alt="Amazon IPs" /> </a>

You can observe how the market reached a plateau at $15 per IP for several months in 2017, but then accelerated rapidly to $18 per IP. A new plateau at $20 per IP was reached between March and December of 2019, but prices since the start of 2020 have again started to climb.

## Global Size of the IPv4 Market Place
### Number of IPs transferred each year

<p align="left"> <a href="" target=""> <img src="https://i.imgur.com/8PnZnUp.png" alt="Amazon IPs" /> </a> 

The chart above shows the IPs transferred through the RIR’s on a global basis. Total volume is driven by large transfers, consisting of /12s and larger. This has plateaued at almost 70 million IPs transferred each year from 2017 to 2019.
