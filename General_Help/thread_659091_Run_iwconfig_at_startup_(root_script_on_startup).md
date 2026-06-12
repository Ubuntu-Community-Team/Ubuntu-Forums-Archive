---
title: "Run iwconfig at startup (root script on startup)"
date: 2008-01-05
forum: General Help
---

### Post by josephdaniel on 2008-01-05
Hi... 
I've installed Gutsy my Desktop computer and I have successfully set up Internet Connection Sharing on it. It shares my wired internet connection to my laptop via an ad-hoc network.

The problem is that I need to run the script below each time after startup to get the ad-hoc network running. i've tried adding the script to /etc/init.d/rc.local or /etc/init.d/boormisc.sh but neither worked. As much as I understood from other posts; my problem is running a script that requires root user at startup. I've read about cron and tried it but still it doesn't work. 

Could someone please guide me how to do this?

sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode ad-hoc
sudo iwconfig wlan0 channel 10
sudo iwconfig wlan0 essid 'Joe-Ubuntu'
sudo iwconfig wlan0 key off
sudo ifconfig wlan0 up

#sudo dhclient wlan0
sudo ifconfig wlan0 192.168.0.1

sudo /etc/init.d/dhcp3-server start
sudo /etc/init.d/firestarter restart

---

### Post by richardjennings on 2008-01-05
il give it a shot:

```

#!/bin/sh
ifconfig wlan0 down
iwconfig wlan0 mode ad-hoc
iwconfig wlan0 channel 10
iwconfig wlan0 essid 'Joe-Ubuntu'
iwconfig wlan0 key off
ifconfig wlan0 up
ifconfig wlan0 192.168.0.1
/etc/init.d/dhcp3-server start
/etc/init.d/firestarter restart

```

save that code as whatever.sh

Now make the file whatever.sh executable;

```
chmod +x whatever.sh
```

move the file over to /etc/init.d/

```
sudo mv /home/username/Desktop/whatever.sh /etc/init.d/
```


Then make the script run at startup

```
sudo update-rc.d whatever.sh defaults
```

---

### Post by josephdaniel on 2008-01-06
Still doesn't work. After startup, I run iwconfig to see if the wireless network is running but it still doesn't start automatically.

---

### Post by gunbladeiv on 2008-02-10
anyone could help me with this too???
i need to make my snort run everytime i start the box...
please.. anyone?

i got a script has command like this to run:
> sudo snort -c /etc/snort/snort.conf -i eth0 -D

So how can i make it as a startup script and run without needing the sudo command?

---

### Post by kroiz on 2008-03-29
have you solved this?

---

### Post by gunbladeiv on 2008-03-30
i have solve the problem,

try this one(correct me if i'm wrong), 

1.  run "which <program name>" to get where is the binary located.  
2.  then you should edit you rc.local to run the program on start.  To run this, you need root access. 
3.  "sudo vi /etc/rc.local" 
4.  add command line before "exit 0" in the rc.local.

for example,

1.  I run "which snort" and this will return "/usr/local/bin/snort" .(so i know the exact snort locate at /usr/bin)
2.  so i edit my rc.local using vim. 
3.  This is how my rc.local will look like:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

/usr/local/bin/snort -c /etc/snort/snort.conf -i eth1 -D


exit 0

```

---

### Post by kroiz on 2008-04-15
thanks [gunbladeiv]("http://ubuntuforums.org/member.php?u=312055"), That does the trick.

I hear that ubuntu             is moving from System V init daemon (SysVinit) to [Upstart]("http://upstart.ubuntu.com/") init daemon.
I wonder if this file will survive this transition?

---

### Post by gunbladeiv on 2008-04-15
no problem :)

---

