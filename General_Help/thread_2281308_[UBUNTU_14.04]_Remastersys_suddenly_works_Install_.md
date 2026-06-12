---
title: "[UBUNTU 14.04] Remastersys suddenly works Install option"
date: 2015-06-06
forum: General Help
---

### Post by David_Ramsay on 2015-06-06
Remastersys used to work pre - ubuntu 14.04 and for a while 14.04 worked.
However, for a long time, remastersys only boots the live CD option even if
you select the install option --- until today...

Hope someone can work out what made it work.

IF you see  the Install Custom Live CD icon appear on your Desktop at the start
of running Remastersys  - everything will work..

Changes made since last used remastersys a few days ago:-

Sudo chown -R <your account name> /home/<your account name>

^^ if you do sudo nautilus, you have to do this afterwards because permissions change and
thumbnailers etc stop working..  Standard procedure - for me anyway.

Downloaded and compiled / installed squashfs4.3.

Ran Relinux to test it.. given remastersys only live boots.. Without rebooting, found that when try
reconnect my tethered Internet wireless, came up - no permission to start in network manager so
I rebooted. <maybe a clue>

The only other changes was that I installed libcuda multi core development libs that kicked out
my ubuntu wine 1.7, so installed again wine1.7 that forced download of
libcuda1-331_331.113-0ubuntu0.0.4_amd64.deb.

Nice having remastersys running the install option again instead of only live booting :)

---

### Post by sudodus on 2015-06-06
Please avoid ```
[COLOR=#ff0000]sudo GUI-application[/COLOR]
``` use ```
[COLOR=#008000]gksudo GUI-application[/COLOR]
``` instead. If gksu and gksudo are missing, install

```
sudo apt-get install gksu
```

There is an important difference:

Many GUI-applications write to configuration files (often hidden files in the user's home directory). When you run them with sudo, they will be owned by root, and not available for your regular user id. (So you had to reset the ownership after running nautilus with superuser privileges.)

When you run with ***gksudo***, the configuration files will be written to root's home directory **/root**, and will not interfere with your regular user's configuration.

```
[COLOR=#008000]gksudo nautilus[/COLOR]
``` is better.

---

### Post by David_Ramsay on 2015-06-06
gksu nautilus works..  Thanks...  Must change bad habits...

Not the issue of why Remastersys stopped working Install Option - ages ago.
Would love to know the answer...  or is it that simple... gksu

Remastesys is rebranded and pay for - and hope GNU licence enforces
pay licence when coder goes for the money.

---

### Post by David_Ramsay on 2015-06-17
Not solved - reboot - when worked == and does not work.  you have to pay for linux
version of DOS ghost.. Though had it solved :(

---

### Post by sudodus on 2015-06-18
I know this happened with Remastersys. But there are alternatives, if you do not want to pay for Remastersys. ***Are you prepared to try an alternative? ***There will be more work, and it is hard to know how much more work ...

You mentioned Ghost. It is a tool for ***cloning***. If cloning is what you want, there are several methods and tools. I would suggest that you use ***Clonezilla***.

If you want to make an own iso file for installing in other computers, things will be a little more complicated, but there are still alternatives to try.

---

### Post by David_Ramsay on 2015-06-18
Remastersys is the norton ghost but for is for linux.

The bootable dvdr, or usb stick is essensual.

Remastersys stopped working again after a few ubuntu updates, then suddenly works again
after re-installing a previously installed libcuda1 update.

What libcuda has to do with Remastersys is a little confusing.. But works..

maybe just default to ubuntu default gfx driver b4 backing up?

---

### Post by sudodus on 2015-06-18
Yes, if you want better portability, you should use the free and automatic drivers (and avoid proprietary drivers).

---

### Post by David_Ramsay on 2015-07-13
sudodus said: Clonezilla.

Thanks, I am now all clonezilla and read  the thread:-

linux.com/learn/tutorials/783416-how-to-image-and-clone-hard-drives-with-clonezilla

The tuxboot live creator and the linux clonezilla boot image

Works Perfectly bootable  USB or Optical media.

A little more complex than norton ghost, mount points and keyboard maps but mostly
just skip those as default options.

The app is chocka block instructions whilst doing it - code instructions and warnings..
^^^

Love - uses all cpu cores when compress the partition or disk image.

Also backs up NTFS windows, smaller and faster than norton ghost.

Loves my usb stick boots clonezilla :)

note: 

Windows, I still have to delete hiberfil.sys and pagefile.sys via linux b4 I start a 
windows ntfs backup.  I never knew clonezilla could also backup windows.

---

### Post by sudodus on 2015-07-13
Congratulations :KS

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

### Post by David_Ramsay on 2015-07-13
Using Firefox - cannot find "Thread Tools at the top of the page" it is solved.

---

### Post by sudodus on 2015-07-13
> **David_Ramsay said:**
> Using Firefox - cannot find "Thread Tools at the top of the page" it is solved.

See the attached screenshot :-)

---

### Post by David_Ramsay on 2015-10-08
months - weeks later - the icon solved == not on the page - but on the list -duh

learned gksudo instead of sudo ;)

---

