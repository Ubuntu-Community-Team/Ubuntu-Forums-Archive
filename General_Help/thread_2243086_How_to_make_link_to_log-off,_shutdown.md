---
title: "How to make link to log-off, shutdown?"
date: 2014-09-06
forum: General Help
---

### Post by Chanath on 2014-09-06
How to make a link in /usr/share/applications for logoff and shutdown? Where are these stored?

---

### Post by Chanath on 2014-09-06
This shutdown and logoff must be somewhere as an app, so I'd like to have a link on the desktop, other than on the indicator on the panel. Where are they stored in 14.04?

---

### Post by whitesmith on 2014-09-06
This code will cause an immediate reboot```
shutdown -r now
```If you do a```
man shutdown
```you'll find a number of options for shutdown. All you have to do is put the one you want into a  one-line shell script and give it executable privileges. By the way, shutdown is in /sbin.

[edit] The first command above requires sudo to work. Habitual's reference jogged my memory.

---

### Post by Habitual on 2014-09-06
These dbus commands may still work for your version of Ubunutu... 
[http://ubuntuforums.org/showthread.php?t=2164727&p=12742163](http://ubuntuforums.org/showthread.php?t=2164727&p=12742163)

---

### Post by Chanath on 2014-09-07
> **whitesmith said:**
> This code will cause an immediate reboot```
shutdown -r now
```If you do a```
man shutdown
```you'll find a number of options for shutdown. All you have to do is put the one you want into a  one-line shell script and give it executable privileges. 

Thanks, Whitesmith!
Could you please let me know this one-line shell script?

---

### Post by whitesmith on 2014-09-07
Just use gedit (nano, if you're braver) to create several scripts. To get the system to reboot type```
shutdown -r now
```into gedit. Save the file in your home directory as, say, shutdown-r. Then change -r to -P and save the result as shutdown-P, etc. Make sure you give each one the executable permission. Then simply drag them to your desktop to have a choice of shutdown methods. By all means read "man shutdown" because there are many options available for this command. Cheers.

---

### Post by Chanath on 2014-09-07
Got it. Thanks!

---

### Post by CaptainMark on 2014-09-07
These links advise removing the need for a sudo a password from commands usually reserved for root, that's pretty bad advice in my opinion.  I haven't used Ubuntu in some time but I believe (last I checked) that you could still use
```

gnome-session-quit --logout
gnome-session-quit --logout --force
gnome-session-quit --power-off
gnome-session-quit --power-off --force
gnome-session-quit --reboot
gnome-session-quit --reboot --force

```
All without root privileges

---

