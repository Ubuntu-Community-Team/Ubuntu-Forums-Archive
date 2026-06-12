---
title: "GRUBbing Windows ?"
date: 2007-07-07
forum: General Help
---

### Post by mhenriday on 2007-07-07
I'm running a triple boot (**Ubuntu 7.04**, **Windows XP Home**, **Vista Business**) set-up on an **AMD 64 X2 5000+** with two 250 GB harddisks, as follows :
[INDENT]Disk /dev/sda: 250,0 GB, 250059350016 byte
255 huvuden, 63 sektorer/spår, 30401 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte

    Enhet Start     Början        Slut     Block    Id  System
/dev/sda1   *           1       14744   118431148+   7  HPFS/NTFS
/dev/sda2           14745       29489   118439212+   7  HPFS/NTFS
/dev/sda3           29490       30401     7325640    c  W95 FAT32 (LBA)

Disk /dev/sdb: 250,0 GB, 250059350016 byte
255 huvuden, 63 sektorer/spår, 30401 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte

    Enhet Start     Början        Slut     Block    Id  System
/dev/sdb1   *           1       29650   238163593+  83  Linux
/dev/sdb2           29651       30401     6032407+   5  Utökad
/dev/sdb5           29651       30401     6032376   82  Linux växling / Solaris[/INDENT]
As might be expected, I experience frequent crashes with **Vista**, which require re-installation of the OS. This is, of course, annoying, but not a major problem - the re-installation process doesn't take much more than an hour and I keep no important data on that system, but use it instead for testing purposes (**Vista** sandbox ?). What I do find irritating, however, is that after a **Windows** re-installation, **GRUB** no longer boots when I start the computer, with the result that I only have access to my **Windows** disk (the computer is configured in such a way that **Windows** doesn't «see» my **Ubuntu** disk) ; thus, I am unable to access **Ubuntu**. In my ignorance, the only way I have hitherto found to deal with this problem is to also re-install **Feisty**, which means that **GRUB** automatically boots when I start the computer, giving me access to both the **Windows** and the **Ubuntu** disks....

I don't mind performing this operation once or twice, but as a permanent solution to the problem of **Windows** crashes, I find it distinctly lacking. How can I put a better solution in place ? Is it possible, for example, to install 64-bits **GRUB 2** from an ISO CD directly upon starting my computer after a **Windows** re-installation (I expect to have to do several of these in the future) and thus gain access to both my harddisks ? If so, how is this best done ? Any other suggestions ? Any concrete help fellow **Ubuntu** users can provide in this regard will be most welcome !...

Henri

---

### Post by geek_Man on 2007-07-07
Everytime you reinstall Vista, you should pop in the Ubuntu Live CD and in the termina run : ```
grub-install /dev/sdb
```Please verify this first, it's been a long while since I've dealt with this stuff. If you boot from your first HD, then change /dev/sdb to /dev/sda. Like I said, verfiy this...

---

### Post by mhenriday on 2007-07-07
Thanks a lot ***geek*_Man** ! I knew I was missing something simple and obvious - to those who knew about it ! But if I remember the train of events correctly, after re-installing **Windows**, inserting the 64-bit **Ubuntu Feisty** live CD, and re-booting my computer, I get a screen which allows me to choose whether to (re-)install **Feisty**, run the OS off the live CD, do a mem test, etc, etc, but I don't remember access to a terminal as being one of the alternatives presented there. Is that alternative indeed present, and my failure to recall it due to my never having used it before, or, if not, how and where in the installation process can I gain access to a terminal ? Again, I'm probably overlooking something obvious to the *cognoscenti*, but everything is easy if one knows how, and nothing if one doesn't....

Henri

---

### Post by geek_Man on 2007-07-07
You'll want to run the OS of the Live CD and run the terminal from there. HTH...

---

### Post by hooksie on 2007-07-07
> **mhenriday said:**
> Thanks a lot ***geek*_Man** ! I knew I was missing something simple and obvious - to those who knew about it ! But if I remember the train of events correctly, after re-installing **Windows**, inserting the 64-bit **Ubuntu Feisty** live CD, and re-booting my computer, I get a screen which allows me to choose whether to (re-)install **Feisty**, run the OS off the live CD, do a mem test, etc, etc, but I don't remember access to a terminal as being one of the alternatives presented there. Is that alternative indeed present, and my failure to recall it due to my never having used it before, or, if not, how and where in the installation process can I gain access to a terminal ? Again, I'm probably overlooking something obvious to the *cognoscenti*, but everything is easy if one knows how, and nothing if one doesn't....

Henri

You could do a full boot into Feisty from the Live CD, and just use the terminal in the OS.

Unless of course there is some direct terminal access from the CD that I don't know about.

Edit:Beaten by geek_Man

---

### Post by mhenriday on 2007-07-08
Thanks ***geek*_Man** and **hooksie** ! I doubt that I should have thought of gaining access to a terminal by booting from the live CD without your help ; this, again , is one of those procedures that seems obvious when familiar, but hard to guess when not - at least for unimaginative users like myself. I'll be sure to use it when the next occasion arises, as alas, it certainly will....

Henri

PS : I'm using the **GRUB 2beta** on my machine ; booting from a live CD terminal will, of course, alter GRUB back to the 0.97 version, will it not ? Compared with having to re-install **Feisty**, however, definitely a minor problem, susceptible to solution with a couple of mouse clicks....

---

### Post by mhenriday on 2007-07-30
The other day I saw a reply under the title **PCLinuxOS makes this task even easier** by a chap calling himself **johnson12** on a [*ZDNet thread*]("http://blogs.zdnet.com/hardware/?p=609") devoted to dual-booting **Vista** med **Linux** :> After you install vista, boot the live cd and issue "redo-mbr" as root and it will reset your bootloader, and add in vista as a grub, or lilo boot option.

Wonder when the buntu guys will add this wonderful feature?

This strikes me as well as a great option to add to **Gutsy** before it's released in October. Anything that facilitates dual-booting should be a plus for **Ubuntu**, and unless I miss my guess, adding it to the **Gutsy** build shouldn't be too complicated - any developer working on the release who might care to comment on this matter ?...

Henri

---

### Post by fjgaude on 2007-07-30
I'm no developer but I'm sure the Gusty team are working at all the improvements that people are requesting. As for me:

I'm just learning all the ends-and-outs of GRUB through the man pages for update-grub and grub-install. Amazing.

frank

---

