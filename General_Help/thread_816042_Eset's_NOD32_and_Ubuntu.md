---
title: "Eset's NOD32 and Ubuntu"
date: 2008-06-02
forum: General Help
---

### Post by wislon32 on 2008-06-02
I use Ubuntu as my IMAP server, which then feeds out to several Windows workstations.  I use NOD32 from Eset as my antivirus software on the windows machines, but would like to use it within Ubuntu to do primary screening.  I've managed to download and install the Linux version onto the Ubuntu workstation (Eset's instructions are not totally correct) and as far as I can tell it's running in the background, though whether it is updating automatically I can't tell. I'm relatively new at Linux / Ubuntu, so don't always know where to look for help or the right command.

_**Question** (since Eset have gone very quiet)_.  I can't find any GUI to help with configuration. Is there one? And has anyone else experience of working with NOD32 on Ubuntu who can give me tips as to what to do, how to configure it etc.?

---

### Post by foresthus on 2008-10-10
Hi,

if someone has an idea I'll be glad to hear someting about this.

thnx

---

### Post by wislon32 on 2008-10-10
Eset tell me there is a web front end.  However, I've never managed to work out where it is, if it is installed, or whether it works.  And the series of hoops I had to go through to install NOD32 was horrific.  In fact, I gave up.  I still don't know whether NOD32 is working or not.

I come from a Windows environment and I find it very frustrating to install applications in Ubuntu / Linux, where all you get is a set of incomprehensible console commands.  If Windows can simplify the process, why can't developers do it for Linux?  Synaptic isn't bad, but not all apps use it.

---

### Post by unclecameron on 2010-01-18
there is an upcoming Desktop Linux release with a GUI installer, you might find that easier.

Are you using some sort of mail server software on your Ubuntu box, like Postfix, Exim, etc? NOD32 can hook into those servers, but working with a Linux mail server, with or without an AV scanner, isn't simple to figure out for someone new to Linux, or even those have been working with Linux for awhile.

---

### Post by n0dix on 2010-01-18
See this thread: [http://ubuntuforums.org/showthread.php?t=494913]("http://ubuntuforums.org/showthread.php?t=494913")

---

### Post by wislon32 on 2010-01-19
Thanks. I'm never sure whether I ever actually got NOD32 working. 

I've actually given up using Ubuntu for reasons related to the installation of NOD32.  Why does everything have to be so complicated, when I'm told Ubuntu (and Linux) is so flexible?  

And the thread mentioned above illustrates exctly why I left Ubuntu.  
     Not only must I use the command line, but even the examples are wrong.  And 
     To compound it, there is a higher proportion (than Windows) of users who think it is clever to denigrate new users who are having difficulty

Hopefully in the future, if I try again I'll be able to use a dekstop version - as there should have been 2 years ago.

---

### Post by n0dix on 2010-01-19
> **wislon32 said:**
> 

I've actually given up using Ubuntu for reasons related to the installation of NOD32.  Why does everything have to be so complicated, when I'm told Ubuntu (and Linux) is so flexible?  

You don't need and antivirus in Ubuntu, and in general any Linux distro.
> **wislon32 said:**
> 
     To compound it, there is a higher proportion (than Windows) of users who think it is clever to denigrate new users who are having difficulty

This is not true. :lolflag:

---

### Post by lamrod on 2010-04-07
Eset are now running a BETA of their desktop nod32 av product. see [http://beta.eset.com/linux](http://beta.eset.com/linux) for more details.

---

### Post by Kitkin15 on 2011-06-09
> **n0dix said:**
> You don't need and antivirus in Ubuntu, and in general any Linux distro.

This is not true. :lolflag:
Did you really just say that? Of course you need an Anti Virus when running ANY system, it dont matter if its Windows, Linux, or Unix. All though Virus's are rare in Linux and Unix they are still there. Always remember, if a program can be written for an Operating System, Then a Virus can be written for that same Operating System. 

People kept saying that Macs (Unix) Was secure and could not get a virus (I heard this from "Security Pros") I dis-agreed with them. Now here we are, with all these infected Macs, people didnt listen.

Eset is what you should get, im going to get it, it might be hard to install but Eset's webpage should have instructions on it. 

The beauty of Linux is the ability to do whatever you want, and this is made possible through the Terminal. Truthfully once you get the hang of BASH everything becomes easier then it was on Windows.

---

### Post by linuxinstalledfromhdd on 2011-06-09
> **Kitkin15 said:**
> Did you really just say that? Of course you need an Anti Virus when running ANY system, it dont matter if its Windows, Linux, or Unix. All though Virus's are rare in Linux and Unix they are still there. Always remember, if a program can be written for an Operating System, Then a Virus can be written for that same Operating System. 

People kept saying that Macs (Unix) Was secure and could not get a virus (I heard this from "Security Pros") I dis-agreed with them. Now here we are, with all these infected Macs, people didnt listen.

Eset is what you should get, im going to get it, it might be hard to install but Eset's webpage should have instructions on it. 

The beauty of Linux is the ability to do whatever you want, and this is made possible through the Terminal. Truthfully once you get the hang of BASH everything becomes easier then it was on Windows.

Just use Bitdefender for now until NOD32 releases a viable Deb installation.
  
Bitdefender installation directions are about 1/4 the way down this guide:

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

It is identical, since I have used both. Actually I would say Bitdefender is better, has the exact same GUI and management capabilities, because it's free and it has larger automatically updatable definition lists to draw from.  IMHO

Nod32 was great years and years and years ago.. If you only used NOD32 with Windows, that would completely explain why someone would switch to Linux eventually.  Just research a recent review Bitdefender verses Nod32.

---

### Post by K1773R on 2011-09-18
congratulations, you got a useless AV now... :popcorn:

---

