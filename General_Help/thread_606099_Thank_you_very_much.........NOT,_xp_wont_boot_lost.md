---
title: "Thank you very much.........NOT, xp wont boot lost all info"
date: 2007-11-07
forum: General Help
---

### Post by gutted on 2007-11-07
messed up with wiping the ubunto partition
now wont boot to xp menu (had xp and vista)
tried fixboot copying ntldr etc
nothing

i need this back up and running asap


im trying to reinstall this linux ***** again to see if it will sort out the boot sectors
any ideas?

---

### Post by floke on 2007-11-07
I have plenty of ideas.
Perhaps if you apologise for your rudeness and calm down then someone might help you.

---

### Post by tombott on 2007-11-07
Reinstall Ubuntu, this should detect XP and add a boot record in Grub.
Alternatively you could run a XP repair from XP cd.

Don't blame Linux if you delete a partition and Windows won't boot!

---

### Post by gutted on 2007-11-07
all these years with computers in our lives they are still rubbish

tried xp resotre

running ubunto now, reinstalled it, chose my second hd (different make) and guess what

it looks like its installed on the first hd

might reinstall xp on the second hd and run a file recovery prog, thats if it recognises the hd !!!

this is not good, i'm on **** street ere guys

help!!!!

---

### Post by Dixon Bainbridge on 2007-11-07
I'm always amazed that people still don't back up any important data externally. If you lost all your data due to dual booting experiments/stupidity (delete as applicable) then tough luck. 


Backup
Backup
Backup

Lesson learned. You won't do that again will you? Sorry for the sarcastic tone, but based on your mannerisms in asking for help, you deserve it.

---

### Post by tombott on 2007-11-07
Sorry to hear your having problems, but computers will only do what we tell them to do.

You should never install / play with partitions on systems that have critical data, end of.

If as you say your windows partition has been over written with Ubuntu then I am sorry for you, but Ubuntu always gives me the option to resize any detected NTFS or Ex3 partitions when installing.

---

### Post by Colro on 2007-11-07
> all these years with computers in our lives they are still rubbish

A computer can only be as intelligent as the person sitting in front of it.

---

### Post by bigken on 2007-11-07
> **Dixon Bainbridge said:**
> I'm always amazed that people still don't back up any important data externally. If you lost all your data due to dual booting experiments/stupidity (delete as applicable) then tough luck. 


Backup
Backup
Backup

Lesson learned. You won't do that again will you? Sorry for the sarcastic tone, but based on your mannerisms in asking for help, you deserve it.


totally agree blaming the os when its human error lack of experience and common sense  
before you do any more damage remove the hdd and put into another pc see what windows can see

---

### Post by gutted on 2007-11-07
i agree with the backup

but you can't do a backup on every bootup

i erased the ubunto partition and the menu just wouldnt allow me to do anything so I dont think i'm to blame 100% ere guys i still had another HD with XP on and another partition with the ubunto partition

sh!t happens i suppose

---

### Post by gutted on 2007-11-07
if anything then i'm blaming these boot menus
if i had deleted vista of the 2nd HD then i would still have been able to boot XP or ubunto
i deleted ubunto - now i cannot load xp or vista

my error yes but if i had mistakenly deleted vista i would still have had xp

---

### Post by Maestro23 on 2007-11-07
> **gutted said:**
> if anything then i'm blaming these boot menus
if i had deleted vista of the 2nd HD then i would still have been able to boot XP or ubunto
i deleted ubunto - now i cannot load xp or vista

my error yes but if i had mistakenly deleted vista i would still have had xp

Do you have your Vista/XP discs?  Or did your system come OEM and you failed to make those Recovery/Restore discs.

---

### Post by tombott on 2007-11-07
By deleting Ubuntu you deleted GRUB which gives you the option of multi booting.

Reinstalling Ubuntu should have fixed this for you.

---

### Post by gutted on 2007-11-07
do have both xp and vista discs

tried fixboot etc with xp disc
tried with the vista disc

but with the reinstall if ubunto i did choose the 2HD but appears to have installed on the 1st HD

Grub tried to load but as it does when i leave a memory card in it came up as failed (or something, i then remove the memory card and reboot)

---

### Post by edwardTheGreat on 2007-11-07
> **gutted said:**
> if anything then i'm blaming these boot menus
if i had deleted vista of the 2nd HD then i would still have been able to boot XP or ubunto
i deleted ubunto - now i cannot load xp or vista

my error yes but if i had mistakenly deleted vista i would still have had xp

The Problem seems to be the connector between your keyboard/mouse and your deskchair, there might be a screw loose in there... kidding. :)

Did you sort it out?
> **gutted said:**
> 
i erased the ubunto partition and the menu just wouldnt allow me to do anything


Erasing Partitions is a fairly destructive activity, I hope you know which partitions were XP/Ubuntu/Vista and only deleted the one you wanted. 
Did you manually set the partitions where Ubuntu (and/or grub) will be installed, or did you let the installer do it? 

What do you mean " the menu just wouldn't allow me to do anything"? when you select an option it does nothing? or does something and then stops?

> **tombott said:**
> 
Reinstall Ubuntu, this should detect XP and add a boot record in Grub.

This sounds like a feasible way to try and get it back to recognising XP and Vista, 
Were you using the Windows XP bootloader or the Windows Vista bootloader before you overwrote it with Grub when you installed Ubuntu?

---

### Post by TuxTwig on 2007-11-07
Boot from Live CD. Run Gparted. If you can still see your XP partition, delete your Linux partition. This is the easiest way to return to XP. In XP, reformat your hard drive and then reinstall Ubuntu. EDIT: Hmm, seems like you've already tried this, what do yuo mean by "it doesn't allow you to do anything"? Try Supergrub to fix your Windows Bootloader if that's what you mean. He should be using Windows Vista bootloader by default if he didn't do any tweaking when he installed Vista.

---

### Post by skoal on 2007-11-07
Gutted, no worries there brother.

First, post back the output from a terminal:
```
sudo fdisk -l
```

We'll getcha back to running all 3. No problemo.

\\//_

---

### Post by bruce89 on 2007-11-07
It would be nice if you learnt how to spell Ubuntu so you can insult it properly.

---

### Post by roastgarlic on 2007-11-07
XP and Vista boot in different ways. A third-party software is required if the 2 OS are to be booted off the same drive.

---

### Post by edwardTheGreat on 2007-11-07
> **roastgarlic said:**
> XP and Vista boot in different ways. A third-party software is required if the 2 OS are to be booted off the same drive.

I don't believe this to be true, I am sure you can boot Windows XP using the Windows Vista Bootloader.
The bcdedit command line tool can sort that out for you (admittedly it's not very easy to come to terms with but you can)

---

### Post by gutted on 2007-11-07
got vista back on using vista repair option again, worked this time
got my xp drive back as well but wont boot, at least i can get some info off there
I did (last week) back up emails etc so not so bad, just lost a few of this weeks emails (emails were saved on another HD partition!! not found that yet)

a good time to start again me thinks

cheers for any positive helpful replies

---

### Post by bruce89 on 2007-11-07
I am an idiot, feel free to misspell Ubuntu.

[QUOTE=Sef]Dear bruce89,

You have received an infraction at Ubuntu Forums.

Reason: Insulted Other Member(s)
-------
If someone misspells Ubuntu or any other word then just gently point it out instead of insulting them.
-------

This infraction is worth 1 point(s) and may result in restricted access until it expires.  Serious infractions will never expire.

Original Post:
[post]3727168[/post]
> It would be nice if you learnt how to spell Ubuntu so you can insult it properly.

All the best,
Ubuntu Forums[/QUOTE]

---

### Post by tombott on 2007-11-07
> **bruce89 said:**
> I am an idiot, feel free to misspell Ubuntu.


lol, you cannot be serious???

I'm sorry but if somebody gets a infraction for that it's a sad state of affairs

---

### Post by DaymItzJack on 2007-11-07
I've also had problems where I know I select the correct hard drive (I got two separate ones) and it still seems to mess up my XP/Vista. I eventually just disconnected my first hard drive and installed Ubuntu with only one hard drive plugged in, that seemed to work.

---

### Post by inversekinetix on 2007-11-08
if you only want to fix the XP mbr, run the xp disk, get to the repair console and use 'fixmbr' it will write a new MBR for your XP,  if you want to add other OS you can install WINGRUB to your windows drive then edit your windows boot.ini file.  If you are more comfortable with windows and use it more than other OSs I would recommend using wingrub, it will preserve your windows boot.

---

### Post by TheBigBentley on 2007-11-08
If you have problems with dual booting Linux and Windows then use Wubi. That way it wont touch your partitions and boots to virtual disk file.

---

### Post by Ultimadlamer on 2007-11-08
If your point, right now, is to temporarily boot XP so you can attempt to backup your data, other avenues may be available besides messing with the MBR.

Have you considered running a boot manager from CD?  In situations like these (and I do run into them plenty, I like to experiment...) I've had good luck with something called Smart Boot Manager.  It lets you boot from any partition on the drive, so far as I can tell, without having to write to the MBR at all.  Basically, it does the same thing as Grub, but as a one-shot not-so-Linux oriented way.

Smart Boot Manager (and a few other Boot Managers I haven't quite bothered to learn yet) are available as part of the Ultimate Boot CD.  Do a google search for it, you'll find it.  It's free, like Ubuntu is.  Burn it to a CD and run it.  Smart Boot Manager is in File system Utilities -> Boot Managers, after you start your computer up from it.

Try booting each of your partitions using it.  If XP won't load from there, then it's damaged.

When I first started trying to use Linux, I encountered a similar situation where I damaged my windows install as well.  However, since then Linux in general has appeared to make great strides, and Ubuntu in specific has been very easy for me to use.  Perhaps you should be angry at Microsoft for making operating systems that are so easy to break?  :)

---

### Post by amvella on 2007-12-04
this happened to me before.. nothing to wory..
just boot with xp cd
go to repair
go to command line
type in FIXMBR 

this will fix ur master boot record. thats all. hope it works for u.

---

