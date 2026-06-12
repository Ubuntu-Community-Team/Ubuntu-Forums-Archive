---
title: "How does one boot to console - no gui?"
date: 2008-05-09
forum: General Help
---

### Post by 01000111 on 2008-05-09
Greetings all,
I have Xubuntu 8.04 running on a 15GB partition and back it up with partimage.  To do this, I boot from the LiveCD, install partimage, create the image, then reboot normally.  As I'm rather paranoid, and make lots of changes to my environment, I do this fairly often... typically once/week or more.

Is there a method to boot to the console without the GUI starting to reduce boot time?  If not, is there a good howto describing how I can create a minimal custom livecd that boots with no gui and has partimage installed?

Any assistance is appreciated.

01000111

---

### Post by songshu on 2008-05-09
what happened to /etc/inittab ??????

back in the days that i started with linux nobody knew how to startx nd we had to fiddle woith vertical and horizontal refresh rates (good luck finding that in your monitors documentation)

apparently inittab has been replaced?

i wouldn't dare to recomend the below link with confidenence because i never used it myself and i just found it on google after not being able to find inittab.

so please read the warning on that page and come back and let us know ;)

[http://caulfield.info/emmet/2008/03/add-a-textonly-runlevel-to-ubu.html](http://caulfield.info/emmet/2008/03/add-a-textonly-runlevel-to-ubu.html)

---

### Post by Monicker on 2008-05-09
Debian/Ubuntu do not use /etc/inittab, though it is still alive and well in other distros.  ;)

---

### Post by songshu on 2008-05-09
> **Monicker said:**
> Debian/Ubuntu do not use /etc/inittab, though it is still alive and well in other distros.  ;)

etch still uses it.

but i noticed  /etc/event.d/rc-default in the link i posted, i do not seem to be able to find that one on my gutsy tough.

somebody has some experience with this?

---

### Post by vdawg on 2008-05-09
> **01000111 said:**
> Greetings all,
I have Xubuntu 8.04 running on a 15GB partition and back it up with partimage.  To do this, I boot from the LiveCD, install partimage, create the image, then reboot normally.  As I'm rather paranoid, and make lots of changes to my environment, I do this fairly often... typically once/week or more.

Is there a method to boot to the console without the GUI starting to reduce boot time?  If not, is there a good howto describing how I can create a minimal custom livecd that boots with no gui and has partimage installed?

Any assistance is appreciated.

01000111

I had this same problem of needing just to boot into the console, but I have ubuntu with gnome (gnome display manager: gdm). I will post my solution, maybe it can help you as well.

[FONT="Courier New"]
sudo apt-get install rcconf
sudo rcconf
[/FONT]
and then I set the gdm to not display on boot :)

OR

use the boot up manager (under the system menu), and disable the gdm

---

### Post by 01000111 on 2008-05-09
Isn't there just some param I can add to the grub line to do a text-only boot?

---

### Post by vdawg on 2008-05-09
> **01000111 said:**
> Isn't there just some param I can add to the grub line to do a text-only boot?

Try the rcconf :)

---

### Post by songshu on 2008-05-09
xubuntu uses gdm as well..

vdawg has the answer i think

---

### Post by 01000111 on 2008-05-09
> **vdawg said:**
> Try the rcconf :)

That looks promissing, but how would I use that with the LiveCD?

---

### Post by songshu on 2008-05-09
[http://minibuntu.crealabs.it/](http://minibuntu.crealabs.it/)


try this one

---

### Post by vdawg on 2008-05-09
Hmm, the boot-up manager on the live-cd should do the trick, I do know that you can save your livecd configurations on the disk to be read back in, hopefully it will do for the boot-up manager as well :)

---

### Post by 01000111 on 2008-05-09
> **songshu said:**
> [url]http://minibuntu.crealabs.it/[/url

That looks like what I need.  I'll give it a try and let you know.

Thanks!

---

### Post by 01000111 on 2008-05-09
> **vdawg said:**
> Hmm, the boot-up manager on the live-cd should do the trick, I do know that you can save your livecd configurations on the disk to be read back in, hopefully it will do for the boot-up manager as well :)

I suppose I can use bum to modify my current environment to not load the gui, then make a livecd from my boot partition???

Does that sound right?

I'm surprised that there isn't a Linux equivalent of the DOS boot floppy.

---

### Post by vdawg on 2008-05-09
Err no, you boot using the livecd, then set the bum not to load the gui, the livecd should save your settings and then when you boot back using it, it wont load the gdm.

It's been a while since I used a livecd (touchwood) but when I did I remember changing the desktop background etc, and it saved my settings somewhere on the hdd. I don't remember if it was automatic or if I had to click a button to tell it to save my configuration etc.

PS: Live cd is the equivalent of a boot floppy, except much more powerful. There are other livecds that are purely for diagnostic purposes and wont load a X-session., check this out : [http://www.frozentech.com/content/livecd.php](http://www.frozentech.com/content/livecd.php)

Good luck!

---

### Post by Verstege on 2008-05-09
Just append a simple <blank>s to kernel parms to boot into single user mode.

Cheers

---

### Post by 01000111 on 2008-05-09
Ah.

Perhaps I'm going about this the wrong way...  I'm simply trying to make a backup of my Xubuntu partition so when I screw it up, I can put it back.  I've been using partimage, but one cannot make an image if its currently mounted, that's why I need to boot with the livecd.

Is there a better/easier/faster way?

---

### Post by songshu on 2008-05-09
> **01000111 said:**
> 
I'm surprised that there isn't a Linux equivalent of the DOS boot floppy.

there is, millions of them, but usually not recognised as usefull by the ubuntu crowd due to the lack of firefox integration and shiny buttons with a human theme.

you could actually also use the alternate cd and cancel the installation before formatting the disk.

apt-get install partman and mount whatever you would like to mount


*edit* what exactly would you like to make a backup of and where do you want to put the backup?

---

### Post by 01000111 on 2008-05-09
> **Verstege said:**
> Just append a simple <blank>s to kernel parms to boot into single user mode.

Nah... can't be THAT easy!?!?  I'm going to try that right now.

---

### Post by niteshifter on 2008-05-09
Hi,

Take a look at [SystemRescueCd]("http://www.sysresccd.org/Main_Page"), as you're already familiar with partimage. Console mode is default - but you can use a GUI if you like, Has a good set of tools, can run in RAM (freeing up your CD/DVD writer) and has UDF support for CD / DVD writing.

---

### Post by 01000111 on 2008-05-09
> **Verstege said:**
> Just append a simple <blank>s to kernel parms to boot into single user mode.

Nice... just what I was looking for.... But it takes almost as long to boot as with the GUI.


[QUOTE=niteshifter]Take a look at SystemRescueCd, as you're already familiar with partimage. Console mode is default[/QUOTE]

Thanks.  I'll take a look at that as well.

01000111

---

### Post by Th3Professor on 2008-05-09
> **G said:**
> I'm surprised that there isn't a Linux equivalent of the DOS boot floppy.

DOS as in MSDOS? *nix predates *DOS. There was a Unix "boot floppy" long before DOS. :) (Before Ubuntu's days, or even Debian.)

Just a quick look at, and very basic look, at the age of the systems...

Unix is nearly 40 years old, ("UNICS", or older if you consider Multics);
[MSDOS is around 30 years old];
Linux is close to 20 years old,
(Debian's around 15 years old),
(Ubuntu's ~3 years old).

The floppy disk dates back to the beginning of UNIX.

The thing is, so many Linux (and even Unix) systems these days are so GUI-heavy that it requires removing GUI to get just a "CLI".

If you like using the command line interface and would like to avoid any GUI, you might consider Unix over Linux. However, there are plenty of Linux systems that also easily allow for non-GUI set-ups. I'm referring to from the point of install, not simply disabling it (as in not even installing GUI).


:guitar:

---

