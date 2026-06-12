---
title: "Help! installing windows"
date: 2008-03-30
forum: General Help
---

### Post by fruni on 2008-03-30
Ok so, I am installing windows again and hears how i did it:

1. Deleted all my ubuntu partitions (Was reformatting them anyway so i decided to install them after windows)

2. could not delete the linux swap or w/e partitions because they were locked so i ignored them

3. inserted my restore disk  (Toshiba satellite 1900 series) 

4. Got a simple message saying no C: or something like that.

5. Got a couple errors in a row but i just hit ok and the restore disk fixed them.

6. rebooted

7. grub starts up and gives me error 17.... I thought i deleted grub when i got rid of linux?

EHh.. I am kinda confused lol.. What am i to do :(

EDIT: will post a screen shot of my partitions when in a sek

---

### Post by Fixman on 2008-03-30
You can't install windows with a restore CD, you need an install CD. If your computer came with windows pre-installed and you don't have a restore CD, you can call the OEM witch gave you the computer, or 
[Download it using BitTorrent]("http://thepiratebay.org/tor/4040101/Microsoft.Windows.Vista.Ultimate.x86.Integrated.February.2008.OE") (**THAT IS LEGAL because you bought a copy of windows**).

---

### Post by fruni on 2008-03-30
[IMG]http://img267.imageshack.us/my.php?image=screenshotfm6.png[/IMG]

[http://img267.imageshack.us/my.php?image=screenshotfm6.png](http://img267.imageshack.us/my.php?image=screenshotfm6.png)

I am pretty sure that SDA1 is my windows install but i cant access it lol

and to the post above im pretty sure it has installed windows because what else would the 1.52 gigs be? and that is a live cd btw.

And I guess I will just torrent it if worse comes to worse. Thanks :)

---

### Post by Fixman on 2008-03-30
If you have a windows install CD you don't need to torrent, just re-install it.

---

### Post by fruni on 2008-03-30
I dont have a windows install sadly :( but .. still what would it have installed thats 1.52 gigs? could it possibly be the windows i use to have on here?

---

### Post by Fixman on 2008-03-30
> **fruni said:**
> I dont have a windows install sadly :( but .. still what would it have installed thats 1.52 gigs? could it possibly be the windows i use to have on here?



Its not windows, its just a "recovery partition", with probably a prelude and some trash data. Althrought I'm really surprised its that big, Id expect 1/2GB. However, if it boots on GRUB then its not windows.

---

### Post by fruni on 2008-03-30
It does not boot on grub because when it starts up grub gives me error 17.

---

### Post by forrestcupp on 2008-03-30
First of all, you didn't uninstall GRUB, grub is on the MBR and deleting Linux doesn't delete that.  You just deleted all of the settings for grub, so that's why it doesn't work.

You can't install Windows because of what it says, there's no C:.  It's because you don't have an NTFS partition to install it on.  Download [the GParted LiveCD](http://gparted-livecd.tuxfamily.org/) and boot to the CD to delete all of your partitions and create a new NTFS partition with all of your space.  Then you will be able to install Windows.  

And hopefully when you install Windows, that will take care of your grub problem.  If not, download [Super Grub](http://supergrub.forjamari.linex.org/), boot to that CD, and choose the option to restore the Windows boot loader.

---

### Post by fruni on 2008-03-30
Thanks forestcupp, but as you can see in my screen shot the windows disk made its own NTFS partition (That was what one of the errors that got fixed were). And I will try the super grub thing.

---

### Post by fruni on 2008-03-30
ermmm what do i do in super grub??

Super Grub Disk (WITH HELP)
Super Grub Disk (NO HELP)
GRUB => MBR & !LINUX! (1)                AUTO    ;-)
GRUB => MBR & !LINUX! (>=2)       MANUAL   |8-)
!LINUX! (1)          AUTO
!LINUX!  (>=2)  MANUAL
!WIN!                                                                    :(((
WIN =>MBR & !WIN!        :((((((((((((((((((((((((((((((
EASY LIVE SWAP

those are my options lol

EDIT: I hit win and got to the windows set up :D its done setting up now to reboot and see if it worked :)

Well windows set up fine im pretty sure but grub is still going up on bootup with erro 17..


EDIT2: I can boot windows straight from super grub :D But... I do not think my mom who owns this laptop will be happy when she needs to get it back...

---

### Post by fruni on 2008-03-30
Bump

---

### Post by forrestcupp on 2008-03-31
If you can't figure out where to go in Super Grub, try [this solution](http://ubuntuforums.org/showthread.php?t=622828) using your Ubuntu LiveCD.

---

### Post by adrian15 on 2008-03-31
> **fruni said:**
> ermmm what do i do in super grub??

Super Grub Disk (WITH HELP)
Super Grub Disk (NO HELP)
GRUB => MBR & !LINUX! (1)                AUTO    ;-)
GRUB => MBR & !LINUX! (>=2)       MANUAL   |8-)
!LINUX! (1)          AUTO
!LINUX!  (>=2)  MANUAL
!WIN!                                                                    :(((
WIN =>MBR & !WIN!        :((((((((((((((((((((((((((((((
EASY LIVE SWAP

those are my options lol

EDIT: I hit win and got to the windows set up :D its done setting up now to reboot and see if it worked :)

Well windows set up fine im pretty sure but grub is still going up on bootup with erro 17..


EDIT2: I can boot windows straight from super grub :D But... I do not think my mom who owns this laptop will be happy when she needs to get it back...

Either you go to: 
**Super Grub Disk (WITH HELP)**
either you go to:
**WIN =>MBR & !WIN!        :((((((((((((((((((((((((((((((**
which will fix your windows boot directly.

I still ask myself if the quick menu was a good idea.

I think I am going to add an **??????????????**  option (with help) at the bottom and I will rename:
**Super Grub Disk (WITH HELP)**
to:
**Super Grub Disk (WITH HELP) RECOMENDED!!!**

adrian15

---

### Post by forrestcupp on 2008-03-31
> **adrian15 said:**
> Either you go to: 
**Super Grub Disk (WITH HELP)**
either you go to:
**WIN =>MBR & !WIN!        :((((((((((((((((((((((((((((((**
which will fix your windows boot directly.

I still ask myself if the quick menu was a good idea.

I think I am going to add an **??????????????**  option (with help) at the bottom and I will rename:
**Super Grub Disk (WITH HELP)**
to:
**Super Grub Disk (WITH HELP) RECOMENDED!!!**

adrian15

Is Super Grub your project?  It's a great product.  It worked for me when I needed to restore my Windows boot loader when nothing else did.

---

### Post by adrian15 on 2008-03-31
> **forrestcupp said:**
> Is Super Grub your project?  It's a great product.  It worked for me when I needed to restore my Windows boot loader when nothing else did.

SGD is not a product is a project.

It is interesting to see how sometimes Windows' FIXMBR and FIXBOOT are not useful just because they do not activate partitions (or maybe another reasons).

If you like SGD... do not hesitate to make a little donation (see my signature) ;). 

adrian15

---

