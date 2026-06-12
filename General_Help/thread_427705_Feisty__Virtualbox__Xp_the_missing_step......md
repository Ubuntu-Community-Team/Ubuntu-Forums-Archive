---
title: "Feisty / Virtualbox / Xp the missing step....."
date: 2007-04-29
forum: General Help
---

### Post by b_chris on 2007-04-29
I had a lot of trouble setting up the shared folder until I found this post on the VBox Forum, This activates the Guest Additions in VBox.

[http://www.virtualbox.org/discussion/1/737](http://www.virtualbox.org/discussion/1/737)

[COLOR="Red"]

vboxmanage sharedfolder add WinXP -name linux -hostpath /MySharedFolder 

Then start virtualbox again, 

click on Details CD/DVD-ROM there on Mount CD/DVD Some fiddling about "ISO Image File" leads to the addition of 

/opt/VirtualBox/additions/VBoxGuestAdditions.iso 

Then click on "ISO Image File" 

Now boot the virtual machine. There you find VBoxGuestAdditions as an additional (CD) drive. 

Click on it to start installing the additional drivers from Virtualbox. 

Restart Windows and then 

execute cmd and there 

### for my example vvvvv 

net use x: \\vboxsvr\linux 

and voila, it seems to work![/COLOR]


Hope this helps someone......

---

### Post by vr6stress on 2007-04-29
Yeah I had trouble with getting a share between fiesty and xp, luckily I have access to one of them linux gurus at work who just set up a shared folded in fiesty and then used smb to share it for windows, I then found it in windows and set it up as a mapped drive. Works pretty well, I can save/share things between the two any time now...

The instructions from Innotek were a little hard for me to understand, and didn't come across as easy as it was to do it the way I did.

---

