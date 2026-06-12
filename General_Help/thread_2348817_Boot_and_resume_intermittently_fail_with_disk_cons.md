---
title: "Boot and resume intermittently fail with disk constantly reading"
date: 2017-01-07
forum: General Help
---

### Post by Ralph L on 2017-01-07
I am running Xubuntu 16.04 on a Dell D610 laptop. About 1 out of 5 "dead start boots" and "resumes from suspend" fail with the disk constantly reading (at least the disk light is on solid).  When boot fails, the screen is blank, is dimly lighted, and just sits there with no change.  When resume fails, the display shows what was on the screen when suspend was performed.  Sometimes, during resume, the cursor will move normally for about 5 seconds and then it (as well as the display) freezes. The system will respond to no input, other than pushing the power off button.  After resume fails and I push power off/on to reboot from scratch, the display for selecting the OS comes up, I select the OS and the blank screen dimly lit (normal) comes up.  However, often after OS select (but not always) the screen freezes and the disk starts reading forever.  Thus, frequently I have to reboot twice after a failed resume.  I have let the system sit for several hours reading the disk during one of these failed boots or resumes, but the disk reading never stops, and the system makes no progress toward completing boot or resume.
I really don't have any insight into what is causing the problem, but I would like to know if anybody else is having the problem. One possibility is that my Firefox, which is always up and has a number of extensions installed is causing the problem.  I have disabled many of the extensions to try to see if I can solve the problem, and I will continue to monitor the system.  Here are the extensions that I normally have installed:
Classic Theme Restorer
h264ify
Mozilla Archive Format
Print Edit
printpdf
Privacy Badger
uBlock Origin
Ubuntu Modifications
Better Privacy
HTTPS Everywhere
Memory Restart
Self-Destructing Cookies
OpenH264 Video Codec
Shockwave Flash
Anybody know if one of these extensions can cause problems??

---

### Post by DuckHook on 2017-01-07
In your case, the potential issues are exacerbated by the fact that your laptop is so old. If I recall, these old dogs still used IDE drives. With such age, the problem could be the HDD. Such drives did not have SMART circuitry, so you would have to test using *fsck*.

Also, take a look through your logs. Especially syslog.

I doubt that the problem is FF, but you never know. Stranger things are known to have happened.

---

### Post by KeepItSimpleStupid on 2017-02-12
I had virtually the same issue in 12.04 LTS.   The real problem was constantly growing logs.There's a hidden file (beginning with a .) that is something like .Xsesssionerrors. It kept on growing. -rw-------  1 ubuntu ubuntu **202738787** Feb 12 04:12 .xsession-errors.  It still does, apparently.  Upgrading Compiz  cut the frequency down.  Use **ls -a -l **and look for large files.
Once, I set up a cron job to delete the file periodically.  I have not investigated reports of growing logs in a  VPN I was using.  In my case, it's the LIVE CD and the CD light keeps blinking just as your HD light keeps blinking.  So check disk space.

---

### Post by Ralph L on 2017-02-13
Thanks for the responses.  I don't think my problem involves the .xsession-errors file.  Mine is only 82 bytes long.  However, you may be correct that there is another very large file being written.  I will keep an eye out for that.

---

### Post by Ralph L on 2017-05-15
I continue to have this problem.  I have had it for several years.  I believe it dates back to when I converted from Ubuntu 12.04 to Xubuntu 14.04.  I am now running Xubuntu 16.04.  The problem (system randomly freezing when resuming from suspend) is very annoying.  I have found new evidence of the failure in the lightdm.log file.  Whenever, I have the failure I seem to get an error message.  Here is a bit of the log showing the error message and some surrounding messages:```
[+1437.20s] DEBUG: Session pid=1025: Terminated with signal 1
[+1437.86s] DEBUG: Seat seat0: Session stopped
[+1437.86s] DEBUG: Seat seat0: Stopping display server, no sessions require it
[+1437.86s] DEBUG: Sending signal 15 to process 928
[+1437.87s] DEBUG: Got signal 15 from process 1
[+1437.87s] DEBUG: Caught Terminated signal, shutting down
[+1437.87s] DEBUG: Stopping display manager
[+1437.87s] DEBUG: Seat seat0: Stopping
[+1439.93s] DEBUG: Seat seat0 changes active session to 
[+1439.93s] CRITICAL: session_get_login1_session_id: assertion 'session != NULL' failed
[+1440.84s] DEBUG: Process 928 exited with return value 0
[+1440.84s] DEBUG: DisplayServer x-0: X server stopped
[+1440.84s] DEBUG: Releasing VT 7
[+1440.84s] DEBUG: DisplayServer x-0: Removing X server authority /var/run/lightdm/root/:0
[+1440.84s] DEBUG: Seat seat0: Display server stopped
[+1440.84s] DEBUG: Seat seat0: Stopped
[+1440.84s] DEBUG: Display manager stopped
[+1440.84s] DEBUG: Stopping daemon
[+1440.84s] DEBUG: Exiting with return value 0
```From what is in the log, it appears that lightdm was shutting down to enter suspend mode, when the error took place.  I tried to find a corresponding error in syslog, but could not, because I can't find a way to match the relative times in lightdm.log with the absolute times in syslog.  I googled the error message ```
CRITICAL: session_get_login1_session_id: assertion 'session != NULL' failed
```and found lots of problems similar to mine--some with claimed workarounds. I installed several of the workarounds, but none of them solved my problem.

Has anybody else seen this error in lightdm.log?? Has anybody seen this problem in other versions of Ubuntu or other versions of Linux in general?  Does anybody understand the lightdm.log file well enough to say what happened in lightdm to cause this error?
Any help is much appreciated!!!!!!

---

