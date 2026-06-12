---
title: "bitcoin transaction security"
date: 2017-10-02
forum: General Help
---

### Post by ktat on 2017-10-02
Hi,

I'm an Ubuntu user who has just got into speculating in the cryptocurrency market.

I've set up a private wallet and now I want to be able to send coins from this wallet to friends.

The way I hoped to do this was to use a live version of Ubuntu (without persistence) and install the Electrum Wallet on it anytime that I wanted to do a transaction.  I think this gives great security as I will always know that I am using a clean OS (no opportunity for key logging or screen capturing software to have been secretly installed).

Unfortunately, when I tried this I have run into a problem.  Following the instructions on [https://electrum.org/#download]("https://electrum.org/#download") doesn't work.

I tried:
```
sudo apt-get update
```

before running:
```
 sudo apt-get install python-qt4 python-pip
```

and still no luck, anyone have any ideas why this isn't working?

---

### Post by ian-weisser on 2017-10-02
What makes you think they are not working?
Are you getting some kind of error messages? If so, what *exactly* do they say? (Accuracy is important)

---

### Post by ktat on 2017-10-02
Hi,

Sorry for my vague post.  I have since had another attempt and noted the outcomes.

After starting up the live USB, I connected to the wireless (no problem), opened firefox and looked up the Electrum download page.

I then opened up a terminal and started with this:
```
ubuntu@ubuntu:~$  sudo apt-get install python-qt4 python-pip
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package python-qt4
E: Unable to locate package python-pip
```

that didn't work, so I tried this:
```
ubuntu@ubuntu:~$ sudo apt-get update
Ign:1 cdrom://Ubuntu 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719) xenial InRelease
Hit:2 cdrom://Ubuntu 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719) xenial Release
Get:4 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]                               
Hit:5 http://archive.ubuntu.com/ubuntu xenial InRelease  
Get:6 http://archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]           
Get:7 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages [358 kB]
Get:8 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages [636 kB]
Get:9 http://archive.ubuntu.com/ubuntu xenial-updates/main Translation-en [266 kB]
Get:10 http://security.ubuntu.com/ubuntu xenial-security/main Translation-en [159 kB]                                                         
Get:11 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11 Metadata [305 kB]                                                    
Get:12 http://security.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [60.3 kB]                                                 
Get:13 http://archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons [211 kB]                                                       
Get:14 http://security.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [57.5 kB]                                                    
Get:15 http://security.ubuntu.com/ubuntu xenial-security/restricted amd64 Packages [7,352 B]                                                  
Get:16 http://security.ubuntu.com/ubuntu xenial-security/restricted Translation-en [2,432 B]                                                  
Get:17 http://security.ubuntu.com/ubuntu xenial-security/restricted amd64 DEP-11 Metadata [200 B]                                             
Get:18 http://archive.ubuntu.com/ubuntu xenial-updates/restricted amd64 Packages [7,972 B]                                                    
Get:19 http://archive.ubuntu.com/ubuntu xenial-updates/restricted Translation-en [2,692 B]                                                    
Fetched 2,278 kB in 9s (238 kB/s)                                                                                                             

** (appstreamcli:8401): CRITICAL **: Error while moving old database out of the way.
AppStream cache update failed.
Reading package lists... Done
```

I then retried the previous command, with the same result.  So, I tried the Software downloader, this failed to launch (no error message, the icon lit up for a bit then stopped flashing).

So then I tried:
```
ubuntu@ubuntu:~$ gnome-software 
Timeout was reached
```

and:
```
ubuntu@ubuntu:~$ session-installer 
/usr/lib/python3/dist-packages/sessioninstaller/core.py:47: PyGIWarning: Gst was imported without specifying a version first. Use gi.require_version('Gst', '1.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gst
/usr/lib/python3/dist-packages/sessioninstaller/core.py:48: PyGIWarning: Gtk was imported without specifying a version first. Use gi.require_version('Gtk', '3.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gtk
Falling back to package information
INFO:Starting service
DEBUG:Checking for inactivity (30s)
DEBUG:Checking for inactivity (60s)
DEBUG:Checking for inactivity (90s)
^CTraceback (most recent call last):
  File "/usr/bin/session-installer", line 26, in <module>
    main()
  File "/usr/lib/python3/dist-packages/sessioninstaller/core.py", line 1522, in main
    si.run()
  File "/usr/lib/python3/dist-packages/sessioninstaller/core.py", line 452, in run
    self.loop.run()
  File "/usr/lib/python3/dist-packages/gi/overrides/GLib.py", line 576, in run
    raise KeyboardInterrupt
KeyboardInterrupt
```

As you can see, I stopped this process with ctrl+c as it appeared to be going nowhere.

I hope this helps in finding a solution.

---

### Post by deadflowr on 2017-10-03
The python-pip and python-qt4 packages are in universe which is not enabled on live sessions. (or at least in your current live session)
open the live session's Software and Updates and enable universe (community)
or run
```
sudo add-apt-repository universe
sudo apt update
```
then you should be able to install the python packages.

---

### Post by ktat on 2017-10-05
Thanks, deadflowr - that worked a treat.

didn't actually need the add-apt-repository line, but the other part made all the difference.

Is it possible to have all those downloaded files pre downloaded on to a usb to speed up the whole process?

---

### Post by deadflowr on 2017-10-05
> Is it possible to have all those downloaded files pre downloaded on to a usb to speed up the whole process?
Sure, but can be painful.
You need to do a custom livecd setup.
[https://help.ubuntu.com/community/LiveCDCustomization]("https://help.ubuntu.com/community/LiveCDCustomization")

---

