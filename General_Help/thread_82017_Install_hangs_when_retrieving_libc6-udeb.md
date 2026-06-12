---
title: "Install hangs when retrieving libc6-udeb"
date: 2005-10-25
forum: General Help
---

### Post by ApexWebSolutions on 2005-10-25
This is for Breezy Badger 5.10, Kubuntu-Live.

The checksum of the download is perfect: 83ab6f648ce431d26c08321d1f95457a

This disk is fine, and the error is occurring at the same place as others, so that's not it.  From Windows I can explore the disk, and it autostarts and the program intros run.  From Kubuntu, when I boot from the disk, it hangs at 20% Retrieving libc6-udeb.

Others had the [same problem with 5.04 Hoary Hedgehog]("http://ubuntuforums.org/showthread.php?t=73412"), and with non-Live version.  Lowering burn speed did not help them.  Similar with [this thread]("http://www.ubuntuforums.org/showthread.php?t=71401").  They did not have any resolution for this hangup.

Burning CD with DeepBurner & Pacific Digital USB2 24x10x40 drive.

Booting from Targus PADVD010 (since P.Digital drive won't boot on Toshiba Portege M200).  The Targus uses a [TEAC DV-28E]("http://www.teac.com/DSPD/pdf/MostRecent8_25_2003/DV-28E-0201.pdf") drive with [Genesys Logic GL811E]("http://www.genesyslogic.com/econtents/product02.asp?minicidx=2&lastcidx=3&SN=34") controller and chipset.

24x speed is within capabilities of both drives and the 40x CD-R.

All the usual suspects appear to be clean, so I'm down to Kubuntu/Ubuntu incompatibility with hardware.

Hard drive is P-ATA6, not SATA.  So that's not it.

The problem afflicts other releases of Kubuntu, and both Live and regular versions.  It's not a CD or burn problem.  It hangs at the same place for users with certain types of hardware, both SATA and non-SATA.

Reluctantly, I'm heading back to distrowatch to pick from MEPIS and Mandriva, or maybe SUSE.  I'll also fill out a bugzilla report.

TIA for all help.

---

### Post by RasRedox on 2005-10-26
Don't get too excited....I have the identical problem.  
I've tried different sources, burning on different machines and I've produced several different CDs that ALL boot fine on 3 other machines, just not the one I need KU 5.10 on.
They ALL hang at the same spot as yours (libc6-udeb, 20% of task) on my target machine- dumping me to a text-based menu.

My target machine is a Dell 9100 dual core 2.6 Ghz, a couple of months old.  No other CD has given me problems and when I do the "CD integrity check", the install program says everything's fine.
Is your Cd reader a "DVD/CD" drive?  Otherwise, we seem to have pretty different hardware.

I posted here earlier, have gotten ca 50 visits, no replies yet.  I'll let you know what/if I find anything out .

RasRedox

---

### Post by RasRedox on 2005-10-29
Well, I just tried U 5.10 live i386 (not the KU) from a different site, burned with a different computer and had the same result at the same place.

Sigh

It let me get into a shell (whoopee...) 
I was interested if there were some reorganized files on a Ubuntu disk vs a Kubuntu and maybe getting a different interruption point.  nope.

I'll keep trying and let you know if anything happens.

RasRedox

---

### Post by meowmeow on 2005-12-10
I have had the identical problem: The live and installation cd hangs on retrieving libc6-udeb.
Well I could sove the problem with the cdrom drive from the old computer. In my case it seems to be connected to the new dell dvd writer drive

Meow

---

### Post by skipgolf530 on 2005-12-19
I have tried to re-create the kubuntu live 5.10 disk three times. I have downloaded from three different sites, I think the last one I tried was from England, I am in Ohio. They all fail from or at the same place. I am downloading from with a wireless modem on a p4, I have used K3b and Gnome burner to make multiple copies, they all fail. I have tried to load from an 8 speed, a 24 speed and a usb dvd-cd rom. They all fail. However I did download to the machine I am trying to make a live kubuntu and instead downloaded ubuntu it loads fine. I haven't tried to download to the other machine and creating the disk there. Has anyone tried using that other operating system to create the CD?

---

### Post by littleears on 2006-01-09
I'm having the same problem. 

System is a Shuttle SS51G (probably v1.0), with SIS chipset (SiS651).
Sony DRU-810A DVD drive.

I've tried:
(all in the last couple of weeks)
Kubuntu live CD (probably 5.10)
Kubuntu install CD (probably 5.10)
Ubuntu install CD (probably 5.10)

I tried multiple versions of both CDs, at least one of which was *written* on another CD burner. 

The DVD is new and seems to work fine in windows. I've updated the DVD's bios to the latest.

The PC is old and has happily run windows for a few years.

I've never installed linux on this pc before, but I have installed debian on other machines many times. 

Any suggestions?

---

### Post by littleears on 2006-01-09
Yea!
After my last post I did some more searching and learned that the sony dru-810a has the same chipset as Benq DW1640 and Plextor px-740a (Philips Nexperia chipset with the PNX7860E recording engine and TZA1047HL analog pre-processor, according to [http://www.anandtech.com/printarticle.aspx?i=2581)](http://www.anandtech.com/printarticle.aspx?i=2581)).

Also there is a bug that discusses this: 
[https://bugzilla.ubuntu.com/show_bug.cgi?id=16901](https://bugzilla.ubuntu.com/show_bug.cgi?id=16901)

This bug report helped me and I'm glad to say I am posting this from a system running the kubunto live cd!

The trick was to type the following at the livecd boot prompt

[INDENT]live cdrom-detect/cdrom_hdparm=-d1[/INDENT]

Good luck everyone.

-littleears

---

### Post by lset on 2007-02-23
Hi,

Any suggestions on how to deal with this hanging problem during a Xubuntu Edgy Eft 6.1 install? At the beginning of install I use "F6 Other Options" to apend  cdrom-detect/cdrom_hdparm=-d1  to the boot options but this does not work.  I know this CD is valid as I have successfully used it for installs on other machines. Live is not an option as this is an install on a low memory (96MB) Toshiba Satellite Pro 490XCDT (~10 yrs old).

Thanks in advance

Lset

---

