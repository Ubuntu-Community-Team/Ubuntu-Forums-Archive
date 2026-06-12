---
title: "Pocket PC/Evolution/Ubuntu/synce problems"
date: 2006-10-19
forum: General Help
---

### Post by sandbagger on 2006-10-19
I'm trying to get my PDA to work with ubuntu so I can sync with Evolution and transfer files. I tried this guide [http://ubuntuforums.org/showthread.php?t=30936](http://ubuntuforums.org/showthread.php?t=30936) (I liked this line at the top "At first glance, SynCE and Multisync can seem a bit daunting. But, it really is not nearly as bad as it seems.")
Ok. So I get down to the synce-matchmaker create INDEX part and I get this:
synce-pstatus: Unable to initialize RAPI: An unspecified failure has occurred
damian@ubuntu-desktop:~$ synce-matchmaker create 1
[synce_info_from_file:51] unable to open file: /home/damian/.synce/active_connection
[rapi_context_connect:97] Failed to get connection info
[main:62] Failed to initialize RAPI

Then I tried this fix [http://synce.sourceforge.net/synce/qa.php](http://synce.sourceforge.net/synce/qa.php) but most of the suggestions they give I have no idea how to implement. Someone said I should delete the ~/.synce/active_connection but when I use Nautilus to find it the file's not there.
Can anyone help me out with this? It's a hell of a lot harder than windows where the setup process is just to download activesync.
](*,)

---

### Post by lazyart on 2006-10-24
I installed the multisync package and it worked until I rebooted, giving me the RAPI message.  While I had used ttyUSB0 to connect originally, when I rebooted I got the error until I tried:

sudo synce-serial-config ttyUSB1

Then the connection went like it should using:

sudo synce-serial-start

This is with a Dell Axim x30 running WM2003SE.

---

### Post by jlamorie on 2006-10-31
Whenever you see an error about being unable to open .synce/active_connection, the problem is that you do not have an active_connection to the PDA.

If you do not have any other USB serial devices (cellphones, serial dongles) then you can use the synce-serial-config /dev/ttyUSB0 10.10.0.2:10.10.0.1 followed by synce-serial-start to get things going.

You may also need to get dccm running as well, but I did that a long time ago.

I have a hotplug script that gets all of this going automatically, including determining which USB device to use.  Let me know if you want it.

Joshua

---

### Post by pmilin@ptt.yu on 2006-11-01
Dear Joshua,
It would be wonderfull to have that script. I am having very strange problems with my HP iPAQ 1940. First, I managed, with some RAPI-problems at start, to synce it with Dapper, following: [http://www.ubuntuforums.org/showthread.php?t=30936](http://www.ubuntuforums.org/showthread.php?t=30936). Then, I managed bluetooth connection following: [http://www.ubuntuforums.org/showthread.php?t=50932](http://www.ubuntuforums.org/showthread.php?t=50932). However, now I cannot use USB anymore. Do you know why I lost it? Is there some conflict between USB and bluetooth syncing? Only one synce-serial-config stuff?

Sincerely,
Petar Milin

---

