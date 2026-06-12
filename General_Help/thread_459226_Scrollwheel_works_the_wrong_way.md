---
title: "Scrollwheel works the wrong way"
date: 2007-05-30
forum: General Help
---

### Post by mikemcfarlane on 2007-05-30
Hi
I have just installed the latest version of Ubuntu for the first time :) and am well impressed. However, my Wacom tablet mouse scroll wheel works the wrong way ie scrolling down goes up.

I've had a look at a few posts and generally most people recommended changing /etc/X11/xorg.conf in the ZAxisMapping parameter. Currently this is set to "4 5", I tried "5 4" and also "6 7" which seemed to be common settings/advice, but my wheel still works the wrong way.

Any advice would be great.

Thanks in advance.

Mike

---

### Post by strabes on 2007-05-30
Did you restart your x server after making the changes to xorg.conf? You have to restart it for your settings to be applied. You can use ctrl+alt+backspace

---

### Post by mikemcfarlane on 2007-05-30
Hi Strabes

Thanks for the reply. Yes, I logged out and restarted the X server as you described. I also tried the usual Windows trick! of rebooting. Neither worked. Would you have expected swapping the 4 and the 5 in the ZAxisMapping to have worked?

Perhaps it is a peculiararity of Wacom tablets? I'm going to have a look at some of the dedicated drivers for Wacom tomorrow:
linuxwacom.sourceforge.net/
And also a quick Google search revealed Linux drivers on the Wacom site, so maybe some inspiration there:
[www.wacom.com/productsupport/linux.cfm](www.wacom.com/productsupport/linux.cfm) 

If there are any other suggestions, that would be great.

Mike

---

### Post by mikemcfarlane on 2007-05-30
Quick update:
I swapped the Wacom mouse/tablet for an MS Optical mouse and the wheel works the right way. I guess that it is something to do with the way the Wacom mouse works.

---

### Post by mikemcfarlane on 2007-05-30
Guess I should have tried searching the forums for 'Wacom' rather than 'scroll wheel'!

[https://help.ubuntu.com/community/Wacom#fndef-8b312f1d3e82635df77c28ee18c0f755afb650ea-0](https://help.ubuntu.com/community/Wacom#fndef-8b312f1d3e82635df77c28ee18c0f755afb650ea-0)

Problem solved.

---

