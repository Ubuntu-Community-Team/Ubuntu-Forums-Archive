---
title: "nmap - scan from file for port 22, 23 and output save to file"
date: 2017-08-14
forum: General Help
---

### Post by rayyy2 on 2017-08-14
Hello,

I have range of IP subnets specified in test.txt file. I want to scan it for port 22, 23 open. and save only those hosts IP addresses who have port 22, 23 open to output.txt file. how to do it?

I see following path when I issue pwd command:

/home/pc


so Should i save text.txt file (contains IP subnets that I want to scan) in /home/pc directory ? will output.txt file be saved in /home/pc ?

---

### Post by Habitual on 2017-08-14
[masscan]("https://github.com/robertdavidgraham/masscan")

[http://blog.erratasec.com/2013/09/masscan-entire-internet-in-3-minutes.html](http://blog.erratasec.com/2013/09/masscan-entire-internet-in-3-minutes.html)

So fast.

---

### Post by rayyy2 on 2017-08-14
> **Habitual said:**
> [masscan]("https://github.com/robertdavidgraham/masscan")

[http://blog.erratasec.com/2013/09/masscan-entire-internet-in-3-minutes.html](http://blog.erratasec.com/2013/09/masscan-entire-internet-in-3-minutes.html)

So fast.

Thanks. how to do have masscan do scan for ip subnets specified in the file? what will be the command to do masscan to scan port 22, 23 for subnets specified in file text.txt?

---

### Post by Habitual on 2017-08-14
```
sudo vi /etc/mytargets
``` and populate
```
[COLOR="#FF0000"]**range = **[/COLOR]
rate =  100000.00
output-format = list
output-status = all
output-filename = mytargets.xml
ports = 22,23
noshow = closed

### Leave these alone ###
### adapter
adapter-ip = 0.0.0.0
adapter-mac = 00:00:00:00:00:00
router-mac = 00:00:00:00:00:00

### other
exclude-file = /etc/masscan/excludes.txt

```
[COLOR="#FF0000"]**range = **[/COLOR] This is the network you wish to scan

```
sudo touch /etc/masscan/excludes.txt
```

To run it:
```
sudo masscan -c /etc/mytargets
```
After the run, inspect ~/mytargets.xml

---

