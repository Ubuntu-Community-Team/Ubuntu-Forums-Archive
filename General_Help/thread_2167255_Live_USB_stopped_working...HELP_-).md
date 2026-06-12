---
title: "Live USB stopped working...HELP :-)"
date: 2013-08-13
forum: General Help
---

### Post by pete-petenoto on 2013-08-13
I had 13.04 32bit running great on a Sandisk Extreme USB 3.0 64gb stick.

For the most part I use it on a Toshiba Portege laptop but sometimes on various desktops as well.

I set the usb drive up with unetbootin, I split the drive into roughly two 30gb partitions following this thread  [http://www.howtogeek.com/97177/how-to-put-ubuntu-linux-on-a-usb-thumb-drive-without-the-mess/](http://www.howtogeek.com/97177/how-to-put-ubuntu-linux-on-a-usb-thumb-drive-without-the-mess/) so that I could use it as a thumb-drive as well.

I also partitioned the Live install section following this thread [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent) so that I would have a larger persistence drive.

I also bypassed the unetbootin install or run screen following this thread [http://askubuntu.com/questions/47522/how-to-bypass-try-it-install-screen-when-booting-from-usb-live-session-wit](http://askubuntu.com/questions/47522/how-to-bypass-try-it-install-screen-when-booting-from-usb-live-session-wit) 

All of this worked great and I was a bit proud of myself as I am relatively new to Linux and well...  I had a nice USB thumb drive that worked great for standard file storage and swapping, plus a killer install of Ubuntu that ran VERY fast, loaded right up to the sign in desktop and functioned perfectly!

Then last night I tried to boot up the Toshiba laptop and I found myself staring at the purple loading screen with Ubuntu in the center and the little progress squares lighting up from once side to the other under it.  It hangs there indefinitely.  I've tried it on several systems and I get the same results. 

Here the error message:

[IMG]http://www.stinkinghippie.com/images/rhkUd.jpg[/IMG]

I really do not want to start from scratch as I have the install customized the way I like, loaded with software I want and all set up to my tastes.

Does anyone have any suggestions on how to fix the problem, or for that matter what the actual problem is?

---

### Post by VMC on 2013-08-13
The last two lines reference "getpwuid", which indicates:
```
[EIO]An I/O error has occurred.[EINTR]A signal was caught during *getpwuid*().[EMFILE]{OPEN_MAX} file descriptors are currently open in the calling process.[ENFILE]The maximum allowable number of files is currently open in the system.[COLOR=#000000][FONT=Verdana]The *getpwuid_r*() function may fail if:[/FONT][/COLOR]
[ERANGE] Insufficient storage was supplied via *buffer* and *bufsize* to contain the data to be referenced by the resulting **passwd** structure. 
```

---

### Post by pete-petenoto on 2013-08-13
VMC, you are referring to the two lines that end in "22"?  I did a few Google searches on the line with no avail.  Can you suggest a fix?

---

### Post by VMC on 2013-08-13
There's several errors here. I'm not sure if its not your userid, or what. I've never encountered those errors before.
Can you boot up using live cd and run bootinfoscript (see my blue link below), and copy/paste RESULTS.txt back here.

---

### Post by pete-petenoto on 2013-08-13
VMC, thank you for the followup and suggestion of running boot_info_script.  In a bout of frustration I wiped the drive and started over around 3:00am last night :-)  I have never been a very patient man but I do so enjoy trying to fix things...

---

