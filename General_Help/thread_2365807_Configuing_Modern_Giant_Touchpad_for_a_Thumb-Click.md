---
title: "Configuing Modern Giant Touchpad for a Thumb-Clicker"
date: 2017-07-10
forum: General Help
---

### Post by Ralph L on 2017-07-10
I have opened several threads recently on configuring touchpads, and have received very few responses.  After considerable googling I have come up with a solution that is somewhat usable, although certainly not ideal.  I thought others might be interested.

I recently got a new Acer E5575G-57D4 laptop computer. I am having trouble getting my touchpad working the way I want.  It is an ElanTouch, very large, with a single physical switch at the bottom.  The whole touchpad tilts toward the bottom, when depressed.  I am a thumb-clicker.  I disable all the tap-to-click stuff.  I have tried the synaptics driver, the libinput driver, and the mtrack driver. (More recently I discovered something called the evdev driver, which I haven't tried.)  None of them do exactly what I want.  In general my problem is that I want the touchpad to work the same way that my old small two physical button touchpad worked.  Specifically I want to:
1.  Be able to reach the left-click area of the touchpad with my thumb, while the heel of my thumb rests to the right of the touchpad. This means the left-click area has to extend to within an inch of the right edge of the touchpad.
2.  I want the bottom inch of the touchpad to not move the pointer, when I touch it with my thumb--for clicking or just accidentally touching it with my thumb when not clicking.
3.  I want the right-click button to be in the botton right corner extending about an inch to the left and an inch high.
4.  I want to disable all the tap-to-click, finger scrolling (one or more fingers), mouse wheel emulation, etc.
5.  I want the right edge scroll to work--although this isn't super important.
6.  I want the "ignore palm" or "disable touchpad while typing" feature to work--especially on the left side of the touchpad.  I don't seem to have much problem on the right side.
7.  I would like to be able to rest my thumb on the bottom part of the touchpad, and have it completely ignored except when I click the one physical button.

As I said above I tried three drivers, and none of them really satisfied all my wish list.  However, the old synaptics/synclient driver did the best. Attached below is the commented configuration file that I installed (/etc/X11/xorg.conf.d/70-synaptics.conf).  This file (without my additions) was originally /usr/share/X11/xorg.conf.d/70-synaptics.conf.  I followed the directions in it and copied it to /etc/X11/xorg.conf.d.  Then I added my own configuration options for the synaptics driver. 

The only item on my wish list that the synaptics driver didn't satisfy was #7.  There are a lot complaints about the bug in the synaptics driver that prevents the thumb from being rested on the bottom of the touchpad. There have been some patches, but they don't work in the latest version of synaptics. The IgnorePalm feature didn't work, and synaptics doesn't have a DisableTouchpadWhenTyping feature, but syndeamon can do this. However, I also was able to set the touchpad so that no pointer movement could be initiated on the left third of the touchpad. This didn't affect my use of the touchpad.  It is much too large anyway.

The mtrack driver was next best. I could rest my thumb on the bottom third of the touchpad and simultaneously move the pointer with my index finger.  It also automatically extended the left-click area clear across the bottom of the touchpad so I could easily reach it with my thumb. However, I could not configure it so that the right-click button was in the lower right corner.  In fact the only way I could do a right-click (with tapping disabled) was to have one finger on the touchpad while I clicked with my thumb.  This was very awkward. Also, there was no right edge scrolling, and I could not disable the left third of the touchpad to control erroneous pointer movement from my left palm while typing.  However, the Ignore Palm/DisableTouchpadWhenTyping feature seemed to work fairly well, so disabling the left third of the keyboard was not really a necessity.

The worst of the drivers was libinput. On the plus side I could configure the bottom right corner to do a right-click. However, it had all the same deficiencies as the mtrack driver plus more.  The height of the left, middle, and right-click areas was much to small and could not be adjusted with a BottomEdge option. Since I don't want a middle-click button, I was able to reassign that area to make the left-click area extend further to the right, but it did not extend far enough to the right that I could easily reach it with my thumb.  I gave up on it, before I had a chance to test the Ignore Palm/DisableKeyboardWhenTyping feature.  The worst thing is that, from what I read, libinput is being planned as a replacement for all the other drivers. How could the worst be picked??????

Below are some websites on the various drivers. Documentation on all of them is very poor (that is part of the reason I am writing this), and trial and error seems the only way get a working system.
[https://wiki.archlinux.org/index.php/Touchpad_Synaptics#Using_the_driver.27s_automatic_palm_detection](https://wiki.archlinux.org/index.php/Touchpad_Synaptics#Using_the_driver.27s_automatic_palm_detection)
[https://wiki.archlinux.org/index.php/Libinput](https://wiki.archlinux.org/index.php/Libinput)
[https://wiki.archlinux.org/index.php/Touchpad_Synaptics#Using_the_driver.27s_automatic_palm_detection](https://wiki.archlinux.org/index.php/Touchpad_Synaptics#Using_the_driver.27s_automatic_palm_detection)
[https://github.com/p2rkw/xf86-input-mtrack](https://github.com/p2rkw/xf86-input-mtrack)
[https://howchoo.com/g/mdy0ngziogm/the-perfect-almost-touchpad-settings-on-linux-2](https://howchoo.com/g/mdy0ngziogm/the-perfect-almost-touchpad-settings-on-linux-2)
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/1026046](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/1026046)
[https://www.x.org/wiki/Development/Documentation/PointerAcceleration/](https://www.x.org/wiki/Development/Documentation/PointerAcceleration/)
[https://wiki.archlinux.org/index.php/Mouse_acceleration](https://wiki.archlinux.org/index.php/Mouse_acceleration)
[http://510x.se/notes/posts/Changing_mouse_acceleration_in_Debian_and_Linux_in_general/](http://510x.se/notes/posts/Changing_mouse_acceleration_in_Debian_and_Linux_in_general/)
[https://wiki.archlinux.org/index.php/Touchpad_Synaptics](https://wiki.archlinux.org/index.php/Touchpad_Synaptics) 
[https://www.freebsd.org/cgi/man.cgi?query=synaptics&apropos=0&sektion=4&manpath=FreeBSD+Ports&arch=default&format=html](https://www.freebsd.org/cgi/man.cgi?query=synaptics&apropos=0&sektion=4&manpath=FreeBSD+Ports&arch=default&format=html)

---

