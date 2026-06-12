---
title: "Run script on startup after network is available"
date: 2014-09-12
forum: General Help
---

### Post by chris137 on 2014-09-12
Hi,
I've been trying to make this work for quite some time but just now I (probably) realized what the problem is.
I want to start a script everytime my PC starts. I already made an entry in crontab, also moved the script to /etc/rc3.d/
Both do not work and here is what I think why:
The script calls up an URL with wget.
Looking closer in my syslog this happens almost directly before the NetworkManager says "<info> (eth0): preparing device."
Clearly no URL can be opened if there is no network.
I assume what I put in /etc/rc3.d/ got executed even earlier.

Long story short:
How do I (maybe even inside the script via if or so) execute the script or rather open those URLs only after the network is available?

---

### Post by anika200 on 2014-09-12
Did you try the sleep command in front of wget in your script. Something like ```
sleep 30 && wget www.google.com
``` or do you need something else?

---

### Post by chris137 on 2014-09-12
This would probably work but is not really what I am looking for.
I want to run it as soon as possible.
The script turns on my screens so I'd like that to happen right after network is available

---

### Post by ian-weisser on 2014-09-12
One way is to use the hook folders in /etc/network.
To run a script each time a network interface comes up, place the script in /etc/network/if-up.d
Your script must be smart enough to recognize if the interface is appropriate (lo vs. wlan1).

Another way is to use the 'nmcli' or 'ip' commands within your script to query the current state of the network.

Another way is to use Upstart ([http://upstart.ubuntu.com/cookbook/](http://upstart.ubuntu.com/cookbook/)), soon to replaced by systemd, to listen for the appropriate network interface to come up.

---

### Post by chris137 on 2014-09-16
Sorry, completely forgot to reply!
ian-weisser had the right idea.
I have this script now(might be laborious but works):
```
#!/bin/bash
x=0
while [ $x == 0 ]
do
v=$(nmcli d | grep "eth0" | gawk '{print $3}')
if [ "$v" == "verbunden" ]; then
/usr/bin/wget --spider "http://internalip/?switchnumber+action"
/usr/bin/wget --spider "http://internalip/?switchnumber+action"
x=1
fi
done
```

---

### Post by ian-weisser on 2014-09-16
Glad you found a way that works, and that you can maintain.

Thanks for posting your solution, and helping others with the same question.

---

