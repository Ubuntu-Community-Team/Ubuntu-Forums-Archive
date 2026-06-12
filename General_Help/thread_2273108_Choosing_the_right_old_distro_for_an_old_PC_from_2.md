---
title: "Choosing the right old distro for an old PC from 2000"
date: 2015-04-10
forum: General Help
---

### Post by OhLongCat on 2015-04-10
*A little pre-history*. [br]1[/br] I've got at my disposal an old PC from around the year 2000 with Pentium II 400Mhz/RAM 256MB/HDD 40GB/NVidia 32Mb + USB. So it is not so bad, especially the memory (must have been upgraded some years after 2000), but the CPU is a little slow. It has had a buggy Windows XP PE with "extras" (simply unneeded "bells and whistles") from an unreliable unknown source ("some tech guy"). I did not know from where it came and even did not want to check if it had trojans/viruses, so I simply erased the disk and decided to give the PC a second more fair life with Linux. After a little research I chose Lubuntu 14.04 LTS. Surprisingly enough it ran from a USB stick, and even was installed in the GUI regime (though it took about 2 hours, I do not know why). It works quite bearable, I even installed and run LibreOffice. Nevertheless browser (Firefox 34) was unusable at all. It takes up to 3 minutes to simply start it, not to mention you can hardly browse. So after some consideration I installed Windows 2000 additionally onto a second partition. It runs much smoothly, but one thing bothered me: I had to install older versions of software (for example LO 3.6 and Firefox 12 + Flashplayer 11, all are from 2012 - it looks like the ultimate date when everybody stopped supporting Windows 2000). It even plays Flash video, though slow and buggy (I do not know whether it's the fault of the slow CPU or the old system/programs).  [br]1[/br] In general I could leave it as is, but still want some experimenting. I'm also worrying about safety issues even though I installed ClamWin (thanks at least this is up-to-date). Now I want to try another older distro along with the Lubuntu and Windows 2000. [br]2[/br] **The PC must do these tasks**: [br]1[/br] 1) General file management (including USB sticks and archives). [br]1[/br] 2) Text/spreadsheet processing (old OO.o/LO is OK). [br]1[/br] 3) General basic internet browsing with Noscript or alike. It's important. [br]1[/br] 4) Some minor additional tasks (viewing PDF/Djvu and images, listen to MP3, OCR maybe). [br]1[/br] 5) Bonus feature: watching flash videos and watching stream-TV (based on flash). As I said it works with Windows 2000, so nothing is impossible. [br]1[/br] *Very important*: the distribution's GUI must have Russian localisation. The persons who will use the PC do not know English at all. It also must be as close to Windows-like GUI as possible (though there is no much choice: older GNOME, KDE or Lxde). [br]1[/br] **Now my questions**: [br]1[/br] 1) What to choose: Debian, Ubuntu or Mint. I do not consider other distros, as I am acquainted only with the above-mentioned, and they are enough for my goal.  [br]1[/br] 2) What version? I lean to the versions from around 2005-2007. Debain Sarge (2007)/Lenny(2009) or Ubuntu Edgy (2006)/Feasty(2007). I need not too old but not to new to work smoothly. [br]1[/br] 3) How is safe to use older outdated releases? I mean not in an ideal sense but as safe as Windows2000+ClamWin or safer. My main concern is viruses which could be got from an infected USB stick or from downloading some dodgy .exe. Yes, I know there are a lot of other safe issues, and Linux also has viruses/trojans, but anyway it seems much difficult to infect a Linux PC with viruses. [br]1[/br] 4) Could more recent versions of programs be installed to an older release? Say, could I install Firefox 30 + recent Flashplayer to Debian Sarge? Will it work? Is it worth to install new programs? I'm bothered only with browser, older versions of other software (like LO) is OK. [br]1[/br] P.S. Options "throw this out" or "buy upgrade" are not considered. [br]1[/br] P.S.2. I know there exist similar threads about old hardware, but I wanted advice about my particular situation.  [br]1[/br] P.S.3. Tried Debian 5 Lenny "live CD" from USB, it is not much faster than Lubuntu 14.

---

### Post by QIII on 2015-04-10
Hello.

Would you please edit this WOT (Wall Of Text) so that is in paragraph form?

As it is, it will probably drive many would-be helpers away.

---

### Post by Holger_Gehrke on 2015-04-10
The Ubuntu versions you mentioned are all **way past End of Life**. You won't even get critical security fixes for them and would have to compile a lot of software yourself to work with the older than dirt libraries you'd have...
Using Lubuntu and light weight applications is probably your best bet. The worst problem I see in your situation is the web browser. Both firefox and chrome are memory hogs which tend to stall if you don't have at least 1G of RAM; the long start up time for ff you wrote about is down to the fact that it started swapping before it was even completely loaded ...

---

### Post by OhLongCat on 2015-04-10
> **QIII said:**
> Hello.  Would you please edit this WOT (Wall Of Text) so that is in paragraph form?  As it is, it will probably drive many would-be helpers away. Done. Looks like a [forum bug](http://ubuntuforums.org/showthread.php?t=1531988), it does not understand line breaks, I've added them manually.

---

### Post by CaptainMark on 2015-04-10
Your title makes me feel old, please change it.

---

### Post by QIII on 2015-04-10
You needn't try to use bbcode.  You can type in plain text and put in line breaks with the "enter" key, as you can with a text editor.

Like I just did.

1. This.

2. That.

---

### Post by OhLongCat on 2015-04-10
> **Holger_Gehrke said:**
> The Ubuntu versions you mentioned are all **way past End of Life**. You won't even get critical security fixes for them and would have to compile a lot of software yourself to work with the older than dirt libraries you'd have...  I 'm not a programmer and hardly understand this "security-fix" anxiety and you see I will not plan to run a server or some very important thing, and hardly any hacker would try to intrude into my PC. The last update of Win2000 was from 2005. Not to mention I have another old PC which goes to internet with Win98 quite happily (with no Javascript and Flash though)...

---

### Post by QIII on 2015-04-10
Please see [this]("http://ubuntuforums.org/showthread.php?t=2229730").

We would rather not have those who volunteer on these forums spend their time attempting to address problems with EOL, unsupported versions of Ubuntu.

One need not be a programmer to understand this:  Those versions pose a security threat to you whatever your use of them, the repositories have been moved and you cannot update the software any longer and yes, people will take advantage of your personal computer if they can.

---

### Post by OhLongCat on 2015-04-10
> **QIII said:**
> You needn't try to use bbcode.  You can type in plain text and put in line breaks with the "enter" key, as you can with a text editor.  Like I just did.  1. This.  2. That. I tried, it didn't work, it deletes line breaks. The first time I encounter this in a forum. Maybe my browser or something. Not too important though, sorry for off-topic.

---

### Post by kerry_s on 2015-04-10
i think just simple & works should be good enough, your lucky it still runs in the first place.
[http://sourceforge.net/projects/elementaryos/](http://sourceforge.net/projects/elementaryos/)

---

### Post by OhLongCat on 2015-04-10
> **QIII said:**
>  We would rather not have those who volunteer on these forums spend their time attempting to address problems with EOL, unsupported versions of Ubuntu. OK, you or other very busy tech guys needn't pay attention to my problem if you think it is "worthless", but I hope someone other might help.  >  One need not be a programmer to understand this:  Those versions pose a security threat to you whatever your use of them, the repositories have been moved and you cannot update the software any longer and yes, people will take advantage of your personal computer if they can. Unfortunately not. For me, a not too tech-savvy commoner, "security thread" are just two meaningless words. I need a particular obvious tangible example why I shouldn't use, for example, Ubuntu 5 or alike.

---

### Post by Holger_Gehrke on 2015-04-10
> **OhLongCat said:**
> ... and hardly any hacker would try to intrude into my PC.
But an automated system like a BotNet would just love to welcome your machine into the army of DDoSing, spam sending zombies. Worms and trojans that do this kind of stuff **do** exist on Linux ...

> **OhLongCat said:**
> 
The last update of Win2000 was from 2005. Not to mention I have another old PC which goes to internet with Win98 quite happily (with no Javascript and Flash though)...

And only the missing Javascript and Flash are protecting your machine from being someone else's plaything ... Do yourself a favour, get the avira bootdisk (a linux bootdisk with a program to search for windows malware) or something similar to it and have it run a check on that Win98 box ...

---

### Post by OhLongCat on 2015-04-10
> **kerry_s said:**
> i think just simple & works should be good enough, your lucky it still runs in the first place. [http://sourceforge.net/projects/elementaryos/](http://sourceforge.net/projects/elementaryos/) Thanks, but I fear it will not work. For all these "old PCs distros"  an "old PC" means 5-10 years old. I tried Puppy Linux, but it works very slowly on my PC. Pity, there are no distros for 90s PCs. They deserve to live a second life! :)

---

### Post by QIII on 2015-04-10
> **OhLongCat said:**
> OK, you or other very busy tech guys needn't pay attention to my problem if you think it is "worthless", but I hope someone other might help.   Unfortunately not.

I am merely making the policy of the Forum Staff (also volunteers) known to you.  If you care to contest it, you are welcome to post in the Resolution Center.

---

### Post by matt_symes on 2015-04-10
Hi

I get the impression you don't know much about Linux and computers. That  comment is not intended as a slight as there are many more subjects i  know nothing about than those i do.

> P.S. Options "throw this out" or "buy upgrade" are not considered. 
 P.S.2. I know there exist similar threads about old hardware, but I wanted advice about my particular situation.

I would suggest in your situation though, you may have already decided to ignore the best advice that may be given to you.

Don't use an old distribution. It will be more hassle for you than you need. You won't be able to run new versions of software on an older version of *ubuntu without much, much difficulty.

Even if you don't understand what a "security threat" is, take any advice that says you want to avoid them. After all giving out your pin number for your credit or debit card is a "security threat" and you would not do that.

My advice is to try a small distribution such as one of these as these may be your best bet.

slax - [https://www.slax.org/en/download.php](https://www.slax.org/en/download.php)
slitaz - [http://www.slitaz.org/en/get/](http://www.slitaz.org/en/get/)
tinycore - [http://www.tinycorelinux.net/downloads.html](http://www.tinycorelinux.net/downloads.html)
puppy - [http://puppylinux.org/main/Download%20Latest%20Release.htm](http://puppylinux.org/main/Download%20Latest%20Release.htm)

And good luck as that is old hardware.

EDIT:

I see you've tried puppy. It's bigger than the others i listed above so try one of them instead.

Kind regards

---

### Post by OhLongCat on 2015-04-11
> **matt_symes said:**
>  I get the impression you don't know much about Linux and computers. That  comment is not intended as a slight as there are many more subjects i  know nothing about than those i do.   I've sincerely admitted I'm not a tech guy, I have another profession and proud of it. Maybe, an advanced user, who knows tricks here and there. But I can assure you I'm more advanced than the others, 99% people around me does not know about Linux at all, not to mention how to install, for example, dual boot. I just give you an example. I managed to find out how to: 1) install Lubuntu from a USB stick, while the target PC does not support USB boot; 2) install Windows 2000 after that: you understand that I broke the grub, but I found out how to correct it (boot-repair, yes); 3) I found out what versions of old software are working with Windows 2000 (took me some time for research). Hardly anybody other around me would do this. They just threw out a quite workable PC and I'm trying to bring it back to life. If this forum for tech guy, y'all must have said this in big letters for any newbies, but I thought it's for people with rather much less knowledge and experience than me.  > **matt_symes said:**
>  Don't use an old distribution. It will be more hassle for you than you need. You won't be able to run new versions of software on an older version of *ubuntu without much, much difficulty.  Even if you don't understand what a "security threat" is, take any advice that says you want to avoid them. After all giving out your pin number for your credit or debit card is a "security threat" and you would not do that.  Credit cards? You're kidding. I've already explained for what I'm doing the PC: a "typewriter" with a potential of working in internet (to find some stuff, like document templates). I have even a little older PC which does these tasks with Win98, why this particular PC cannot do them also? [br]1/[br] I have now little options. Whether it's Windows 2000, that has the latest security updates in 2005 or it's Ubuntu from the same 2005. At least in Ubuntu it's impossible to run some dodgy .exe from a USB stick. Are you trying to say that Windows 2000+ClamWin is much safer than Ubuntu 5? Bad news then, similarly Windows 8 must be safer than Ubuntu 14 as well.  > **matt_symes said:**
>   My advice is to try a small distribution such as one of these as these may be your best bet.  slax - [https://www.slax.org/en/download.php](https://www.slax.org/en/download.php) slitaz - [http://www.slitaz.org/en/get/](http://www.slitaz.org/en/get/) tinycore - [http://www.tinycorelinux.net/downloads.html](http://www.tinycorelinux.net/downloads.html)  I suppose localisation of Slitaz and TineCore could be problematic, though I'll try Slax, thanks. I  also do not like such marginal distributions, this is why my choice fell upon something more mainstream. Looks like my mistake. No-one answered my particular questions.

---

### Post by bapoumba on 2015-04-11
> **OhLongCat said:**
> I tried, it didn't work, it deletes line breaks. The first time I encounter this in a forum. Maybe my browser or something. Not too important though, sorry for off-topic.
Off topic I agree, and late reply that is, but are you allowing yahooapis ?

---

### Post by OhLongCat on 2015-05-20
> **bapoumba said:**
> Off topic I agree, and late reply that is, but are you allowing yahooapis ? Everything is on, but it still does not work.

---

### Post by mattharris4 on 2015-05-21
> **OhLongCat said:**
> *A little pre-history*. [br]1[/br] I've got at my disposal an old PC from around the year 2000 with Pentium II 400Mhz/RAM 256MB/HDD 40GB/NVidia 32Mb + USB. **. . . **

Tiny Core sounds and looks interesting and claims to run on a computer with a PII and 128MB RAM.  Your computer meets those specs.  Frankly you are lucky there is still an OS with a graphical user interface that will run on such hardware.  If I absolutely had to use a computer with those specs that is the OS I would probably try on it.  

Slax will supposedly run on computers as old as an i486 but I cannot determine if it has a graphical user interface and if it has internet capabilities.  Without those features a modern OS is next to useless.

I know I would not use the internet on an EOL version of anything, especially for tasks requiring personal information such as your Social Security number, name, address or bank account/credit card information.  It is too easy for a hacker to sneak code onto your computer to send such information to him -- with that he could ruin your credit or even commit crimes and give your information to the police claiming to be you, get out on bail and go on the run.  If the latter happened theoretically you could go to prison for his crimes, certainly you would get arrested, handcuffed, taken to jail, strip searched, locked in a cage with murderers, rapists, etc. (and them doing God knows what to you) and spend time in jail until the police figure out they have the wrong guy.  That is why you do not use an OS without adequate security features -- like an EOL OS.

---

### Post by mattig89ch on 2015-05-21
I'm sorry, I didn't see this in your original post, what video card are you working with?

I've used ubuntu on and off for years, and the most recent version should still work on your old hardware.  But you may have to use the command line for a bit, until you find a minimalistic ui you can install.

---

