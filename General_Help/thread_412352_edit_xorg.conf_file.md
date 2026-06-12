---
title: "edit xorg.conf file"
date: 2007-04-18
forum: General Help
---

### Post by gambleton on 2007-04-18
Hi all
This is my first post, I'm a complete newbie to Linux, a refugee from the horrors of Vista.
I've installed a copy of 6.1 a couple of months ago and have been doing pretty well finding my way around it until I tried to upgrade the display driver.
I followed instructions that I found at "http://ubuntuguide.org/wiki/Ubuntu_Edgy".
Specifically item # "1.11.2.1 How to install Graphics Driver (NVIDIA)"
At one point I opened the file "/etc/X11/xorg.conf" and replaced the driver name "nv" with "nvidia".
Now ubuntu will not start because I guess the new driver had not loaded properly and so cannot be found.  I am sure this can be solved by re-editing the file and changing the driver name back to "nv".  However I cannot find a way to open the file.  I have booted up in recovery mode and tried to open the file using "gedit" with no luck.
I can boot up in windows which is on a seperate HD on the same machine or ubuntu on CD.
I suspect that there is a simple answer to this but I'm getting a bit lost and would appreciate any help.
Thanks
Dave

---

### Post by WiseElben on 2007-04-18
Welcome to Ubuntu!

You can't edit using gedit because gedit requires an X environment. You can, however, use nano, a console-based text editor:

```
$ sudo nano /etc/X11/xorg.conf
```

Save the file by pressing Ctrl + O, then Enter.

---

### Post by gambleton on 2007-04-18
Success!
As easy as that.
Many thanks.
Dave.

---

