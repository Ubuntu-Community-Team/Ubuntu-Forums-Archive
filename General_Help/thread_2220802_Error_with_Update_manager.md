---
title: "Error with Update manager"
date: 2014-04-29
forum: General Help
---

### Post by BigBaka on 2014-04-29
Dear all,
Recently I tried to update ubuntu 12.04 on a desktop computer (64 bit) i hadn't used in a few months, so several linux headers were downloaded. There was quite  lot of stuff to download so I let it run by itself and went out, but when i came back it would seem that the update process had crashed. I was updating using sudo apt-get dist-upgrade. Not sure if it is relevant but this first crash came back with something like "faliure to write bits: broken pipe" and all I could do was restart. 

Upon restarting - had some following hardware issues which i seem to have finally fixed by plugging in a new power supply to the internal hard drive - I went to do the dist-upgrade again and an error came back saying I had to run sudo dpkg --configure -a . This seem to mostly work, although there was some error at the end. After this I ran sudo apt-get dist-upgrade again and after a process ran into a final error related to update-manager. Now I can't run synaptic, or update manager, nor it seems firefox or google chrome. Other software so far seems OK though. When running dist-upgrade I get the following error.

glenn@GRdesktop:~$ sudo apt-get dist-upgrade
[sudo] password for glenn: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up update-manager (1:0.156.14.13) ...
SyntaxError: ('invalid syntax', ('/usr/lib/python2.7/dist-packages/UpdateManager/UpdateManager.py', 1, 12, 'package CPAN::Shell;\n'))

dpkg: error processing update-manager (--configure):
 subprocess installed post-installation script returned error exit status 101
Errors were encountered while processing:
 update-manager
E: Sub-process /usr/bin/dpkg returned an error code (1)
glenn@GRdesktop:~$ 

Any suggestions for what I can do to get things going again?

Also noticed that my network settings and network (via LAN cable) appear to not work either.

Regards,
BB

---

### Post by ian-weisser on 2014-04-30
Do you want to get the system up and working fast?
Or do you want to explore the problems, fix each one, and learn more about how your system works?

---

### Post by ibjsb4 on 2014-04-30
For the moment just remove update-manager.

```
sudo apt-get remove update-manager
```
then

```
sudo apt-get update && sudo apt-get upgrade
```
If it now worked, reinstall update-manager.

```
sudo apt-get install update-manager
```

---

### Post by BigBaka on 2014-05-26
Thanks for your help guys, after this I realised that a new LTS Ubuntu release had just been put out (aka 14.04) so thought I would just install that instead of trying to deal with this. Alas due to power outage I now have a new issue with my MBR [http://ubuntuforums.org/showthread.php?t=2226285](http://ubuntuforums.org/showthread.php?t=2226285), but for me this issue is solved.

---

