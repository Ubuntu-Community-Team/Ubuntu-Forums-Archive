---
title: "Freezing problems!"
date: 2013-06-18
forum: General Help
---

### Post by jll339 on 2013-06-18
Hi all,

Lately I've been having monumental problems with my work laptop!! It keeps freezing up on programs it would normally have absolutely no problem with! I'd like to say that when I first recieved this laptop a few weeks ago it was running perfectly smoothly and multitasking just fine! It was only around the time a few days ago when this aggravation started. 

I can use Firefox just fine, but if I want to add an attachment to an email, or download a file... it will just blackout a bit and freeze up, then _very_ soon after the whole computer freezes.

Same for trying to open LibreOffice files.

I have already looked extensively on how to kill programs when the mouse freezes and how to do a safer restart if necessary (as opposed to force shutdown by power button), that's not what I need help with.

 I can't really do ANYTHING anymore, I need to solve the problem at the **root**.

_Here are the things I've narrowed down as the possible causes_:
1. Installation of avgd antivirus [yes, this was a huge, dumb mistake, but the IT crew at my job made me do it for protocol, so please don't tell me that it's not necessary on Linux and all, I know all that, I just need to know if this is known to be a huge problem, perhaps I should just delete it and not tell them...]

2. Opening an Ubuntu One account [takes up insane %CPU (45% just for starting up!) so I've disconnected it but it still runs at startup and I don't know how to fully get rid of it. Ubuntu One is great, really, but I guess not on this laptop]

------------
Also, I've taken a look at the 'top' terminal command when firefox freezes and it really will freeze up on %CPU of like... 40%. Not even half!

**Stats**
_OS:_
Running 32-bit Ubuntu 13.04

And just in case this might be useful information,
_Laptop type_: Lenovo T60 IBM Think-Pad

Thanks for any advice at all, and please let me know if more information would be useful!
This is beyond frustrating as you can imagine >.<

---

### Post by 2F4U on 2013-06-18
I have a T60 running 12.04 just fine without any issues, basically it runs almost any Linux distribution I wish (I haven't tried 13.04.). Did you look into the system log file, since it may contain hints on why the machine freezes? Did you check temperatures, is it maybe overheating? Did you verify that the RAM is ok?

---

### Post by jll339 on 2013-06-18
Thanks for the advice with the system logs. I will check that out now. I'm not used to sifting through that though so I'm not entirely sure what to keep an eye out for. Will still try though and keep you posted.

I may also check out the RAM but my machine was processing high data throughput before so I am not too inclined to think that may be the case.

Lastly, the machine actually never overheats. One good thing about this laptop is that I'm really never hearing the fan or feeling any heat. Very nice on that end!

---

### Post by HermanAB on 2013-06-18
Man, I wish I had a freezing problem - it was 44 degrees Celsius again today...

Anyhoo, are you using Wifi or wired ethernet?  If the one, switch to the other.

If you trawl through the logs, you will eventually notice what it looks like when the machine starts up.  Any problem reports would be immediately before that.

---

### Post by jll339 on 2013-06-19
Gahh, unfortunately that didn't work either! It was really good advice, though, it almost looked like it would! And these issues started happening around the time I switched over to Ethernet with an IP address (when before I was just on Wi-Fi).

There are so many logs, should I be looking at the start-up one?

I would like to be able to fix this without having to resort to wiping out the computer and/or getting a new one. I've got all my stuff on here. :(

---

### Post by matt_symes on 2013-06-19
Hi
> 
I can use Firefox just fine, but if I want to add an attachment to an  email, or download a file... it will just blackout a bit and freeze up,  then _very_ soon after the whole computer freezes.

Same for trying to open LibreOffice files.

So do you only see this issue when opening, closing or saving files on the local hard drive ? 

Does it happen in Nautilus file browser ?

Can you identify this as a trigger for the freezing ?

Can you get to a console and restart the session by pressing these keys at the same time..

```
ctrl + alt + f1
```

..loging into the console and typing

```
sudo service lightdm restart
```

Have you verified the filing system using a LiveCD/USB ?

Have you run a SMART on the hard drive ?

Is there anything in the log files ?

```
~/.xsession-errors
```
```
/var/log/syslog
```
```
/var/log/xorg.0.log
``` 

If you disable the anti virus daemon for a while, does it still freeze ?

It could be a whole number of things causing this and at the moment, it's kind of stabbing in the dark without further clues.

Kind regards

---

### Post by jll339 on 2013-06-19
This issue only seems to happen when I try to download anything from FireFox (not from the terminal though), and when trying to open pictures and documents on the pre-set applications LibreOffice and the Ubuntu photo viewer application. This is whether I open them in the file browser or from the applications.

I've tried all of those keys and even more, but even though the mouse is visibly moving, absolutely no programs or anything will respond, even when I use: ```
alt+ctrl+F1
``` I try to log in and it just stalls endlessly. So I can't do any functions to kill a frozen program.

After looking it up, I'm not fully sure what a LiveCD/USB and its use in this case. I have not run SMART, I'm not sure how to. I tried the memory test as suggested earlier.

As for disabling the anti-virus, yes we tried that and it seemed to have worked. Now I think it just freezes less often than before, but still does. I should probably delete it... I only know how to use the ```
rm -r
``` function, is there a cleaner way to fully un-install a package? I have a feeling there may be a more proper way.

---------------------------------
As for looking through the log, I'm still a little lost but these are the kinds of reoccurring messages that appear that look a little sketchy:

**from syslog**
Jun 19 09:52:35 jeremy-ThinkPad-T60 wpa_supplicant[1046]: dbus: wpa_dbus_get_obj
ect_properties: failed to get object properties: (org.freedesktop.DBus.Error.Fai
led) failed to parse RSN IE
Jun 19 09:52:35 jeremy-ThinkPad-T60 wpa_supplicant[1046]: dbus: Failed to constr
uct signal
Jun 19 09:52:35 jeremy-ThinkPad-T60 NetworkManager[896]: <warn> Couldn't retriev
e BSSID properties: failed to parse RSN IE.

**from Xorg.0.log**

[    19.974] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.21.6-0ubuntu4 (Bryce Harrington <bryce@ubuntu.com>)
[    19.974] (WW) Falling back to old probe method for vesa
[    19.974] (WW) Falling back to old probe method for modesetting
[    19.974] (WW) Falling back to old probe method for fbdev
[    19.974] (II) Loading sub module "fbdevhw"

^although I think the above may be fine, not sure. This message only appeared once in this log, unlike the **syslog **error messages and their re-occurrence many times over.

Thanks for the suggestions! Any of these messages look like something?

---

### Post by jll339 on 2013-06-19
I also noticed this kind of error when looking through  **/var/log/apport.log**

ERROR: apport (pid 2544) Tue Jun  4 11:17:40 2013: called for pid 2313, signal 1
1, core limit 0
ERROR: apport (pid 2544) Tue Jun  4 11:17:40 2013: script: /usr/lib/ubuntu-sso-c
lient/ubuntu-sso-login, interpreted by /usr/bin/python2.7 (command line "/usr/bi
n/python /usr/lib/ubuntu-sso-client/ubuntu-sso-login")
ERROR: apport (pid 2544) Tue Jun  4 11:17:40 2013: gdbus call error: Error conne
cting: Could not connect: Connection refused

ERROR: apport (pid 2544) Tue Jun  4 11:17:40 2013: debug: session gdbus call: 
ERROR: apport (pid 2544) Tue Jun  4 11:17:46 2013: wrote report /var/crash/_usr_lib_ubuntu-sso-client_ubuntu-sso-login.1000.crash

----------------------------------

Oddly enough, the last submission in this log was Jun 5th... is that normal? Or is that really bad?

---

### Post by matt_symes on 2013-06-19
Hi

> **jll339 said:**
> I also noticed this kind of error when looking through  **/var/log/apport.log**

ERROR: apport (pid 2544) Tue Jun  4 11:17:40 2013: called for pid 2313, signal 1
1, core limit 0
ERROR: apport (pid 2544) Tue Jun  4 11:17:40 2013: script: /usr/lib/ubuntu-sso-c
lient/ubuntu-sso-login, interpreted by /usr/bin/python2.7 (command line "/usr/bi
n/python /usr/lib/ubuntu-sso-client/ubuntu-sso-login")
ERROR: apport (pid 2544) Tue Jun  4 11:17:40 2013: gdbus call error: Error conne
cting: Could not connect: Connection refused

ERROR: apport (pid 2544) Tue Jun  4 11:17:40 2013: debug: session gdbus call: 
ERROR: apport (pid 2544) Tue Jun  4 11:17:46 2013: wrote report /var/crash/_usr_lib_ubuntu-sso-client_ubuntu-sso-login.1000.crash

----------------------------------

Oddly enough, the last submission in this log was Jun 5th... is that normal? Or is that really bad?

If that was the last crash you had then that would make sense if the freezing is not creating a crash dump.

Kind regards

---

### Post by jll339 on 2013-06-19
> **matt_symes said:**
> Hi



If that was the last crash you had then that would make sense if the freezing is not creating a crash dump.

Kind regards

Well my computer crashes multiple times a day, for over a week or two now. That includes today and yesterday, so it wasn't the last crash (and I can't fully remember when it started happening but I don't feel it was that early in the month. Could be wrong). That's why I'm worried about that log. If it hasn't been logging any information for that long, is there something really wrong?

---

### Post by matt_symes on 2013-06-19
Hi

> **jll339 said:**
> This issue only seems to happen when I try to download anything from FireFox (not from the terminal though), and when trying to open pictures and documents on the pre-set applications LibreOffice and the Ubuntu photo viewer application. This is whether I open them in the file browser or from the applications.

I've tried all of those keys and even more, but even though the mouse is visibly moving, absolutely no programs or anything will respond, even when I use: ```
alt+ctrl+F1
``` I try to log in and it just stalls endlessly. So I can't do any functions to kill a frozen program.

Open a terminal and type

```
firefox
```

Browse to a site and download something. Do you get any diagnostic information in the terminal before it freezes ?

I find it odd that it's still freezing here as this is where you would expect the virus scanner to do its job but you said you disabled it.

> After looking it up, I'm not fully sure what a LiveCD/USB and its use in this case. I have not run SMART, I'm not sure how to. I tried the memory test as suggested earlier.

A LiveCD/USB is the Ubuntu install CD where you select the "try Ubuntu" option as opposed to installing straight away.

From here you can run various diagnostic routines such as a fsck on the root filing system and SMART test on the drive itself - if the drive supports SMART.

> As for disabling the anti-virus, yes we tried that and it seemed to have worked. Now I think it just freezes less often than before, but still does. I should probably delete it... I only know how to use the ```
rm -r
``` function, is there a cleaner way to fully un-install a package? I have a feeling there may be a more proper way.

That depends on how the software was installed. You can ...

```
sudo apt-get remove <package_name>
```

if you installed using a package manager. If installing from source, you maybe able to 

```
sudo make uninstall
```

or delete the files.

How did you install the anti virus software and how did you disable the anti-virus software ? 

> 
---------------------------------
As for looking through the log, I'm still a little lost but these are the kinds of reoccurring messages that appear that look a little sketchy:

**from syslog**
Jun 19 09:52:35 jeremy-ThinkPad-T60 wpa_supplicant[1046]: dbus: wpa_dbus_get_obj
ect_properties: failed to get object properties: (org.freedesktop.DBus.Error.Fai
led) failed to parse RSN IE
Jun 19 09:52:35 jeremy-ThinkPad-T60 wpa_supplicant[1046]: dbus: Failed to constr
uct signal
Jun 19 09:52:35 jeremy-ThinkPad-T60 NetworkManager[896]: <warn> Couldn't retriev
e BSSID properties: failed to parse RSN IE.

**from Xorg.0.log**

[    19.974] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.21.6-0ubuntu4 (Bryce Harrington <bryce@ubuntu.com>)
[    19.974] (WW) Falling back to old probe method for vesa
[    19.974] (WW) Falling back to old probe method for modesetting
[    19.974] (WW) Falling back to old probe method for fbdev
[    19.974] (II) Loading sub module "fbdevhw"

^although I think the above may be fine, not sure. This message only appeared once in this log, unlike the **syslog **error messages and their re-occurrence many times over.

Thanks for the suggestions! Any of these messages look like something?

I can see nothing in the logs that suggest the problem.

Kind regards

---

### Post by jll339 on 2013-06-19
Ok, thanks all for your help!
Just one last thing then, to try to solve the freezing issues I'd like to try removing avgd from the system. Is rm -r the best way to go or is there a better way for un-installing packages?

---

### Post by jll339 on 2013-06-21
I executed the uninstall function for avg, now my computer works much better! There is still moments where a program will freeze, but it's not something that requires a shut-down, it can be handled. This is very good news to me!

---

