---
title: "Trouble with tar - &quot;input/output&quot; error"
date: 2007-05-06
forum: General Help
---

### Post by ytene on 2007-05-06
I'd really appreciate any help that can be offered with this little gem...

Ubuntu 6.10/AMD64 on Tyan Thunder K8W with an Adaptec Ultra160 PCI SCSI Card and a Freecom (HP) DAT72 Tape Deck. Hardware ID of the deck is /dev/st0

If I attempt a backup using, for example, the syntax

tar cvfz /dev/st0 /home/ytene/data

I am rewarded with a spooling tape drive and a scrolling display of files being written to the tape. So far so good. However, if I try and catalog the tape - or restore from it, using the syntax

tar tvf /dev/st0

all that I get for my trouble is the following error message :

root@voyager:/home/ytene# tar tvf /dev/st0 ./sylpheed_Mail
tar: /dev/st0: Cannot read: Input/output error
tar: At beginning of tape, quitting now
tar: Error is not recoverable: exiting now
root@voyager:/home/ytene#     

I did some basic trawling around and came upon the following reference:-

[http://lists.freebsd.org/pipermail/freebsd-bugs/2006-December/021514.html](http://lists.freebsd.org/pipermail/freebsd-bugs/2006-December/021514.html)

[forgive the fact that this is a bsd site and not specifically linux related - I think the tools are largely common] and I tried to follow the suggestions given there, but without success. These failures seem to be 100% consistent and repeatable. I have tried to erase the tape back to "new" state, by using 

mt -f /dev/st0 erase

which, for 72Gb tapes, takes an age! However, this makes no difference. I have tried brand new tapes, with the same results. As a final check, I have rebooted this machine into WindowsXP and tried to use NTBackup to prove the tape hardware. This works perfectly. I am therefore pretty confident that my hardware and tape media are all OK. 

What's really puzzling/frustrating to me is that I am *sure* I've had this working before. Maybe not on 6.10, but almost certainly on 6.04 or 5.10.  Obviously slightly concerned as my ubuntu machine is where I do all my serious work... so would like to have a reliably working backup solution. 

I'd really appreciate any tests or steps I can take to diagnose and preferably fix this problem...

Thanks in Advance...

---

### Post by rai4shu2 on 2007-05-06
"tar tvf"? Should that work with a tape? I thought you would use "tar xvf".

---

### Post by ytene on 2007-05-06
Yes, the -tvf option does work. When used with a tape, -t just gives a catalog, i.e. it tells you what is on the tape without attempting to perform any actions [such as restore] with the contents.

It should work...

-xvf - as you rightly suggest, is used to eXpand the archive - restore it - as required. I've also tried all combinations of including and excluding the z option, which parses files through the zip archive tool. This makes no difference either way.

---

### Post by rai4shu2 on 2007-05-06
Sounds like a kernel issue, although that would just be a guess.

---

### Post by ytene on 2007-05-07
OK, if it's safe to assume that this isn't a problem with the GNU tools, then can you suggest how to diagnose further?


I have another ubuntu build for my machine [ I use HDD caddy cases to swap bootable discs] and tried to execute a tar tvf with Dapper Drake, but got the same results.


If this is a kernel problem, then it seems to impact at least the last 2 releases I have tried. Were I confident of my memory, I'd add that I believe the last time I had to perform a restore in anger I was using Breezy Badger. For a variety of reasons I'd deployed the i386 binaries for Breezy [couldn't get the AMD64 version to install properly]. I'm now wondering if there is any value in downloading and trying the i386 ISO for Feisty, just to see if this makes any difference.

Any thoughts?

If we go on the premise that this is kernel-related, then can you suggest where I should look to see if I can locate and diagnose the problem please? 

Thanks in advance!

---

