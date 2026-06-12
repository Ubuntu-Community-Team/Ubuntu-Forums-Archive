---
title: "Something horrible has happened with permissions"
date: 2014-07-20
forum: General Help
---

### Post by thewozza on 2014-07-20
I'm not a total idiot, but to be sure I am an idiot.

Nonetheless when I booted up 14.04 this morning after using it mostly happily for the last few weeks I was not presented with a login screen, just a blank screen.  The screen wasn't off, just nothing.

I first flipped over to a terminal with CTRL-ALT-F1 and immediately was presented with a run of errors saying I don't have permissions to access /dev/null.  This seemed weird, and when I checked I did indeed find that /dev/null global permission was set to read only.  I changed permissions, restarted lightdm and I was able to get in.

But it keeps changing back each time I reboot, so this is certainly not fixed.

Also I have *other* permissions errors, for example I can't start a terminal session - it says: "There was an error creating the child process for this terminal" and "getpt failed: Permission denied".

I'm not sure what else is broken, but I can't fathom what managed to mangle the system so horribly.  I recently installed adb tools from the repo, so I could manage my android phone, and I created a rule in /etc/udev/rules.d to allow my computer to see my phone - that's the only thing I did.

What do I do?  This seems like a damn mess and I may just have to abort and go back to 12.04.

Edit: I went in to my apt history and removed the last packages that I installed in the last few days - just android-tools-adb and android-tools-fastboot but it didn't help at all.

Edit2: additional symptom is that I can't log back in after my screen is locked, it just say I've failed my password.  I have to tell it to switch users, then attempt to log back in as myself again.

---

### Post by bapoumba on 2014-07-20
```
mount
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
```
What do you have for /dev/pts ?

(Edit, for ref : [https://bugzilla.redhat.com/show_bug.cgi?id=509632](https://bugzilla.redhat.com/show_bug.cgi?id=509632))

---

### Post by thewozza on 2014-07-20
I have exactly the same /dev/pts as you show here.

But it isn't in fstab, I'm guessing that Ubuntu must mount it using a different mechanism.

---

### Post by bapoumba on 2014-07-21
Hmm OK thanks. Wrong idea then. And yes, it does not show into fstab here either. The bug is old, I do not know if RedHat still does it that way, but the remount command should have worked. Came around getpt from your post. Will look again.

---

### Post by thewozza on 2014-07-21
An additional symptom which is really bad for my workflow is that I can no longer access tty devices.  I'm a network consultant and part of my job means that I have to access devices via serial (these days it is a tty over USB) and this permissions thing has killed it.

It looks like I can still use screen, if I CTRL-ALT-F1 to a shell.  What a mess.

---

### Post by bapoumba on 2014-07-21
Shot in the dark :
[https://bbs.archlinux.org/viewtopic.php?id=125097](https://bbs.archlinux.org/viewtopic.php?id=125097). Reinstall initscripts ?
```
apt-cache policy initscripts
initscripts:
  Installed: 2.88dsf-41ubuntu6
  Candidate: 2.88dsf-41ubuntu6
  Version table:
 *** 2.88dsf-41ubuntu6 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/main i386 Packages
        100 /var/lib/dpkg/status
```

---

### Post by thewozza on 2014-07-21
Update manager crashed, with this error: update-manager crashed with OSError in _open_terminal(): out of pty devices

I'm not entirely clear what a pty device is, but I am not able to open a terminal either.

Edit: /proc/sys/kernel/pty/max reports 4096, and /proc/sys/kernel/pty/nr reports 6.

That should be (IIUC) the max pty and the current pty counts.  So again this is probably a permissions error, and not really running out of pty devices.

---

### Post by thewozza on 2014-07-21
It looks like my version of initscripts is the same as yours.

I am not sure how to re-install them, I tried using apt but it looked like it was going to uninstall the entire system as a dependency, so that's probably not it.

I tried a dpkg-reconfigure but nothing happened - no result at all so I guess it isn't configurable.

---

### Post by bapoumba on 2014-07-21
To your last comment (still looking on that error, but does not look common..)
```
sudo apt-get install --reinstall initscripts
```
From the previous link, I'd do it from recovery mode (not sure about what they call level 3).

---

### Post by thewozza on 2014-07-21
Re-installing initscripts didn't help at all.

It sure is a weird one.

---

### Post by bapoumba on 2014-07-21
The only thing I found approaching your error leads to a dead page. #909066 (long page, take a while to load here) : [http://reqorts.qa.ubuntu.com/reports/launchpad-database/private-apport-crashes.html](http://reqorts.qa.ubuntu.com/reports/launchpad-database/private-apport-crashes.html)
may be because these are private ?

---

### Post by thewozza on 2014-07-23
I've abandoned this, and went back to 12.04.

To the future readers experiencing this bug (maybe even myself) I'm sorry, I wasn't strong enough - there are no answers here.

---

### Post by Hoang_Viet_Dung on 2015-01-13
> 
I recently installed adb tools from the repo, so I could manage my  android phone, and I created a rule in /etc/udev/rules.d to allow my  computer to see my phone


I have same problem with you. 
I spend many days with many times reinstall ubuntu. 
Finally, I remembered that I changed "/etc/udev/rules.d to allow my  computer to see my phone". 
So I delete what you created. Problem resolved.

---

