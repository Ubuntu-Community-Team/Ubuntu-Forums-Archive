---
title: "Bash telnet scripting"
date: 2007-04-12
forum: General Help
---

### Post by gss6 on 2007-04-12
I'm needing to make a script that when you give the name of  the script, lets call it disconnect, it will telnet into a cisco router and run  ashutdown on a port, disconnecting the room from the network. The arguement will point to a text file and it will pull out the variables (ip to telnet to, and the port number to shutdown. I could make it a long if/then script to set the variables, but i think the text file will make it easier to update, although I know nothing about bash I/O.

Heres something I need the text file to look like.

```

#disconnect.config
#syntax <room> <ip of switch> <switch of port>
cas165 192.168.1.1 1
cas166 192.168.1.2 2
cas168 172.13.0.2 8

```

so that then I give the following command

```
disconnect cas166
```

it will go into the file and pull the ip 192.168.1.2 to telnet to and shutdown port 2

---

### Post by rvbhute on 2007-04-12
Have you looked at **expect**? 

[http://en.wikipedia.org/wiki/Expect](http://en.wikipedia.org/wiki/Expect)

I made a script to reboot my GLB-502T ADSL modem for my ISP's happy hours! First you run through the process yourself - telnetting and noting the prompts that occurs. Then scripting it through expect is very easy. Expect can be installed through  apt-get/synaptic.

---

### Post by bashologist on 2007-04-12
I've never used telnet before, but maybe something like this:
```
#!/bin/bash
if [[ -n "$1" ]]; then
	case "$1" in
		"cas165" )
 			echo "cas165 command here"
		;;
		"cas166" )
 			echo "cas166 command here"
		;;
		"cas168" )
 			echo "cas168 command here"
		;;
	esac
fi
```

---

