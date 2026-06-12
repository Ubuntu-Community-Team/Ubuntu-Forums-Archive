---
title: "Rescan SCSI Bus and Wipe 56 Drives on Gutsy"
date: 2008-02-19
forum: General Help
---

### Post by JohnnyXmas on 2008-02-19
Hello!

I wasn't sure if this should be under server or general, so I posted in both.

I just built something interesting, and need some tips on getting it to do what I need it to:

I have 4 Compaq StorageWorks SCSI Arrays connected to a Compaq Proliant DL580 G2 server using SymBIOS Logic 22910 Ultra2 LVD HBA's. Each array can hold and address up to 14 drives. The server is running a Win2K AS \ Ubuntu Gutsy Dual-Boot.

the purpose of this setup is to provide fast mass drive testing and erasure. I need to be able to load it up with drives, test them for SMART failures and bad sectors, then perform a one-pass erasure.

Can you guys provide me with a walkthrough on how to perform these tasks with this equipment?

I have been using Ubuntu for a few years now as a Desktop \ Laptop OS, so I am very familiar with it, along with the locations and functions of the major configuration files and such. I have just never had to deal with this particular situation (of course), so a lengthy step-by-step is not necessary, just a general rundown of the quickest way to perform these tasks.

I'm WELL aware of SMART not really being that great, but we're contractually obligated to do it by our client, and far be it from me to turn away easy money. What I do need, is instructions on how to rescan the SCSI busses each time I swap drives out, so I don't have to constantly reboot the machine. Furthermore, I need a quick way to tell it to wipe all the drives on said busses (except for the primary one, which holds the OS), without having to fdisk and mount every single one, every single time. Right now I'm doing it under Solaris 10 on a Sun V480, whose "format" command at least provides a menu system, but it's still REALLY tedious.

This is going to be a permanent situation, with hundreds of drives per month going through it, so you can imagine how insanely tedious it would be to do that manually.


Thanks!!

---

### Post by jaton on 2008-06-13
You need to install the application:
# apt-get install scsitools

The you can run it:
# rescan-scsi-bu.sh

You need to run the commands as root or though the sudo command.

---

### Post by JohnnyXmas on 2008-06-17
Yeah, that didn't work so good. As in, it didn't work at all. It would go through the motions, but never recognize any changes. I ended up just writing a bash script using sg3utils and have it just remove every drive from every SCSI bus and ID, and then re-check each one individually. Takes at most 15 seconds, and works like a charm.

I also use the sg_format tool, and a similar bash script. Everything is going swell.

---

