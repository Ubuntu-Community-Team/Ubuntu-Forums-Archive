---
title: "Cannot login to ubuntu 14.04"
date: 2016-03-21
forum: General Help
---

### Post by elim-qiu on 2016-03-21
I updated my ubuntu14.04 and cannot login to the system anymore. 

If I put wrong username and/or password, it will show the login error msg, otherwise after the submission, it returns the login window again.

Is there anyway to fix the problem?

---

### Post by TheFu on 2016-03-22
Hard to tell what is really happening underneath.  Also, you aren't clear - is this a text login or a GUI login?

The best answer I have is to boot from a liveCD/Flash drive, mount the location with the last log files that show what happened and use those to figure out would might be causing the issue.

Unrelated, but I'm seeing a similar issue with the alpha 16.04 server - login, login, login, login .. ... ... ... ... ... ... login for hours if I leave it - no time to enter any credentials before the next login prompt is shown.  Installation seemed fine - full-disk, lvm, ssh-server - nothing else.  Haven't looked at the log files myself. Needed a working system after screwing around with 14.04, 15.10 whole drive encryption for 3 days first.  But this thread is about the issue you are seeing, not mine.

---

### Post by elim-qiu on 2016-03-22
It was GUI login not working

---

### Post by Impavidus on 2016-03-22
Hit ctrl+alt+F2 to switch to the text interface and try and log in. When you type your password nothing will show up. Next run```
ls -l .Xauthority .ICEauthority
```This will show the properties of those two hidden files. The output should look like```
-rw------- 1 username username 6680 mrt 22 09:36 .ICEauthority
-rw------- 1 username username   55 mrt 22 09:36 .Xauthority
```If it shows root instead of your user name, run```
rm .Xauthority .ICEauthority
```This will remove the offending files. They will be recreated on the next successful login in the GUI. Changing ownership to yourself also works. You can logout from the console and then switch back to the GUI using ctrl+alt+F7.

In my experience on the forums, this is the most common cause of this type of login failure. The login is actually successful, but the GUI crashes immediately and logs you out again. The root cause is improper usage of sudo, which may change ownership of the mentioned files.

---

