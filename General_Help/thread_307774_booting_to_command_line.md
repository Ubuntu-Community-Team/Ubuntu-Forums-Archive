---
title: "booting to command line"
date: 2006-11-27
forum: General Help
---

### Post by betawind on 2006-11-27
Okay...2 questions here...

First off, how do I boot straight to command line?  I'm used to debian where I got to see all the nitty gritty and then got my beautiful login: prompt.  Can I get this w/ Ubuntu?  And if so, how?

Second, when I switch to a command line via CTRL+ALT+F2 (or any F key) I do get the console login, but the font is...different than what I'm used to.  Its almost as though the command line is emulated or something.  Any thoughts?

~Beta

---

### Post by junglepeanut on 2006-11-27
Just guessing, you could uninstall gdm.

In here there is a post about changing the fonts of the tty. Long time since I read it.

---

### Post by betawind on 2006-11-27
I dont want to kill GDM all together though, I just want to be able to manually boot to it.  For some reason I find it comforting to boot directly to CLI...call me crazy.  I'll see if i can find that post on changing tty fonts, thanks for the heads up on that.

~Beta

---

### Post by junglepeanut on 2006-11-27
You know I think some one just commented it out of a start file once to get what they wanted, I'll see if I can find that one as that is a common question: from people who migrate from debian or were shown linux by somebody who used a debian system. Not sure why as I had a debian that did not do that, but it was when I was much newer than the new guy I am now, so somebody helped me configure it.

---

### Post by betawind on 2006-11-27
If you could find that, I would definitely appreciate it.  I'll do some searching myself on that subject.

---

### Post by junglepeanut on 2006-11-27
[http://ubuntuforums.org/showthread.php?t=299165&highlight=gdm+start](http://ubuntuforums.org/showthread.php?t=299165&highlight=gdm+start)
[http://ubuntuforums.org/showthread.php?t=291731&highlight=gdm+start](http://ubuntuforums.org/showthread.php?t=291731&highlight=gdm+start)

These talk about run levels, I figure some one smart will chime in real soon, both mention 3 being low enough.

---

### Post by junglepeanut on 2006-11-27
[http://doc.gwos.org/index.php/Speed_up_boot](http://doc.gwos.org/index.php/Speed_up_boot)

This shows a nice little speed up process and one of the options you can have is to turn gdm on or off.

Maybe this is what you are looking for, I could not find the right option on mine by changing files, but this should work.( I even renamed some gdm.conf files and it went on like I did nothing when I rebooted.)

---

### Post by betawind on 2006-11-27
Found the solution to the font issue...kind of...if I add a vga=### line to my Ubuntu Kernel line in /boot/grub/menu.lst I get a better resolution, which is what I wanted all along.

Regarding the gdm start issue, thanks to both of you for the links...I'll do some reading and see what I can find.

---

