---
title: "panel icon?"
date: 2016-02-16
forum: General Help
---

### Post by garyed on 2016-02-16
This question is twofold. Running Ubuntu Studio 14.04 on a wired connection desktop & I have an icon on my panel that is two arrows, one facing up & one facing down. The icon controls my ethernet connection & I have to manually click on " Ethernet connection 1" every time I boot up to get connected so I definitely need it. Since I would be unable to connect to the internet without it I was trying to find a way to restore it if it was ever lost. When I look for possible icons to add to my panel it doesn't show up like the other panel icons I have so I'm a little confused how to to it. So I know how to delete it but i don't know how to get it back. Any ideas appreciated. If there is a terminal command that would do the same thing as clicking on the "eterhnet connection 1" that would be nice too. I know I should not have to do any of this & it should connect automatically every boot up but I had a thread in the networking forum a while back that I tried so many things to get the internet working I can't remember all i did & I'm just happy to have that it's working now.

---

### Post by Dennis N on 2016-02-16
In the XFCE desktop environment that I think Ubuntu Studio uses, if you right-click on the network icon (or volume icon) and select remove, you actually remove the **indicator plugin**. So what you look for as a panel item would be "**indicator plugin**". Check and you should see it in the panel items.

---

### Post by ajgreeny on 2016-02-16
To get the ethernet connection to autoconnect have a look at my answer to the post at [http://ubuntuforums.org/showthread.php?t=2313790&p=13440823#post13440823](http://ubuntuforums.org/showthread.php?t=2313790&p=13440823#post13440823)

No reply from that questioner yet to know if it worked, but it should do.

---

### Post by garyed on 2016-02-16
> **Dennis N said:**
> In the XFCE desktop environment that I think Ubuntu Studio uses, if you right-click on the network icon (or volume icon) and select remove, you actually remove the **indicator plugin**. So what you look for as a panel item would be "**indicator plugin**". Check and you should see it in the panel items.

I see the indicator plugin with a circled i as an icon but are you saying if i removed my arrow icon from the panel then it would be gone from the indicator plugin?

---

### Post by Dennis N on 2016-02-16
If you right click on the network icon and select remove, a dialog pops up which says "Are you sure that you want to remove the indicator plugin"? So that is what will be removed, even though you think you are removing the network icon. Your volume icon would go with it since it needs the indicator plugin to appear.
 
If you then restore the indicator plugin to the panel, both of those icons will come back. The plugin is for use by other applications to show an icon. So, if something went wrong with the application that put the icon there, then only that one would disappear.

I have had just the volume control icon disappear several times in Xubuntu installs in the past (not recently). Never found out why, and I never got it back. There is another volume control that can be used, however.

---

### Post by garyed on 2016-02-16
Thanks for the info

---

