---
title: "[SOLVED] Hewlett-Packard Scanjet 2400"
date: 2005-10-18
forum: General Help
---

### Post by vyruss on 2005-10-18
I have an HP Scanjet 2400 scanner which refuses to work in XSane and Kooka. Instead, I get a screenshot from my TV card (!) and never get the option to choose the scanner.

Has anybody had any success with getting this baby to work?

---

### Post by Rogmo on 2005-10-18
Take a look in here:

[http://lists.alioth.debian.org/pipermail/sane-devel/2003-September/008803.html](http://lists.alioth.debian.org/pipermail/sane-devel/2003-September/008803.html)


Hopefully that helps you :)

---

### Post by tobassam on 2005-10-26
Exact same problem here, the article pointed to above is 2 years old ! Come on, there must some progress on this since then ?!

---

### Post by nicknack on 2005-11-21
Hi, 

I see i'm not the only one with this problem.
I've seached a lot of sites, but can't find a driver for the scanjet 2400.
:confused: :confused:

---

### Post by andrebtoda on 2006-10-25
> **nicknack said:**
> Hi, 

I see i'm not the only one with this problem.
I've seached a lot of sites, but can't find a driver for the scanjet 2400.
:confused: :confused:

one year...

someone have the solution??

the hpoj dont recognize my scanner...](*,)

---

### Post by vyruss on 2006-10-27
> **andrebtoda said:**
> one year...

someone have the solution??

the hpoj dont recognize my scanner...](*,)

It sounds crazy, but SANE still does not support this scanner. How unbelievably hard can it be to write a driver for it?

---

### Post by mahiyar on 2007-01-11
This is the first real disappointment  with Ubuntu,  and to find out that the problem has been around  for  years.  My model  of scanner  HP-2400 is  some   years old, and still nobody could write a driver or do people think that linux can do without scanners.

---

### Post by ofir_k on 2007-01-22
I have the same problem.

I also tried, several times, to write a driver for this scanner, but the documentation in SANE's site is hard to understand.

If someone has a good tutorial on how to write a SANE backend, please post it here (or give a link to it).

---

### Post by ofir_k on 2007-01-22
I contact HP regarding this issue, and this is the email I got:
> 
Thank you for contacting HP Total Care.

I understand that you want to use your scanjet 2400 scanner on a Linux
environment.

Ofir, I really apologize for the fact that the Linux compatible drivers
are not yet available for your scanner, however, our Research and
Development team are working on it and it should be available soon.

I would request you to sign up at the below mentioned website so that
you are informed when the driver is available:

[http://www.register.hp.com](http://www.register.hp.com)

I think that we should contact them regarding this issue - if a large group of people will contact them, they will release drivers and softwares immediately!

---

### Post by mahiyar on 2007-01-22
Good, thanks ofir_k, will do it immidiately. Scanjet 2400 is one of the most widely used scanner in countries like India, where it provides good value for money.

---

### Post by ofir_k on 2007-01-24
The more people will send them an email, the quicker they will write a driver for the scanjet 2400.

BTW,
The scanjet 2400 is considered a good scaner for high resolution scans - it can scan at 999999x999999 (I saw this information on some store).

---

### Post by obbe on 2007-03-28
hi, still nobody has made drivers for this scanner? i must using windows when i need to scan everything :mad: :(

---

### Post by arthpix on 2007-08-07
No, there is no driver so far, but you would use a virtualized windows in order to avoid a reboot every time you need to use it. tht's the way i'm doing. Installed a Win2k with vmware player and every time i need the scanner I only have to run the VM. Pretty much fast than rebooting.

---

### Post by mdmcginn on 2007-11-20
Re: Hewlett-Packard Scanjet 2400 still isn't recognized by xsane on Ubuntu 7.10 Gutsy. But here's a link with instructions on how to make it work: 

[http://www.elcot.in/linuxdrivers_download.php](http://www.elcot.in/linuxdrivers_download.php)

I'm not sure how they can do that, since the SANE website itself says it's not supported: see [http://www.sane-project.org/sane-backends.html](http://www.sane-project.org/sane-backends.html)

---

### Post by mahiyar on 2007-11-21
mdmcginn- this procedure seems to be for kooka which is the scanning programme for kde, can we install that in Ubuntu, have you tried this in Gutsy? Basically the procedure makes do with the 5400 drivers.

---

### Post by mahiyar on 2007-11-21
No it does not work. On running sane you still get the same message "no devices available". It does not make do with the 5400 drivers, can somebody confirm whether this works in "kooka" ?

---

### Post by mahiyar on 2007-11-21
No it does not work in "kooka" also at  least not in gnome environment.

---

### Post by mahiyar on 2007-11-21
:guitar:  It works, and beautifully, from xsane. What had happened that somehow the file extraction had not worked even after using sudo. So there were no files in /usr/lib and /usr/lib/sane. I copied from the cmd line each file to the folder, restarted the computer and voila !!!! it worked. So finally after waiting for about a year my final hurdle has been removed. Thanks mdmcginn, thanks a ton. BTW the other drivers shown in the site are for **printers** Samsung ML 2010, Xerox phaser 3117, **scanners **HP Scanjet 2400, HP Scanjet 8300.

---

### Post by mahiyar on 2007-11-21
The result of my first scan.

---

### Post by Sain on 2008-01-19
Does this really work? Can someone confirm this?

I've been waiting for linux drivers for HP 2400 for ages now, this is too good to be true :) I'll give it a try when I get home..

---

### Post by rocktorrentz on 2008-01-19
> **Sain said:**
> Does this really work? Can someone confirm this?

I've been waiting for linux drivers for HP 2400 for ages now, this is too good to be true :) I'll give it a try when I get home..
It definitely works (well it does on my arch linux install).

---

### Post by Sain on 2008-01-21
I keep getting "No scanners were identified" message after using scanimage -L command. What am I doing wrong?

---

### Post by Sain on 2008-01-21
Nevermind, I got it to work. I just skipped to the next step and edited dll.conf. After that scanimage -L identified the scanner...

---

### Post by endofnow on 2008-07-02
Just another confirmation. Worked fine for my Scanjet 2400 on Ubuntu 8.04.

---

