---
title: "Changing GRUB bootscreen"
date: 2012-12-30
forum: General Help
---

### Post by ClockworkSwordfish on 2012-12-30
Trying to change the GRUB boot screen background, I found many how-tos that deal with editing the .conf file, but I heard about a way a while ago (for GRUB 2 only, I think) to change the splash screen that required just copying the file to the appropriate folder, no .conf editing needed. Anyone hear of this? I don't want to mess around with GRUB more than I have to.
Thanks!

---

### Post by Lila7714 on 2012-12-30
I think you can just put a jpeg, tga, or png in /boot/grub/ and run 'sudo update-grub'

---

### Post by oldfred on 2012-12-31
I have not used it.

       Post Your Grub 2 Themes -  drs305
[http://ubuntuforums.org/showthread.php?t=1823915](http://ubuntuforums.org/showthread.php?t=1823915)
A Beginner's Guide to Theming GRUB2 - towheedm  & post #28 for grub2 2.00
[http://ubuntuforums.org/showthread.php?t=1534689](http://ubuntuforums.org/showthread.php?t=1534689)

---

### Post by Pjotr123 on 2012-12-31
I have done it myself, repeatedly and successfully. This is my how-to:
[https://sites.google.com/site/easylinuxtipsproject/beautifygrub](https://sites.google.com/site/easylinuxtipsproject/beautifygrub)

Good luck! :)

P.S.: I've been doing this for years on my multi-boot systems, and in my opinion it's a pity that Ubuntu doesn't have a nice themed Grub background by default, like openSUSE has. It would really make having a dual boot system much more attractive-looking. 

Even for those who usually boot Windows from it.... A couple of years ago I even suggested it on Launchpad, but unfortunately to no avail.

---

### Post by ClockworkSwordfish on 2012-12-31
Yup, just putting the file in /boot/grub and then running "grub-update" did the trick just fine. Thanks!

That was very easy, it really is a shame Ubuntu doesn't come with a cool boot screen. I really liked Debian's spacey one, and OpenSuse's was pretty good too. I am more surprised Ubuntu doesn't have one. Anyway...

---

