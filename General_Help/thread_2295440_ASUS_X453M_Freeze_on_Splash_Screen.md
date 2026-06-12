---
title: "ASUS X453M Freeze on Splash Screen"
date: 2015-09-18
forum: General Help
---

### Post by anonprophet on 2015-09-18
hi i just want to start learn linux and i think im falling in love with Ubuntu distro

i got problem when booting from live cd to install it

my problem like this thread


[http://ubuntuforums.org/showthread.php?t=2256657](http://ubuntuforums.org/showthread.php?t=2256657)
[http://software.moftalk.com/cannot-install-ubuntu-14-04-on-asus-x453m-5VtnhNED.html](http://software.moftalk.com/cannot-install-ubuntu-14-04-on-asus-x453m-5VtnhNED.html)


i dont know how to run it live (always freeze in splash screen) like carl say 
[http://ubuntuforums.org/showthread.php?t=2256657&p=13186961#post13186961](http://ubuntuforums.org/showthread.php?t=2256657&p=13186961#post13186961)

please anyone, help me

---

### Post by Bashing-om on 2015-09-18
anonprophet; Hello:

Can you boot up the liveDVD ?
Are you certain the download was good ?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Is the burn to DVD good ?
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

If so, provide useful info on the exact hardware graphics :
```

lspci -vnn | grep -i VGA
lspci -vnn | grep -i 3D

```
With the expectation that the boot parameter "nomodeset" may prove beneficial in booting the operating system.

[INDENT][INDENT]we can make it happen
[/INDENT][/INDENT]

---

### Post by anonprophet on 2015-09-18
[COLOR=#000000]Are you certain the download was good ?
[/COLOR]Ya, the checksum passed

[COLOR=#000000]Is the burn to DVD good ?
[/COLOR]Yes, passed too :D

```

ubuntu@ubuntu:~$ lspci -vnn | grep -i VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation ValleyView Gen7 [8086:0f31] (rev 0e) (prog-if 00 [VGA controller])
ubuntu@ubuntu:~$ lspci -vnn | grep -i 3D
ubuntu@ubuntu:~$ 

```

3D nothing show

---

### Post by Bashing-om on 2015-09-19
anonprophet: OK;

So, the liveDVD boots - no problem. The problem is in installing the operating system to the hard drive ?
As that is the case we need to look at the hard drive :
```

sudo parted -l

```
check and see that there is "space" available to install ubuntu.

[INDENT][INDENT]seek and ye shall find
[/INDENT][/INDENT]

---

### Post by anonprophet on 2015-09-20
i got the solution

just change OS Selection from Windows 8.1 to Windows 7
and now freeze on boot or shutdown gone

but, i still have another problem

please see 
[http://ubuntuforums.org/showthread.php?t=2295520](http://ubuntuforums.org/showthread.php?t=2295520)

thanks :D

---

### Post by Bashing-om on 2015-09-20
anonprophet; Great !

Pleased you are up and running.

Looks like you have good assistance on your other thread on the brightness issue. There is nothing I can add to it.

You are making good progress all I can further advise is to remark that "one size does not fit all ". There are those times ->

[INDENT][INDENT][INDENT]one has to tweak a bit
[/INDENT][/INDENT][/INDENT]

---

