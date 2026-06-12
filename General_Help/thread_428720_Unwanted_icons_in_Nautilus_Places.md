---
title: "Unwanted icons in Nautilus Places"
date: 2007-04-30
forum: General Help
---

### Post by plueken on 2007-04-30
When I installed Feisty, it automatically recognized every partition on my system and mounted it by default, including the utility partitions that came with my old Dell's hard drive, that I've just never found a good reason to delete since dropping Windows.  I removed the partitions from /etc/fstab, but Nautilus still has them sitting on the sidebar, and if I right click them I am given only one real option - Mount.  If I double click them, it will automatically mount them.  I don't want to use those drives ever, so I don't want Nautilus showing them to me.

My basic question is, where is Nautilus storing the information about those drives (since they are no longer in fstab), and how can I remove the information so Nautilus stops showing them?

Thanks in advance for any help.  Just a few more tweaks left, and I'll have Feisty up and running perfectly and beautifully!

plueken

---

### Post by vav on 2007-04-30
Run /etc/init.d/dbus restart

---

### Post by zvacet on 2007-04-30
```
gconf-editor

```

**apps>nautilus>desktop**

---

### Post by fragos on 2007-04-30
Configuration Editor-> apps-> nautilus-> Desktop sets which icons to display.  Unfortunately "volumes-visible" lumps all the partitions and USB removeables into a single parameter.

---

### Post by vodalus on 2007-05-04
I posted this in the other thread on this issue: [http://ubuntuforums.org/showthread.php?t=428196](http://ubuntuforums.org/showthread.php?t=428196) (which has some good info but does NOT solve the problem).

I am experiencing the same thing (unwanted partitions that the user cannot mount anyway showing up in the nautilus side bar). This did not used to be the case and nothing I have done makes them go away. I have a number of backup partitions and old systems on my drive and do not want this stuff showing up in nautilus.

Has anyone filed a bug report on this as it is certainly a regression in Feisty?

In addition, data DVDs are no longer show up on the desktop or the nautilus sidebar. Thus I must eject them using the button on the drive. Has anyone else seen this problem?
Edit/Delete Message

---

### Post by fragos on 2007-05-04
You can close the sidebar if it annoys you.  As to DVD's not showing up it is likely that you were hacking in the configuration editor.  This all works perfectly well on my system.

---

### Post by vodalus on 2007-05-09
> **fragos said:**
> You can close the sidebar if it annoys you.

But it is useful for other operations so I don't want to close it.  The link I posted above has a fix for this problem.

> **fragos said:**
> As to DVD's not showing up it is likely that you were hacking in the configuration editor.  This all works perfectly well on my system.

My system is near stock so it is not a gconf setting issue.  I added a new account that is pure stock and I have the problem with it as well.  I really don't know what is going on here.  The DVDs I am having problems with are not "named".  They get mounted in /media/cdrom and I can use them but they are not mounted on the desktop or in Computer.  In Ubuntu 6.06 everything worked fine.  I guess I should start a new thread on this issue.

---

