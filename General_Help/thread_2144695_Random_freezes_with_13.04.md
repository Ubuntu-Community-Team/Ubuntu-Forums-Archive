---
title: "Random freezes with 13.04"
date: 2013-05-13
forum: General Help
---

### Post by barna on 2013-05-13
Hi, I have a Dell Inspiron 1564, with this graphics card: Advanced Micro Devices [AMD] nee ATI RV710/M92 [Mobility Radeon HD 4330/4350/4550].
I have upgraded to 13.04 some weeks ago - I do it very cautiously since most of the time the new releases just do not work (I have two linux system partitions, I install the new release on one of them, and keep the old one on the other, and if the new system fails - which is most often the case - then I just switch back to the old system). 13.04 seemed to work after I removed xserver-xorg-video-radeon (see this thread: [http://ubuntuforums.org/showthread.php?t=2141224](http://ubuntuforums.org/showthread.php?t=2141224)) so I switched to it. But life is not so nice, some programs freeze randomly (firefox, xsane, rekonq, etc) - they do not react to mouse and keyboard events. I can kill and restart them. This is the smaller problem. The bigger problem is that the whole system freezes more and more frequently. Either before or after I log in. This below is part of /var/log/syslog, until the freeze (^@^@^@) Does anyone see  problem here? 
Quite a lot of my time is spent now on making my notebook work. 

```

May 13 09:45:15 nbad11 rtkit-daemon[2010]: Successfully made thread 2013 of process 2008 (n/a) owned by '1000' RT at priority 5.
May 13 09:45:15 nbad11 rtkit-daemon[2010]: Supervising 2 threads of 1 processes of 1 users.
May 13 09:45:15 nbad11 rtkit-daemon[2010]: Successfully made thread 2014 of process 2008 (n/a) owned by '1000' RT at priority 5.
May 13 09:45:15 nbad11 rtkit-daemon[2010]: Supervising 3 threads of 1 processes of 1 users.
May 13 09:45:15 nbad11 bluetoothd[972]: Endpoint registered: sender=:1.44 path=/MediaEndpoint/HFPAG
May 13 09:45:15 nbad11 bluetoothd[972]: Endpoint registered: sender=:1.44 path=/MediaEndpoint/HFPHS
May 13 09:45:15 nbad11 bluetoothd[972]: Endpoint registered: sender=:1.44 path=/MediaEndpoint/A2DPSource
May 13 09:45:15 nbad11 bluetoothd[972]: Endpoint registered: sender=:1.44 path=/MediaEndpoint/A2DPSink
May 13 09:45:22 nbad11 kernel: [   54.302288] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
May 13 09:45:22 nbad11 kernel: [   54.305026] sd 4:0:0:0: [sdb] Asking for cache data failed
May 13 09:45:22 nbad11 kernel: [   54.305036] sd 4:0:0:0: [sdb] Assuming drive cache: write through
May 13 09:45:29 nbad11 dhclient: XMT: Info-Request on eth0, interval 34190ms.
May 13 09:45:40 nbad11 NetworkManager[1178]: <warn> (eth0): DHCPv6 request timed out.
May 13 09:45:40 nbad11 NetworkManager[1178]: <info> (eth0): canceled DHCP transaction, DHCP client pid 1469
May 13 09:45:40 nbad11 NetworkManager[1178]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
May 13 09:45:40 nbad11 NetworkManager[1178]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
May 13 09:45:40 nbad11 NetworkManager[1178]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
May 13 09:46:14 nbad11 kernel: [  105.912018] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
May 13 09:46:14 nbad11 kernel: [  105.914600] sd 4:0:0:0: [sdb] Asking for cache data failed
May 13 09:46:14 nbad11 kernel: [  105.914605] sd 4:0:0:0: [sdb] Assuming drive cache: write through
May 13 09:47:06 nbad11 kernel: [  157.521377] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
May 13 09:47:06 nbad11 kernel: [  157.524076] sd 4:0:0:0: [sdb] Asking for cache data failed
May 13 09:47:06 nbad11 kernel: [  157.524079] sd 4:0:0:0: [sdb] Assuming drive cache: write through
May 13 09:47:39 nbad11 dbus[949]: [system] Activating service name='org.kde.powerdevil.backlighthelper' (using servicehelper)
May 13 09:47:39 nbad11 org.kde.powerdevil.backlighthelper: QDBusConnection: system D-Bus connection created before QCoreApplication. Application may misbehave.
May 13 09:47:39 nbad11 dbus[949]: [system] Successfully activated service 'org.kde.powerdevil.backlighthelper'
May 13 09:47:57 nbad11 kernel: [  209.132872] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
May 13 09:47:57 nbad11 kernel: [  209.135808] sd 4:0:0:0: [sdb] Asking for cache data failed
May 13 09:47:57 nbad11 kernel: [  209.135814] sd 4:0:0:0: [sdb] Assuming drive cache: write through
May 13 09:48:49 nbad11 kernel: [  260.742830] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
May 13 09:48:49 nbad11 kernel: [  260.745766] sd 4:0:0:0: [sdb] Asking for cache data failed
May 13 09:48:49 nbad11 kernel: [  260.745773] sd 4:0:0:0: [sdb] Assuming drive cache: write through
May 13 09:48:54 nbad11 dbus[949]: [system] Activating service name='org.kde.powerdevil.backlighthelper' (using servicehelper)
May 13 09:48:54 nbad11 org.kde.powerdevil.backlighthelper: QDBusConnection: system D-Bus connection created before QCoreApplication. Application may misbehave.
May 13 09:48:54 nbad11 dbus[949]: [system] Successfully activated service 'org.kde.powerdevil.backlighthelper'
^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@
^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@
^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@
^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@
^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@May 13 10:21:09 nbad11 kernel: imklog 5.8.11, log source = /proc/kmsg started.


```

---

### Post by dino99 on 2013-05-13
clean the system as much you can : clean/autoclean/autoremove/gtkorphan/bleachbit
if an xorg.conf is around, delete it (the kernel now deal with X directly)
also check the "additional drivers" activation (software properties / jockey-gtk)
an of course your logs are your best friend to find usefull warnings/errors

---

### Post by barna on 2013-05-14
It is a fresh install. I did not play around with any config files. 

Is it possible to *easily* downgrade the X server to that used in 11.10 (the last release that worked on my notebook)? If not, I will just switch back to 11.10 and used it until my notebook dies. I can not continuously spend a lot of time just making my notebook work. 

Thank you

---

### Post by barna on 2013-05-15
I have just done this:
[https://launchpad.net/~makson96/+archive/fglrx](https://launchpad.net/~makson96/+archive/fglrx)
It went flawlessly, I have fglrx-legacy installed, and now desktop effects are working as well - let's hope the random freezes disappear as well.

---

### Post by VMC on 2013-05-15
I'm now always interested in "random freezes" topics, as I have experienced them since 13.04 and now 13.10.
I don't have AMD's video card, but rather Nvidia. I was going to go the route of downgrading nouveau and/or xorg.server.
Instead I installed Mint14, which is modeled after Ubuntu 13.04. dpkg listing showed I have the same nouveau drivers and xorg server as Ubuntu.
But **no freeze at all!** This is after having it uptime for several hours.

Mint uses muffin and not compiz or mutter. That might have something to do with it.

Using precise and experiencing the freezes, I wan't sure what to make of it. examing kern and sys log, showed my nvidia errors. First I thought it may be the newer kernels. But then I remembered a several releases ago about downgrading, my then Intel video card and it worked.

The problem with that is your stuck in the past. Searching the google world for a long time, only revealed a couple of people complaining about nvidia freezes. [I]Specifally, I have this: GeForce 6150SE/nForce 430 Motherboards.

[/I]My thinking is a log of people testing Ubuntu releases use the virtual machine which doesn't do a good job of ID'ing hadware related issues.

[Here]("http://ubuntuforums.org/showthread.php?t=2112723") and [there]("http://askubuntu.com/questions/231972/nvidia-geforce-6150se-nforce-430") are a couple of posts, but they are hung up on installing nvidia drivers to fix the issue, and not what's causing the orignal freeze, with default drivers.

---

### Post by barna on 2013-05-17
There were no more freezes after this intervention, although I am using my notebook 10 hours a day non-stop. A very big THANK YOU to Tomasz Makarewicz.

---

### Post by barna on 2013-07-08
The random freezes started again, they occur once in every 2-3 days if not more often. It produces coloured squares on the screen. I will never buy a notebook with AMD graphics card again. If anybody has an idea for a failsafe solution (I don't care about any fancy effects. I want a plain graphics display which does not freeze), I would be very grateful.

---

