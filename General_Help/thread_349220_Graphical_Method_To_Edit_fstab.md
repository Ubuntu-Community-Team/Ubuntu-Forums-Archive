---
title: "Graphical Method To Edit fstab?"
date: 2007-01-29
forum: General Help
---

### Post by fejimush on 2007-01-29
Is there a graphical method to edit the fstab file?    I couldn't seem to find anything.  (please resist suggesting gedit, gvim, or some other graphical editor. I beat you to it, lol)

It seems reasonable to expect if you add a new hard drive to your system the OS should automatically recognize that there is a new device attached and prompt the user for action.  

I found gparted, which provides a nice graphical interface partitioning disks.  What is there to set up its mount options in a graphical manner?

thanks,
fej

{EDIT}
I found a package called pysdm mentioned by dcstar below.  This installs a Storage Device Manager into System->Administration.  It works in the sense that it automatically updates your fstab file.  The catch is that Ubuntu uses UUID to identify partitions in the fstab file.   UUID's sound like a good idea if you start moving disks around in your computer.   The Storage Device Manager doesn't seem to have any smarts and got a little confused trying to update the fstab file.  The ordering was wrong and ubuntu refused to boot, so I had boot up into the general (safe) mode and manually change the fstab file.
The bottom line is I couldn't find a smart gui front end to edit the fstab file, ahh well.
{END_EDIT}

---

### Post by taurus on 2007-01-29
Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by aysiu on 2007-01-29
System > Administration > Disks?

---

### Post by fejimush on 2007-01-29
> **taurus said:**
> Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Cute...couldn't resist, eh?  Any keyboard monkey can edit fstab, but it takes a real pro to use a gui to do it.

Anyways, I found the package, pysdm, which seems to give me what I want.  Although I haven't tried it.

Graphical Storage Device Manager
PySDM is a PyGTK Storage Device Manager that allows full customization of hard
disk mountpoints whitout manually access to fstab.
It also allows the creation of udev rules for dynamic configuration of storage
devices

---

### Post by fejimush on 2007-01-29
> **aysiu said:**
> System > Administration > Disks?

That was deprecated in Edgy, no more System > Administration > Disks.  They gave us a fairly useless Disk Usage Monitor in Edgy.

---

### Post by taurus on 2007-01-29
Then why don't you use vim to edit /etc/fstab.  That's all I use as my editor.

---

### Post by fejimush on 2007-01-29
> **taurus said:**
> Then why don't you use vim to edit /etc/fstab.  That's all I use as my editor.

Huh?  Of course I can use any editor, take your pick, nano, emacs, vim, gvim, gedit, heck eclipse...but my question was:

Is there a graphical method to edit the fstab file? I couldn't seem to find anything. (please resist suggesting gedit, gvim, or some other graphical editor. I beat you to it, lol)

thanks,
fej

---

### Post by dcstar on 2007-01-29
> **fejimush said:**
> That was deprecated in Edgy, no more System > Administration > Disks.  They gave us a fairly useless Disk Usage Monitor in Edgy.

The **pysdm** package gives similar functionality.

---

### Post by aysiu on 2007-01-29
If a GUI method is that important to you, Mepis and Knoppix allow you to single-click mount any drive (internal or external).

---

### Post by fejimush on 2007-01-30
> **aysiu said:**
> If a GUI method is that important to you, Mepis and Knoppix allow you to single-click mount any drive (internal or external).

No thanks, I like Ubuntu.  

This strikes me as an odd post from a member of the forum staff.  You should know that you can't always get what you want but sometimes one can get most of what they want and Ubuntu delivers in this regard.  

Suggesting that some switch from Ubuntu for something as trivial as this, sounds irresponsible.

thanks,
fej

---

### Post by PriceChild on 2007-01-30
For now this is the way its done in Ubuntu, maybe a gui will be made eventually.> **fejimush said:**
> No thanks, I like Ubuntu.  

This strikes me as an odd post from a member of the forum staff.  You should know that you can't always get what you want but sometimes one can get most of what they want and Ubuntu delivers in this regard.  

Suggesting that some switch from Ubuntu for something as trivial as this, sounds irresponsible.I don't see anything wrong with aysiu's post.

Linux is about choice... for all you know there may be a distro out there better suited to you even than Ubuntu. We're not going to try and wrap you up and keep you from moving.

---

### Post by Endolith on 2008-05-02
**fejimush:** "Is there a way to change the fstab configuration with a graphical tool instead of editing it by hand?"

**everyone else:** "Here's a way to edit it by hand."


Why are Linux users so ridiculous?  Staff members, no less.

Anyway, here is an Ubuntu Brainstorm about this issue:

[http://brainstorm.ubuntu.com/idea/323/](http://brainstorm.ubuntu.com/idea/323/)

It suggests a tool called Disk Manager that allows for modifying the filesystem configuration.

[http://flomertens.free.fr/disk-manager/](http://flomertens.free.fr/disk-manager/)


Also, Nautilus has some mount options in disk properties.  I've never really figured out what they're for or how they integrate with other things like fstab.  For instance, if you right-click on an unmounted drive it has a "Mount volume" option (which doesn't seem to work) and an "Unmount volume" option (which shouldn't even be there if the drive is already unmounted).

If you right-click a mounted drive and select "Properties", there are "Drive" and "Volume" tabs that give details, and then there's a drop-down thing for both tabs, that lists "Mount Point" "File System" and "Mount Options".  What are these for?  If I change these, what happens?  Why aren't they displayed for unmounted drives?

---

### Post by LaRoza on 2008-05-02
> **Endolith said:**
> **fejimush:** "Is there a way to change the fstab configuration with a graphical tool instead of editing it by hand?"

**everyone else:** "Here's a way to edit it by hand."


Why are Linux users so ridiculous?  Staff members, no less.


Yeah, they are ridiculous. Given a question, they will try their best to help.

---

### Post by LaRoza on 2008-05-02
Making a graphical editor would be rather simple, but the reason why no one has taken the time is that there is probably no demand for it.

---

### Post by uzusan on 2008-05-02
I could have used something like this when i upgraded to hardy. I forgot to copy my fstab file and it was overwritten. It wan't a huge pain to rewrite it, but it would have been useful to have a gui based program. 

(Or even without the gui, if i knew some way to scan what partitions where available).

---

### Post by Endolith on 2008-05-02
> **LaRoza said:**
> Making a graphical editor would be rather simple, but the reason why no one has taken the time is that there is probably no demand for it.

A graphical fstab editor is in the top 30 most-requested features on Ubuntu Brainstorm (out of 8000):

[http://brainstorm.ubuntu.com/idea/323/](http://brainstorm.ubuntu.com/idea/323/)


Disk Manager looks like the best for GNOME:
[http://flomertens.free.fr/disk-manager/](http://flomertens.free.fr/disk-manager/)

There's also PySDM:
[http://pysdm.sourceforge.net/](http://pysdm.sourceforge.net/) 

I found another one for KDE:
[http://kfstab.sourceforge.net/](http://kfstab.sourceforge.net/)

Fedora has one, too:
[http://www.diffingo.com/content/view/32/47/lang,en/](http://www.diffingo.com/content/view/32/47/lang,en/)

and an Ubuntu Blueprint:
[https://blueprints.launchpad.net/ubuntu/+spec/fstab-gui](https://blueprints.launchpad.net/ubuntu/+spec/fstab-gui)

---

### Post by alphamerik on 2008-05-19
> **PriceChild said:**
> For now this is the way its done in Ubuntu, maybe a gui will be made eventually.I don't see anything wrong with aysiu's post.

Linux is about choice... for all you know there may be a distro out there better suited to you even than Ubuntu. We're not going to try and wrap you up and keep you from moving.

fejimush is right, that is a ridiculous response.  He came to an Ubuntu forum to ask for help with Ubuntu and a staff person tells him to use a different distro.  It would be one thing if he said he was thinking about going to another distro because he wants X, Y, and Z, which Ubuntu does not have, but that was not the question.

/end of rant

That being said, I can remember in Edgy when a utility like this was available, and now that I am using Hardy I would like something similar without having to thumb through the fstab man pages.  So yes, there is demand for it.  And strangely enough it is currently the 3rd link under a google search for "ubuntu edit fstab".

---

