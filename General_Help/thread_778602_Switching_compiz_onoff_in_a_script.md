---
title: "Switching compiz on/off in a script"
date: 2008-05-02
forum: General Help
---

### Post by gawron on 2008-05-02
I have an ancient Thinkpad T42 with Radeon 7500. It's blacklisted in Hardy btw, but works mostly OK with SKIP_CHECKS, except suspend/hibernate. When compiz is enabled, the session does not survive suspend cycle - ie. after resume, login screen (GDM) is displayed. Suspend works with metacity, so I would like to switch to metacity on suspend, and switch to compiz back on resume.

Now - the question is - how to do it? I can add something like 
```
metacity --replace & 
``` or even ```
metacity --replace --display=:0 &
```to /usr/lib/pm-utils/ scripts but I get "Unable to open display" error message. I guess it has to do with permissions etc. So, could anyone tell me how to controll metacity/compiz (or - I guess - any other X application) from scripts (or from VT, I guess it would be the same...)

---

### Post by Zorael on 2008-05-02
```
DISPLAY=:0 metacity --replace &
```
I think you want to formulate it that way. I don't see why it shouldn't work.

---

### Post by gawron on 2008-05-02
Right, this works :-) Thanks!

---

### Post by lusisto on 2008-05-15
I am running hardy on an acer aspire 5102 and having the same issue (log in screen after suspend cicle with compiz enabled) so I want to do this scripts things to disable/enable compit, but i don't know how. 
Please, could you post how did you do this?

Thanks

---

### Post by tommyhakinen on 2008-05-16
Install Fusion-Icon. it is the fastest and easiest way without command line.
> sudo apt-get install fusion-icon

Access it from System Tools > Compiz Fusion Icon
On the Notification Area, right click on the Compiz Fusion Icon and switch the Windows Manager to Metacity (No visual effect)

---

### Post by lusisto on 2008-05-16
Thanks tommyhakinen. I installed fusion-icon and, after some research, used the scripts posted in this bug report:

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/197209/comments/44](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/197209/comments/44)

compiz00 must be in /etc/pm/sleep.d and 00-compiz-stop in /etc/pm/config.d

Now compiz is switched off before suspend and restored after resume!

---

### Post by itmanvn on 2008-05-16
> **lusisto said:**
> Thanks tommyhakinen. I installed fusion-icon and, after some research, used the scripts posted in this bug report:

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/197209/comments/44](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/197209/comments/44)

compiz00 must be in /etc/pm/sleep.d and 00-compiz-stop in /etc/pm/config.d

Now compiz is switched off before suspend and restored after resume!

could you share your 00-compiz-stop script:lolflag:

---

### Post by lusisto on 2008-05-16
here they are. I just took them from the link I've posted before.
 actually, 00compiz.sh is called "00compiz" (w/o the extension). I put here the sh because otherwise I get an error uploading.

---

### Post by aroch1 on 2008-05-16
If you'd prefer a graphical alternative, try installing and running fusion-icon.  It's in the respositories and gives a nice easy way to turn compiz on/off from your notificiation area.

---

