---
title: "Need urgent Help"
date: 2008-04-12
forum: General Help
---

### Post by K.Morgan on 2008-04-12
OK I'm not sure what's happened but i just turned my computer on and it loaded into grub, i then continued to select Ubuntu, everything seemed to be fine, but then i got some text on the screen which then finished with me being in the command prompt.

I re-booted thinking i accidentally selected recovery mode instead of normal boot, selected normal boot and the same happened again.  I can't get into Ubuntu.

Anybody know what i can do to stop it loading into the command prompt?

Kristian

---

### Post by sekinto on 2008-04-12
Have you done anything recently, like changed video drivers, installed new software, et cetera?
Also, were there any error messages in the boot text?

---

### Post by forestpixie on 2008-04-12
Have you had a kernel update - are you running gutsy - can you boot with an old kernel?

---

### Post by K.Morgan on 2008-04-12
I have been messing with the ALSA drivers trying to get my sound card to work so i may have done something there though I'm not sure.

There were no error messages that i recall during the boot either.

As for the Kernel, i haven't done anything with that and am using the Live CD at the moment to access this forum.

Kristian

---

### Post by forestpixie on 2008-04-12
Don't know if I'll be able to help with that. When you boot does the screen end with an error before you get to the prompt, if it does that could help. If you did things through terminal there should be a record of commands you used - I assume that if you changed files you didn't make a backup.

---

### Post by K.Morgan on 2008-04-12
Right this is what i get when Ubuntu boots.

The Ubuntu logo shows and the progress bar goes up as it's suppose to the i get this:


kinit: trying to resume from /dev/disk/by-uuid/30803379-69f4- (and a bunch of other numbers)

kinit: no resume image, doing normal boot...

ubuntu 7.10 kristian-desktop tty1

kristian-desktop login:


I then enter my user name and password, which then puts me into the command line displaying the same first line you get when loading terminal.


Kristian

---

### Post by prshah on 2008-04-12
> **K.Morgan said:**
> text on the screen which then finished with me being in the command prompt.


If you can tell us the text or include a screenshot (with a digital camera) it would be helpful. As would the output of ```
dmesg | tail -20
``` (But _NOT_ when running off the live CD.).

---

### Post by forestpixie on 2008-04-12
This might help - but I offer no guarantee :) - quick search found this [thread]("http://ubuntuforums.org/showthread.php?p=4665089") which if I was in your position is probably what I'd be trying out.

Post back if it doesn't help or you're not sure.

---

### Post by K.Morgan on 2008-04-12
Thanks for the help,  None of the commands given in other thread worked though.  Looks like I'll have to re-install :(


Kristian

---

