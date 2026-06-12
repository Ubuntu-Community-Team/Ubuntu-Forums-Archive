---
title: "X11VNC startup at boot issues"
date: 2014-12-08
forum: General Help
---

### Post by baseng on 2014-12-08
Greetings to everyone,

I have two active Ubuntu devices, a laptop booted with Win 8.1/Ubuntu 14.04/Kali, and the important one, a standalone Ubuntu 14.04 machine setup for Plex and a virtual WatchGuard Dimension device. I have read countless ways to have x11vnc start on boot. I was unable to get any instance of what I have searched out working. On the laptop, in "Startup Items" I was able to just add:

```
**/usr/bin/x11vnc -xkb -noxrecord -noxfixes -noxdamage -repeat -display :0 -auth /var/run/lightdm/root/:0 -forever -shared -bg -o /var/log/x11vnc.log -passwd "heresmypassword" -rfbport 5900**
```

And with the laptop, reboot, X11VNC is working with that password on 5900. Identical line on the desktop machine does not function. End state goal I'd like to be able to remove the monitor I have on the PC and tuck it behind my entertainment system but I am confused as to why this isn't working. I can take the above line and run it with sudo on either machine, x11vnc starts with the required settings with no errors so I do not believe it is an issue with the line.

I have tried the instructions seen here:
[http://ubuntuforums.org/showthread.php?t=1622843](http://ubuntuforums.org/showthread.php?t=1622843)
[http://www.digitaldrugs.co.uk/wordpress/?p=151](http://www.digitaldrugs.co.uk/wordpress/?p=151)
[http://prismsoul.wordpress.com/2014/06/11/installing-and-configuring-x11vnc-on-ubuntu-14-04/](http://prismsoul.wordpress.com/2014/06/11/installing-and-configuring-x11vnc-on-ubuntu-14-04/)

Perhaps I am missing a minor catch in any of these, or doing a step wrong. My primary concern is I can perform it on one device fine, but not another with identical startup item line. My Linux knowledge is... slightly better than novice at least. Does anyone have any direct experience with this issue or provide any insight as to what I am doing wrong? Thank you for any guidance you guys may have.

---

### Post by baseng on 2014-12-08
Alternatively, if anyone knows a different approach such as a more stable VNC server app (x11vnc is great... but periodically just dumps itself while I am out of the house and trying to manage it forcing a reboot when I get home) I am all ears to recommendations.

While setting up SSH my active VNC session just froze or something, as I am no longer able to move the mouse or do anything, just view. Annoying as this tends to happen daily.

---

### Post by baseng on 2014-12-08
Ok, follow me on this one. I spent my entire day working this out, piecing together bits and pieces from tutorials.

Make a directory for password file and log files:
```
Sudo mkdir ~/.vnc/
```
 
Make a password file:
                ```
x11vnc &#8211;storepasswd ~/.vnc/x11vnc.pass
```
                type password
                confirm password
                hit Y


Next, we make our script:
                ```
Echo &#8220;/usr/bin/x11vnc -xkb -noxrecord -noxfixes -noxdamage -repeat -display :0 -auth /var/run/lightdm/root/:0 -forever -shared -bg -o ~/.vnc/x11vnc.log -rfbauth ~/.vnc/x11vnc.pass -rfbport 5900&#8221; > ~/.config/autostart/x11vnc.sh
```
 
Change permission to executable for all
                ```
chmod +x ~/.config/autostart/x11vnc.sh
```
 
 
Terminate any existing x11vnc. Either go through system, or:
```
ps &#8211;A | grep x11vnc
```
This will give a PID number like 1234
```
Sudo kill 1234
```
 
Test script by:
                ```
Sudo ~/.config/autostart/x11vnc.sh
```
 
Should respond with Port 5900 and bring up another terminal line. Test with VNC client like mRemoteNG or Remmina.
Reboot, test again. This allows access at login screen. Assuming it doesn&#8217;t break on me again.


Now this is working on my laptop, which today decided to break and stop working with my first script in startup programs completely. Going home in a few hours to test on my main platform. But fairly happy with this one.

---

### Post by baseng on 2014-12-09
And again, it does not function on the home machine at startup. Can run the script manually with or without sudo. Likely I messed up permissions at some point while getting Plex to see my fstab mounted logical volume.

Anyone have any ideas whatsoever? Can't add the script to "Startup Manager" and have it work either.

---

### Post by baseng on 2014-12-09
After another long morning of working on it, by opening both machines in SSH terminals and reviewing every file and folder permission and getting them to match, this method continued to fail on the desktop. So. I found and alternative method. This method did not work on my laptop though. I read through boot logs and everything and could not identify why one method worked on one side, and my new method on the other but not vice versa. This entire debacle has drove me to insanity.

So since people are still reading but not responding to this post, Ill fill in what I did to get my desktop running.

Make a script as root
sudo -i

echo "blahblah" > /etc/init/x11vnc.conf

gedit /etc/init/x11vnc.conf

Replace blahblah with:

start on login-session-start

script

/usr/bin/x11vnc -xkb -auth /var/run/lightdm/root/:0 -noxrecord -noxfixes -noxdamage -rfbauth /etc/x11vnc.pass -forever -bg -rfbport 5900 -o /var/log/x11vnc.log

end script

Save and close.

Store a password file at /etc/x11vnc.pass

x11vnc -storepasswd /etc/x11vnc.pass
type once
type twice
Y for yes

Reboot.


And there. Desktop works that way. Laptop works with by other above crazy method of making the startup file at ~/.config/autostart/x11vnc.sh

No idea why. If anyone reads this and has any idea whatsoever of where I went wrong or if it is a hardware difference or what, please let me know. Both machines are now running Ubuntu 14.10.

---

### Post by schneil-2k on 2015-09-06
This method worked for me!
I'm running lubuntu 14.04




> **baseng said:**
> After another long morning of working on it, by opening both machines in SSH terminals and reviewing every file and folder permission and getting them to match, this method continued to fail on the desktop. So. I found and alternative method. This method did not work on my laptop though. I read through boot logs and everything and could not identify why one method worked on one side, and my new method on the other but not vice versa. This entire debacle has drove me to insanity.

So since people are still reading but not responding to this post, Ill fill in what I did to get my desktop running.

Make a script as root
sudo -i

echo "blahblah" > /etc/init/x11vnc.conf

gedit /etc/init/x11vnc.conf

Replace blahblah with:

start on login-session-start

script

/usr/bin/x11vnc -xkb -auth /var/run/lightdm/root/:0 -noxrecord -noxfixes -noxdamage -rfbauth /etc/x11vnc.pass -forever -bg -rfbport 5900 -o /var/log/x11vnc.log

end script

Save and close.

Store a password file at /etc/x11vnc.pass

x11vnc -storepasswd /etc/x11vnc.pass
type once
type twice
Y for yes

Reboot.


And there. Desktop works that way. Laptop works with by other above crazy method of making the startup file at ~/.config/autostart/x11vnc.sh

No idea why. If anyone reads this and has any idea whatsoever of where I went wrong or if it is a hardware difference or what, please let me know. Both machines are now running Ubuntu 14.10.

---

