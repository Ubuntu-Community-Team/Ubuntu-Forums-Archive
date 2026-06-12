---
title: "Saving touchpad settings in Lubuntu"
date: 2016-11-02
forum: General Help
---

### Post by steven66 on 2016-11-02
I have used all flavours on Ubuntu for at least 5 years, and one thing that shows up again and again are missing touchpad settings. I believe at one time a GUI utility like Synaptics or G-something were available to do this job, but was left behind in the ever changing updates of Linux.

I'm wondering why someone can't make a GUI for mouse and touchpad settings that will work for all flavours of Ubuntu? This is a technical impossibility? I would think this would be a very simple program and GUI interface? If anyone is up to the challenge, I'm sure that thousands of thousands of Ubuntu users would be very happy :)

Anyway, I want to make these changes to the touchpad and save them so the system remembers them after a reboot. I have found many posts about this, but it all depends on what flavour of Ubuntu you have and what version! There seems to be little consistency on where this information is saved. That is perhaps why it's impossible to make a mouse and touchpad GUI for Ubuntu?

So, where do I need to save this information for a system wide effect? Oh, btw I use Lubuntu 16.04.

Synclient
MaxTapTime=0
VertEdgeScroll=0
VertTwoFingerScroll=0

Thanks.

---

### Post by kalehrl on 2016-11-02
Try this:
```
nano /etc/X11/xorg.conf.d/synaptics.conf
```
paste this:
```
Section "InputClass"
    Identifier    "Touchpad"
    MatchIsTouchpad    "yes"
    Driver "synaptics"
    Option "MaxTapTime" "0"
    Option "VertEdgeScroll" "0"
    Option "VertTwoFingerScroll" "0"
EndSection
```
log out and see if it works.

---

### Post by steven66 on 2016-11-02
When I try to save the file, I get an error message saying the file or folder does not exist...

---

### Post by vasa1 on 2016-11-02
Have you tried to edit *~/.config/lxsession/Lubuntu/autostart*?
Add the following lines to the file.
```
synclient VertEdgeScroll=0
VertTwoFingerScroll=0
MaxTapTime=0
```Log out. Log back in.

Note that is user-specific and not system-wide.

I haven't tried editing */etc/xdg/lxsession/Lubuntu/autostart* the same way.

---

### Post by kalehrl on 2016-11-02
> **steven66 said:**
> When I try to save the file, I get an error message saying the file or folder does not exist...
Then first try:
```
mkdir /etc/X11/xorg.conf.d 
```
followed by the rest of the commands.

---

### Post by steven66 on 2016-11-02
Thanks, 
it worked by adding one line of code to *~/.config/lxsession/Lubuntu/autostart*: synclient VertEdgeScroll=0 VertTwoFingerScroll=0 MaxTapTime=0

It didn't work by editing the system wide file, only the user file.

---

### Post by steven66 on 2016-11-02
> **kalehrl said:**
> Then first try:
```
mkdir /etc/X11/xorg.conf.d 
```
followed by the rest of the commands.

Would the system go and look for this new file by itself if I create it?

---

### Post by steven66 on 2016-11-02
Does anybody know if there is a synclient setting for two finger vertical reverse scroll (Australian scroll)?

---

### Post by kalehrl on 2016-11-02
> Would the system go and look for this new file by itself if I create it?
It should.
It works this way in Debian 8 so it should work in Ubuntu.

---

