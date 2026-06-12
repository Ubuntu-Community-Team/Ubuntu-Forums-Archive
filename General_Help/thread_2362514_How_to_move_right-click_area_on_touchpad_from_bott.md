---
title: "How to move right-click area on touchpad from bottom-right to right side"
date: 2017-05-29
forum: General Help
---

### Post by Ralph L on 2017-05-29
I recently bought an Acer Aspire E5-575G-57D4 laptop and am trying Xubuntu 17.04 on it from a thumb drive. I am really having trouble using the ElanTech touchpad and am seeking solutions.  The ElanTech touchpad (my opinion) may be the worst touchpad ever made. The touchpad is gigantic.  It has no discrete buttons; the left click is done by pressing on the bottom of the touchpad thus tilting the touchpad toward the bottom where it is sensed with a physical switch. There is no physical switch for the right-click button.  If a touch is sensed on the bottom-right, when the touchpad is tilted, then it is assumed to be a right-click. Needless to say any unintentional brushing of the touchpad causes all sorts of strange things to happen.

I have switched from the Synaptics driver to the libinput driver so that the bottom-left of the touchpad (left-click button area) is not touch sensitive.  The Synaptics driver has a bug which prevents making an area (like bottom left) completely dead.  Since Synclient doesn't work with libinput, I used xinput to configure the touchpad as best I could.  All the options in Synclient are not available with xinput.  I disabled tap-to-click (both one finger and two finger disabled), all scroll methods, and set button mapping to map the middle bottom of the touchpad to left-click.  This confines right-click to the bottom right.  Doing this really helps, but I still occasionally accidentally brush the bottom right right-click area and set off strange happenings.

I would like to remap the bottom right area to be left-click (so the entire bottom of the touchpad is non sensitive) and enable the right edge to be the right-click area.  I used "xinput set-button-map 14 1 1 3 4 5 6 7" (14 is my ElanTech device id) to map the middle bottom to the left-click.  By changing the button mapping to "1 1 1 4 5 6 7" I can also map the bottom right to left-click.  However, then I don't have any right-click button area at all, and no way to do a right click.

My question is "Does anybody know how I can map right-click to the right edge of the touchpad"? Or maybe shrink the bottom right area to be only a 1/2 inch long?  I think I have in the past seen ways of setting button size, but I sure can't find them now.

Note:  To make any of these settings permanent they must be put in /usr/share/X11/xorg.conf.d/90-libinput.conf or (I think) in /etc/X11/xorg.conf.d/90-libinput.conf.  The format of these files can be googled.

Any other suggestions on how to control one of these new giant touchpads with integrated left and right click buttons is welcome.

Any help appreciated...

---

### Post by Ralph L on 2017-06-06
There have been a number of bugs filed concerning the Synaptics driver's inability to completely deaden the "dead zone" created by synclient with the option "AreaBottomEdge". While synclient partially deadens the area, it is still sensed, when doing a "finger count" for 1, 2, and 3 finger actions. Several people have tried to patch synclient to fix the problem, but all the fixes have had problems (like disabling some other function).  Moreover, the fixes have usually worked in just one version of synaptics/synclient, and when the next version came along, they ceased working.  I am running the latest version of xubuntu (17.05, Zesty) and so far I haven't seen a patch for synaptics 1.9.0-1--the version that is in Zesty.  Other people must have struggled with this problem considering that all the new laptops seem to have touchpads that are too big for us thumb-clickers to extend our thumbs over and hit the left-click area.  I guess the finger-clickers don't have a problem, but my "clubby" fingers just don't seem to have the velvet touch needed to be a finger-clicker. I end up doing a 2 finger right-click, when I intended to do a two finger scroll, and vice versa.  I find very strange results happening--like pasting some garbage into an unknown location in a document that I was trying to edit. Often I don't even know that the paste has taken place until days afterward.  Very annoying.
Here are some of the web sites discussing synaptics/synclient patches to fix the problem. If anybody know of one the works in synaptics 1.9.0-1, I would really appreciate a reply.```
https://bugs.freedesktop.org/show_bug.cgi?id=66532
https://askubuntu.com/questions/221664/how-to-tune-touchpad-for-smaller-area
http://pastebin.com/raw/4v9JP2pe
https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/1026046
https://bugs.freedesktop.org/attachment.cgi?id=100632&action=edit
https://bugs.freedesktop.org/attachment.cgi?id=100632
```

---

