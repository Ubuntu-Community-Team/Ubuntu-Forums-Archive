---
title: "How to manually customize keyboard layout switcher in Ubuntu 13.10?"
date: 2013-10-06
forum: General Help
---

### Post by iambodin on 2013-10-06
I'd noticed,in every 3.10-or-newer kernel based linux distro (including Ubuntu 13.10), keyboard layout setting used "Switch to next/previous source using..." (just as in attached pic)

[IMG]https://lh4.googleusercontent.com/-rmdSREFKqUk/UlF-FIDELhI/AAAAAAAAFJs/S8cj7svxZRQ/w844-h481-no/Selection_002.png[/IMG]

I had used to manually edit files in /usr/share/X11/Xkb directory (add Next/Previous source in symbol/group and add option in rule/*) and added "grave accent" option.

[IMG]https://lh3.googleusercontent.com/H-b5b44xITEOsbV4ZYrs3GhKloR9KWy5_ayRw6wZolE=w447-h407-no[/IMG]

How can I manually editted option of keyboard layout switcher in New age distro ? Is it still possible?

---

### Post by xc3RnbFO8P on 2013-10-06
System Settings> Region & Language  (your look different )

---

### Post by iambodin on 2013-10-06
Yeah but I can't edit the source file directly like I did in those days with stuff in /usr/share/xkb/* and so I can't use Grave accent to change the layout or even Alt+Shift.
Gnome-tweak-tool can't help too.:(

---

### Post by grahammechanical on 2013-10-06
That text entry dialog should have the default key combinations in those two panels. They are:

Switch to next source using: Super+Space
Switch to previous source using: Shift+Super+Space

If we click on either of the panels the default key combination changes to "New Accelerator." Click again and the default setting reverts back. If we press a key combination whilst the words "New Accelerator" are showing then the accelerator or switch will change to the new key combination. There should be no need to edit a configuration file but that file is still there in /usr/share/X11/Xkb/group. How useful it is I cannot tell you.

When we install 13.10 we are told that Super+Space is now the default hotkey for Dbus.

I find that it is sensible before upgrading to a new version of Ubuntu to install the new version in another partition of about 10 - 20 GB and test it out and see if I can set it up to how I like it to be. 

Regards.

---

### Post by NikTh on 2013-10-06
There is an open bug that I think is related to the problem of yours. 
[https://bugs.launchpad.net/ubuntu/+source/indicator-keyboard/+bug/1218322](https://bugs.launchpad.net/ubuntu/+source/indicator-keyboard/+bug/1218322)

---

### Post by iambodin on 2013-10-06
> **grahammechanical said:**
> That text entry dialog should have the default key combinations in those two panels. They are:

Switch to next source using: Super+Space
Switch to previous source using: Shift+Super+Space

If we click on either of the panels the default key combination changes to "New Accelerator." Click again and the default setting reverts back. If we press a key combination whilst the words "New Accelerator" are showing then the accelerator or switch will change to the new key combination. There should be no need to edit a configuration file but that file is still there in /usr/share/X11/Xkb/group. How useful it is I cannot tell you.

When we install 13.10 we are told that Super+Space is now the default hotkey for Dbus.

I find that it is sensible before upgrading to a new version of Ubuntu to install the new version in another partition of about 10 - 20 GB and test it out and see if I can set it up to how I like it to be. 

Regards.

I knew that but ,with different combination keys, changing layout for every 3-4 word while typing long document would be royal pain in the ass. I can tell.
Bottom line - I need single key and I think the strength of FOSS is freedom & customizable.

> **NikTh said:**
> There is an open bug that I think is related to the problem of yours. 
[https://bugs.launchpad.net/ubuntu/+source/indicator-keyboard/+bug/1218322](https://bugs.launchpad.net/ubuntu/+source/indicator-keyboard/+bug/1218322)

About that bug, I think so too. (My problem ,grave accent thing, was nearly hopeless)

Just wonder about new xkb system configuration and its new structure. Which file/config do response for it?

---

### Post by slepichev on 2013-10-18
[**[COLOR=#000000]iambodin[/COLOR]**]("http://ubuntuforums.org/member.php?u=628273") the files you are looking for is in */usr/share/X11/xkb/symbols*

---

### Post by cariboo on 2013-10-18
Moved to General Help, seeing as Saucy has been released.

---

### Post by iambodin on 2013-11-08
> **slepichev said:**
> [**[COLOR=#000000]iambodin[/COLOR]**]("http://ubuntuforums.org/member.php?u=628273") the files you are looking for is in */usr/share/X11/xkb/symbols*

That's not work anymore in Ubuntu 13.10. That's why I raised this topic.

---

