---
title: "How do I writer a script for three commands?"
date: 2008-05-25
forum: General Help
---

### Post by Treeh on 2008-05-25
Hey, (sorry for the typo in the title :P)

My WiFi adapter doesn't work unless I type these three commands in terminal:

sudo iwconfig wlan0 txpower on

sudo iwconfig wlan0 essid SMC

sudo dhclient wlan0

How would I make these commands into a script to run at start up?

---

### Post by RATM_Owns on 2008-05-25
Make a file and type this in it:
```
#!/bin/bash
sudo iwconfig wlan0 txpower on
sudo iwconfig wlan0 essid SMC
sudo dhclient wlan0
```

Then save it. Right click, go to Properties, under Permissions allow it to be executed as a program.
Next go to System->Preferences->Sessions, select Add.
For the name, you can put WiFi or something.
For command, choose browse and double click the file you just made.
The comment could be left blank.

---

### Post by Treeh on 2008-05-25
> **RATM_Owns said:**
> Make a file and type this in it:
```
#!/bin/bash
sudo iwconfig wlan0 txpower on
sudo iwconfig wlan0 essid SMC
sudo dhclient wlan0
```

Then save it. Right click, go to Properties, under Permissions allow it to be executed as a program.
Next go to System->Preferences->Sessions, select Add.
For the name, you can put WiFi or something.
For command, choose browse and double click the file you just made.
The comment could be left blank.

Awesome- Thanks!

---

### Post by bingoUV on 2008-05-25
I believe these will ask for password because of the sudo. If you run it in sessions, the request for the password will fail and the commands will not get run.

You should add these commands , without the leading sudo, into the file /etc/rc.local. You will have to edit it as root, so type the following into a terminal
```

sudo gedit /etc/rc.local

```

---

