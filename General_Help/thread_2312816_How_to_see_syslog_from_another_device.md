---
title: "How to see syslog from another device"
date: 2016-02-07
forum: General Help
---

### Post by shahin on 2016-02-07
I am trying to get syslog from my router, and seems it is sending the messages to my Ubuntu 15.10. I have restarted the syslog but I don't see any logs. I believe I need to configure the file 50-default.conf. I did a tcpdump and see the following:

```
10:36:59.389671 IP 192.168.1.1.1026 > 192.168.1.4.514: SYSLOG user.info, length: 124
	0x0000:  4500 0098 0000 4000 4011 b6ff c0a8 0101  E.....@.@.......
	0x0010:  c0a8 0104 0402 0202 0084 309a 3c31 343e  ..........0.<14>
	0x0020:  4665 6220 2037 2031 303a 3336 3a35 3920  Feb..7.10:36:59.
	0x0030:  3230 3136 2057 6972 656c 6573 735f 4272  2016.Wireless_Br
	0x0040:  6f61 6462 616e 645f 526f 7574 6572 2049  oadband_Router.I
	0x0050:  4e46 4f3a 205b 3730 5d20 5573 6572 2061  NFO:.[70].User.a
	0x0060:  7574 6865 6e74 6963 6174 696f 6e20 7375  uthentication.su
	0x0070:  6363 6573 7320 2855 7365 726e 616d 653a  ccess.(Username:
	0x0080:  2061 646d 696e 2066 726f 6d20 3139 322e  .admin.from.192.
	0x0090:  3136 382e 312e 3329                      168.1.3)

```

Which is how I know I am receiving the log messages. I then did a little research online and found out that Priority = facility*8+level. So given the  output above my facility is 1. Right? and level is 6. I also found out that facility 1 is user-level messages. So I uncommented a line in my 50-default.conf file. This is the line: ```
user.*				-/var/log/user.log
```
I then restarted the syslog service. And waited until the router sent s message and I saw it in the tcpdump. But I do not see a file in /var/log called user.log. Help please. 

Sean

---

### Post by shahin on 2016-02-07
I found the fix [Here]("http://askubuntu.com/questions/53910/how-can-i-receive-syslog-logs-from-a-networked-system")

---

