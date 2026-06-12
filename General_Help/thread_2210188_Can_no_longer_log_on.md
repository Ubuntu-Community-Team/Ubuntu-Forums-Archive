---
title: "Can no longer log on"
date: 2014-03-09
forum: General Help
---

### Post by David_OConnor on 2014-03-09
Things were working just fine up until yesterday. I made no changes to my system since.

I can no longer log onto Ubuntu. It appears to have auto-upgraded to 14.04, which IIRC isn't even out yet, and now I can't log in. I'm presented with a login prompt at the left side of a minimally-filled desktop environment. It has three options: My account name, 'guest', and 'remote login'. Entering my password for my login, or using guest does not work. I don't have a remote login.

If I type a bad password, it correctly tells me it's wrong, but a correct password leaves it doing nothing, until I press esc, at which point I can try again.

---

### Post by sffvba[e0rt on 2014-03-09
What leads you to believe your system has "auto-upgraded" to 14.04?

---

### Post by David_OConnor on 2014-03-09
I was running 13.10. It now says 14.04 LTS in the bottom-left corner on the login screen.

---

### Post by David_OConnor on 2014-03-13
Any ideas? Someone else has to have had this.

---

### Post by steeldriver on 2014-03-13
Can you log in at one of the CLI virtual terminals (e.g. Ctrl-Alt-F2 ... hit Ctrl-Alt-F7 to get backto the GUI)?

---

### Post by David_OConnor on 2014-03-13
I'm able to log on successfully using ctrl-alt-f2, to a command line interface. When I go back to the GUI with ctrl-alt-f7, I'm presented with the same unpassable login screen I had before.

---

### Post by deadflowr on 2014-03-13
When you try logging in normal does the password accept but the screen just hangs?

Added: By hanging I mean does the password field go blank, like it stops showing?

---

### Post by David_OConnor on 2014-03-13
Yes, the password field goes blank after entering the correct password. The esc key brings it back.

---

### Post by deadflowr on 2014-03-13
I think I might know the problem, but first let's make sure.

Do the ctrl+alt+F1 thing and login.

Then enter this
```
ls /usr/share/xsessions
```
is there an entry for Ubuntu in there?
(ubuntu.desktop)

---

### Post by David_OConnor on 2014-03-13
No, only gnome.desktop (I'm p sure I'm on Unity, although now that I think about it, the new login screen has a top menu...)

---

### Post by deadflowr on 2014-03-13
Okay, first is there an icon in the password, username box that looks like the ubuntu logo?

If you click on this is there an entry for gnome?

If you select gnome and try to log in does it work?

---

### Post by David_OConnor on 2014-03-13
No icon; just my user name, and the password field.

---

### Post by deadflowr on 2014-03-13
Okay, weird.
Then try this
reopen the F1 session and open the nano text editor
sudo nano

Then enter this
```
[Desktop Entry]
Name=Ubuntu
Comment=This session logs you into Ubuntu
Exec=gnome-session --session=ubuntu
TryExec=unity
Icon=
Type=Application
X-LightDM-DesktopName=Unity
X-Ubuntu-Gettext-Domain=gnome-session-3.0
```

then press ctrl+x 
save it as /usr/share/xsessions/ubuntu.desktop

then try to restart lightdm
```
sudo restart lightdm
```
now see if you can log in.

---

### Post by David_OConnor on 2014-03-13
I guess there's a blue moon tonight. Thank you very much - That put me right to my normal Desktop!

---

### Post by deadflowr on 2014-03-13
Cool. Good to see.
You can mark this as solved if it is.

Go to the part above the first post where it says Thread Tools.
mark as solved should be in there.

Still, the issue of why/how you upgraded to 14.04 remains a mystery...
But that seems to be another matter.

Edit:

Oh yeah, you can re-enter the F1 session and type exit, to close that one and then ctrl+alt+F7 to go back to the normal desktop, if you want.

---

### Post by David_OConnor on 2014-03-13
Cool! It does indeed show I'm in 14.04 LTS under Unity's details.

The only thing I can think of, is that I was on a crappy internet connection for the past few weeks, to the point where all the updates failed. When I got back to a good connection, I clicked through the updates popup, so one of the updates might have done it. I didn't do anything deliberate, just clicked OK to make the update notifications go away.

---

### Post by steeldriver on 2014-03-13
Nicely played deadflowr, impressive diagnosis + fix!

---

### Post by deadflowr on 2014-03-15
So it seems this is a bug.
This thread [here]("http://ubuntuforums.org/showthread.php?t=2209080&page=5&p=12957487#post12957487") discusses(off topic) this problem with the package ubuntu-session not being installed.
If you would you could mark the bug Doug S references in post 53
[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1283826](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1283826)

as affecting you.


Interesting development in that regard.

My own experience is less a packaging problem and more of having too many window managers and desktop envoronments for the greeter to list and as such deleting/moving a few entries in xsessions for easier viewing.
But as I learned removing the session you or on when rebooting brings you to that session as the default option when logging in.
Since no file can be run the login hangs.

---

### Post by David_OConnor on 2014-03-16
Marked; good work.

---

