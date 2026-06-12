---
title: "ATi driver problems (Gutsy)"
date: 2007-10-20
forum: General Help
---

### Post by Peior Crustulum on 2007-10-20
Hi!

As I am completely new to Ubuntu (linux in general) I find venturing into the different aspects of the OS interesting, but complicated.
My current problem is a black screen at startup after I installed the restricted graphics driver.

Asus Striker Extreme
HIS Radeon HD 2900
C2D E6700
4GB Corsair Dominator 6400
Crappy SMC Wifi card that barely functions under windows but works smoothly under Ubuntu

I also wonder how I can install the Linux driver from ATi's website.
It may work better?

Any help is greatly appreciated.

---

### Post by ihcnet on 2007-10-20
You might want to try the guide found here [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide). However, it's for the 8.40.4 version of the driver, and for that particular card they're on version 8.41.7.

---

### Post by Radamand on 2007-10-21
bleh, I have the exact same problem, with the exact same ATI card, ive gone thru that installation twice now with the exact same results, black screen after ubuntu loading screen.

---

### Post by OzzyFrank on 2007-10-22
Hi. I'm having a different problem with a different ATI card, but it all comes down to ATI support in Ubuntu being rather lousy (though this is probably more ATI's fault). I've never been able to get past a black screen when trying to run the **[COLOR="Purple"]fglrx[/COLOR]** driver for more advanced ATI features for my 9200, and have always had to use the generic **[COLOR="#800080"]ati[/COLOR]** driver. At least that worked (let's not even mention the crappy useless installer ATI themselves so kindly released!).

But after upgrading to Gutsy, I can't even use that, but have to use an old [COLOR="#800080"]**vesa**[/COLOR] driver, which has robbed me of some screen resolutions (I know how to set them - they just ain't happening). I also suspect it is what is making DVD playback choppy (at best... in some programs it is downright spastic). And that was after getting back DVD playback (gotta love Gutsy!!).

Anyway, here is the link to my post for any interested:

[http://ubuntuforums.org/showthread.php?t=582357](http://ubuntuforums.org/showthread.php?t=582357)

For those who would like to know how to reset their display, you need to _boot into recovery-mode_, enter the _root password_, then start the wizard with:

**dpkg-reconfigure xserver-xorg**

Go through the options and when the list of drivers is displayed, pick a different one. If using a more advanced driver previously, try **[COLOR="#800080"]ati[/COLOR]** - if that doesn't work, [COLOR="#800080"]**vesa**[/COLOR] should. Just don't bother with [COLOR="#800080"]**vga**[/COLOR] as it will just die after complaining it can't support 24-bit colour (you can specify lower of course, but I wouldn't bother personally).

Exit the wizard and type **startx** or even **gdm**, and you should be able to get into Ubuntu. Then just hope some updates for whatever went wrong come along soon. Hope this helps someone. Cheers

---

