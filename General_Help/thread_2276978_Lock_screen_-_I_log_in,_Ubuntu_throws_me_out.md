---
title: "Lock screen - I log in, Ubuntu throws me out"
date: 2015-05-06
forum: General Help
---

### Post by peter-a on 2015-05-06
Hi all,

I am running 64 bit 14.04 and have installed no new programs in a while, so no changes have preceded this problem, other than the automated Ubuntu updates.

After 10 minutes of inactivity, my PC goes to the lock screen, and all is well as I can hear music still playing.

I then want to log back in, so I wiggle the mouse and get the login screen greeter.

I log back in, the screen flashes, the music stops as all programs are terminated and I'm thrown back to the main login screen as if I had logged out of my session.

I have searched for the problem and can't find anything similar, but that may be because Google is confused by too many other similar lock screen crash issues.

Any ideas? Where would I even begin to look?

I've looked in syslog and dmesg and I can't see anything relevant in there.

For now, I have disabled screen locking so the screen still blanks, it just doesn't lock, which is OK, but not ideal from a security perspective.

---

### Post by dino99 on 2015-05-06
try purging lightdm, then reinstall it; or reconfigure it
then logs might help you to know about the error

---

### Post by etescartz on 2015-05-06
If you are still able to access the system though SSH or through a secondary TTY shell (example: Alt+Shift+F2) check permissions for the files under your /home directory ,or that the username you're trying to login with still owns them.(you might have changed the owner to root, by mistake). 

Also try deleting the  ~/.Xauthority file. If somehow the system shut down abruptly or through a power failure/ forced shutdown, this file could become corrupt and will be unreadable.The system will create a new one in it's place and you'll be able to log back through a graphical interface.

---

### Post by peter-a on 2015-05-06
Thanks both of you, I'll look at these.

FYI, I have no trouble logging back in, I've had no file permissions problems. It's only when I log in from a lock screen that Ubuntu terminates all running programs and throws me back to the greeter.

---

### Post by peter-a on 2015-05-06
p.s. I've also just noticed that if I manually lock my session, I can log back in and all is fine. Weird.

---

### Post by alex375 on 2015-05-06
turn lock screen  off  in screensaver-preferences

---

### Post by ajgreeny on 2015-05-06
If you don't want it, it looks as if you can even uninstall light-locker completely.

I don't know if that means you can not lock the screen manually, but it might be worth trying.

Oor perhaps try removing any home configs for light-locker, purging it and then reinstalling it.

---

### Post by peter-a on 2015-05-06
Hang on.... thanks for all the help, though:

Turn lock screen off? I already did, but that is an insecure, temporary workaround

Can I lock manually? I already said that I can, and it works fine, it's only the lock invoked by the screen timeout that causes the problem

light-locker, will check that thanks

---

### Post by peter-a on 2015-05-11
Well, I upgraded to 15.04 and the problem went away so unfortunately I don't know what fixed it. Thanks for all the help.

---

