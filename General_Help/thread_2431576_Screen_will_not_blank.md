---
title: "Screen will not blank"
date: 2019-11-18
forum: General Help
---

### Post by cscj01 on 2019-11-18
I have Ubuntu 18.04.3 x64 and am currently on kernel 5.2.3-050203-generic.  I am also running Flashback with Metacity.

Prior to my last update which updated the kernel, I could set my screen to blank to any amount (1, 2,...,10 minutes, etc.) and after that amount of inactivity, the screen would blank.  It would wake up when I moved the mouse or pressed a key on the keyboard.  Since the update, the screen will not blank no matter the time setting.  The only place I know to set this is in Settings>Power>Blank screen.  Now I have to turn off my monitor when I leave the computer for any extended period to avoid using power uselessly and having my monitor subject to failure sooner.  Is there something else I should be checking?

---

### Post by cscj01 on 2019-11-18
I just rebooted with kernel 5.0.0-36-generic (my previous kernel before the last upgrade), and the blank time is now working.  I presume, since no one else has raised this issue, it is unique to my configuration.  If anyone else has this issue after the same two kernels (or an earlier one and 5.2.3-050203-generic), I'll file a bug report.  Let me know.

---

### Post by mörgæs on 2019-11-19
Thanks for considering to file a bug report. If you can reproduce the error using the [daily ISO]("http://cdimage.ubuntu.com/daily-live/") then yes please, a bug report will be appreciated.

---

### Post by beguiled on 2020-02-18
Hello. I found your thread and it appears to match exactly my experiences. I’m new to Ubuntu after having transitioned a desktop away from Windows 10 and I’m having no end of trouble making this work. I just want my screen to turn off after 2 minutes (but keep music playing in the background, for instance) as this is a media PC.

I am using 19.10 and have these settings in place:
Power Saving - Blank Screen - 2 minutes
Screen Lock - Off
Automatic Login - On

Is there anything I can do? I’m not sure how to make your kernel settings effective for me. 

Thanks for any guidance you can provide!

---

### Post by DuckHook on 2020-02-18
Welcome to the forums, beguiled:

Please do not necromance old threads. The OP has likely long since left the building. As a general statement, it is not fair to hijack threads belonging to other people since the OP deserves answers that are exclusive to his/her problem (as do you). I have therefore closed the thread. Please post a new thread with details specific to your circumstances.

---

