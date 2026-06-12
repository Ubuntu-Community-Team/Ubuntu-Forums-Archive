---
title: "How to find if libinput is active in xubuntu 17.04"
date: 2017-05-27
forum: General Help
---

### Post by Ralph L on 2017-05-27
I recently bought an Acer Aspire E5-575G-57D4 laptop and am trying Xubuntu 17.04 on it from a thumb drive.  I am really having trouble using the touchpad and am seeking solutions.  Some websites claim that using libinput, rather than synaptic, to control it will help.  But how can I test to see if libinput is being used?  How do I start it (when testing from a thumbdrive) if it is not running.  Also, will synclient still work with libinput, or do I have to set my touchpad configuration some other way?  Any other suggestions on how to control one of these new giant touchpads with integrated left and right click buttons is welcome.

Any help appreciated...

---

### Post by mc4man on 2017-05-27
Don't use 17.04 at all but in lieu of any other answers yet - 
The manifest for 17.04 Xubuntu shows both xserver-xorg-input-libinput & xserver-xorg-input-synaptics installed. Generally then synaptics is what's used. I guess you could find out in various ways, what comes to mind is run this, may be informative,
```
cat /var/log/Xorg.0.log |grep synaptics
```

If it is shown as used then you'd need to remove xserver-xorg-input-synaptics package & reboot. (of no value on a live session..

---

### Post by Ralph L on 2017-05-28
mc4man
Thank you very much for responding.  I really appreciate it.
First, I figured out how to tell if libinput is active.  Under Terminal I ran ```
xinput --list
```This showed that my Elantech touchpad had Id=13.  Then I did ```
xinput list-props 13
```This showed all the libinput features available in xinput, prefixing each one with the word "libinput".  
Second, as for activating libinput, I created the file /usr/share/X11/xorg.conf.d/90-libinput.conf and put in it ```
Section "InputClass"
    Identifier "libinput touchpad catchall"
    MatchIsTouchpad "on"
    MatchDevicePath "/dev/input/event*"
    Driver "libinput"
    Option "Tapping" "True"
    Option "DisableWhileTyping" "True"
EndSection
``` Then I logged out (using the menu, not by using ctl-alt-del) and logged back in again (xubuntu is the user name for the live thumbdrive, with no password).  Then I was running under libinput.  Synclient doesn't work under libinput, so I guess that is another way to tell if one is running under the synaptics driver or the libinput driver.
The good news about libinput is that is it ignores (makes it a dead area) the lower 3/4 inch (or so) of the combined touchpad/left and right click buttons, where you would normally rest your thumb (screwing up the works).  The bad news is that you lose synclient and all the customizing of the touchpad that can be done with it.  Libinput has some adjustments that can be done with xinput, but it cannot adjust the dead area of the touchpad, nor touchpad sensitivity, and at this point I have not been able to even find a way to turn off two finger scroll.  So even with libinput the touchpad is almost worthless.  I think I will try the synaptics driver again.  I saw some websites where people were trying to fix the bug in it that allowed the touchpad to sense a finger in the synclient defined dead area.  Maybe somebody has a patch I can apply.  Also, I borrowed my wife's USB mouse and as long as I am at a desk this works great.  So I guess I will buy one for myself.
As a final rant I must say that laptop manufacturer's have really ruined the concept of a laptop computer.  First, they went to wide screen, making any computer with a decent sized screen too big for an airline seat, and then they went to a giant touchpad with combined touchpad and buttons, which again makes airplane usage (or even armchair usage) almost impossible.  I don't understand why nobody makes the old non-widescreen, small non-integrated touchpad, computer anymore.  I liked those so much.

---

### Post by mc4man on 2017-05-28
Here ever since my laptops starting having these large touchpads with no actual left/right buttons I've gone with external usb mice (mainly wireless) & have disabled the touchpad altogether. The hassle to highlight & r. click was my biggest issue with the 'new' style touchpads.
(- plus with a freewheeling scroll wheel navigating large windows is much easier..

---

