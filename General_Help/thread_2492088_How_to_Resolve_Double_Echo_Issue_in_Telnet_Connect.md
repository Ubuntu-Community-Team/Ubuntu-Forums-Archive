---
title: "How to Resolve Double Echo Issue in Telnet Connection Using socat with 'raw,echo=0' O"
date: 2023-10-30
forum: General Help
---

### Post by salehi-mahdi on 2023-10-30
I'm encountering a double echo issue when trying to establish a Telnet connection using the 'socat' command with the 'raw,echo=0' option. This issue is causing unexpected behavior during the Telnet session, and I'm seeking assistance to resolve it.


I have a Telnet server running on a remote machine, and I'm using the following 'socat' command to forward the Telnet connection to a serial device:


```bash
socat tcp4-listen:5050,reuseaddr,fork file:/dev/ttyUSB0,nonblock,raw,echo=0
```
---
command : `telnet 192.168.50.10 5050`


output:


```
Trying 192.168.50.10...
Connected to 192.168.50.10.
Escape character is '^]'.








Company Layer3-Switch 1.0.0 company-switch
company-switch login: 


company-switch login: 
company-switch login: 


company-switch login: 
company-switch login: 
```




---
- Operating System Server: Ubuntu 20.04.6 LTS
- 'socat' Version: socat version 1.7.3.3
- Operating System Client: Ubuntu 22.04.3 LTS
- Telnet Client: 0.17-44build1

---

