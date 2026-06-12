---
title: "Lilo replaced Grub"
date: 2015-09-20
forum: General Help
---

### Post by mark242 on 2015-09-20
Hi all

I am mystified - i shut down my computer yesterday and when i booted today my nice and nifty grub2 was replaced with a very ugly ascii type lilo bootloader.

I have tried to do an update-grub with no success - i have 3 os's ubuntu / winslow / kali linux. I have not installed anything recently so I am fussed as where this weird problems originates from.

I have no clue as to what to search for so i am sorry for reposts.

I tried to figure out how to change the lilo bak to frub2 but cant find out how.

TIA

---

### Post by yancek on 2015-09-20
I really don't think that Lilo is going to suddenly appear.  None of the operating systems you use have Lilo as a default, in fact few Linux systems still use it.  How do you know it is Lilo?  Maybe the bootloader got messed up and it is booting in text mode.  I think you will need to provide more details.  Frist are you able to boot anything and if so, what?  if you can boot Ubuntu, you should be able to reinstall and update Grub with root permissions if that is what you want.

---

### Post by mark242 on 2015-09-20
The menu says Lilo. I get 2 choices ubuntu and ubuntu old. - booting bot ends me up in my old usual ubuntu part.

---

### Post by mark242 on 2015-09-20
[IMG][IMG]http://i60.tinypic.com/2uyggh0.jpg[/IMG][/IMG]

---

### Post by mark242 on 2015-09-20
Thanks for the hint Yancek - after some searching around and testing i found a solution.

sudo grub-install /dev/sda
sudo update-grub2

---

### Post by yancek on 2015-09-20
Curious as to how something like that happened.  I don't even know if Lilo is in the Ubuntu repositories but it usually won't install itself.  The only Linux systems that currently use Lilo are Slackware and a few of its derivatives.  You got it working which is all that matters.

---

### Post by mark242 on 2015-11-13
> **yancek said:**
> Curious as to how something like that happened.  I don't even know if Lilo is in the Ubuntu repositories but it usually won't install itself.  The only Linux systems that currently use Lilo are Slackware and a few of its derivatives.  You got it working which is all that matters.

The problem keeps coming back - it happned 2 times now - the solution i found works but not permanently.

---

### Post by mark242 on 2015-11-13
I have Kali Linux installed as well - but havnt started it for ages - if I should look for files that replaces grub with grub where should i look ?

---

### Post by deadflowr on 2015-11-13
check to see that lilo is actually installed on Ubuntu.
(as you say, you also have kali)

```
apt-cache policy lilo
```
if so, try a purge command --with -s (simulate)
```
sudo apt-get purge -s lilo
```
this will give you the output of what will be removed, but without actually removing it.
if curious post the output.
otherwise you can remove the -s flag to run it for real.
then I'd re-run the grub-install commands from above.

---

### Post by mark242 on 2015-11-27
> **deadflowr said:**
> check to see that lilo is actually installed on Ubuntu.
(as you say, you also have kali)

```
apt-cache policy lilo
```
if so, try a purge command --with -s (simulate)
```
sudo apt-get purge -s lilo
```
this will give you the output of what will be removed, but without actually removing it.
if curious post the output.
otherwise you can remove the -s flag to run it for real.
then I'd re-run the grub-install commands from above.

apt-cache policy lilo
lilo:
  Installeret: 1:24.1-1
  Kandidat:    1:24.1-1
  Versionstabel:
 *** 1:24.1-1 0
        500 [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) vivid/main i386 Packages
        100 /var/lib/dpkg/status


 sudo apt-get purge -s lilo
Indlæser pakkelisterne... Færdig
Opbygger afhængighedstræ        
Læser tilstandsoplysninger... Færdig
Følgende pakker blev installeret automatisk, og behøves ikke længere:
  kde-l10n-da kde-l10n-engb linux-headers-3.19.0-15 linux-headers-3.19.0-15-generic linux-headers-3.19.0-18 linux-headers-3.19.0-18-generic
  linux-image-3.19.0-15-generic linux-image-3.19.0-18-generic linux-image-extra-3.19.0-15-generic linux-image-extra-3.19.0-18-generic
Brug »apt-get autoremove« til at fjerne dem.
Følgende pakker vil blive AFINSTALLERET:
  lilo*
0 opgraderes, 0 nyinstalleres, 1 afinstalleres og 20 opgraderes ikke.
Purg lilo [1:24.1-1]

---

