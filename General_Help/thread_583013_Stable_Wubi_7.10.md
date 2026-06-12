---
title: "Stable Wubi 7.10"
date: 2007-10-20
forum: General Help
---

### Post by rohedin on 2007-10-20
:) Hi it's me again. Just a quick question, how long do you think it will be untill Wubi 7.10 is stable? (or as stable as 7.04 anyway) Because if it's going to be relatively soon I'm going to wait until then rather than install Wubi just yet.

Thanks.

---

### Post by billy99 on 2007-10-21
i dont know why no one ansered your question..i wanted to know the exact same thing.

im new to linux and ubuntu..and was excited to find wubi.

i wanted to try ubuntu 7.10 but if the wubi 7.10 will take a few months to be realesed in a stable version maybe i should just try ubuntu 7.04.

can anyone estimate when a stable wubi 7.10 will be free to download from the wubi site?


in any case..thanks to those who help..great work.

---

### Post by HampusW on 2007-10-22
A beta version of Wubi 7.10 will probably be released within a few weeks, but it will take some time for a more stable version to be finished. We still don't know how long it will take, because it depends on how many bugs are found in the beta... Don't expect it to be released any soon, though.

So for the moment I recommend you to try 7.04, if you want a stable version.

---

### Post by ago on 2007-10-22
As Hampus said, it will take anywhere from a few days to a few weeks.

We first need to have a feature-complete alpha (that should be a matter of a couple of days).

Then sort out most of the bugs reported (not sure how long that will take, it can be a couple of days, it can be weeks, depends on the bugs that come out).

Then we have our first beta. After that we might have a second beta (what you might define stable). Then we will have a final.



Of course the better and more accurately you guys can report bugs, the quicker the process...

---

### Post by billy99 on 2007-10-22
thanks guys!..for the ansers..now i got it clear.

i think ill try wubi 7.04 with ubuntu 7.04, hopfully ill love it and and than install the 7.10 when its good and ready.

---

### Post by ago on 2007-10-22
That said, the worst it should happen with 7.10 is that the installation fails and then you can uninstall. Having feedback on 7.10, is very important to speed up its release!

---

### Post by rohedin on 2007-10-22
Ok thanks for replying. Anyway I'll install 7.04, once I'm used to it I might give 7.10 a try.

---

### Post by greggus on 2007-10-22
OK, and what about install Ubuntu 7.04 by Wubi and then update it to 7.10 in normal way? (apt-get dist-upgrade)
(I can't check if it works, because I don't have Windows at all.)

---

### Post by ago on 2007-10-22
> **greggus said:**
> OK, and what about install Ubuntu 7.04 by Wubi and then update it to 7.10 in normal way? (apt-get dist-upgrade)
(I can't check if it works, because I don't have Windows at all.)

If anything that will come after... I will post some upgrade script. Essentially it requires:

1. Uninstalling lupin-target
2. Running the Ubuntu upgrade wizard
3. Instally lupin-support (NO LINK YET!!!)
4. Replacing wubildr and wubildr.mbr with custom versions (NO LINK YET!!!).

---

### Post by dndzz on 2007-10-26
I used "Wubi-7.10-alpha-rev368.exe" yesterday and it worked perfectly for me. It even detected I had an AMD 64 system and downloaded and installed the correct Ubuntu 7.10 version!
IMHO, this version is at least a Beta!

---

### Post by ReneD2602 on 2007-10-28
Hello,

I also tried the Wubi-7.10-alpha-rev368.exe Version and had some problems at Installation time.
Ubuntu told me, that there ist no SWAP Partition defined.

The second Problem ist, Wubi took the AMD64 Version, but I want to have the 32Bit Version. 
Where can I select the Version I want to use?


Regards

René

---

### Post by ago on 2007-10-28
Use rev 377 to fix swap issues.
Use "--32bit" to force 32 bit installation on 64 bit systems

---

### Post by ReneD2602 on 2007-10-28
Thank you for the quick answer.

this means I have to start the wubi Program at the command line and add --32bit to it?
Is this correct?

I have some wishes to wubi:

Please put in an Expert Button for a selection of the size for the three disks separately and also a Selection for 32Bit or 64Bit.
There are still some Programs that are not available for 64Bit, so I'm still using 32Bit every time.


Thank you

René

---

### Post by jrharvey on 2007-11-02
> **ReneD2602 said:**
> Thank you for the quick answer.

this means I have to start the wubi Program at the command line and add --32bit to it?
Is this correct?

I have some wishes to wubi:

Please put in an Expert Button for a selection of the size for the three disks separately and also a Selection for 32Bit or 64Bit.
There are still some Programs that are not available for 64Bit, so I'm still using 32Bit every time.


Thank you

René

In 7.10 I havnt run in to ANY programs not usable by 64bit ubuntu. Gutsy should be able to run any 32 bit program

---

### Post by hums07 on 2007-11-04
> **greggus said:**
> OK, and what about install Ubuntu 7.04 by Wubi and then update it to 7.10 in normal way? (apt-get dist-upgrade)
(I can't check if it works, because I don't have Windows at all.)

I tried upgrading Wubi Xubuntu 7.04 to Xubuntu 7.10. Everything went well and working except now there is an error with HAL, so I cannot access other partition of harddisk and external drives. But as far as I know HAL error is not Wubi problem (?).

---

### Post by jaezcurra on 2007-11-04
> **hums07 said:**
> I tried upgrading Wubi Xubuntu 7.04 to Xubuntu 7.10. Everything went well and working except now there is an error with HAL, so I cannot access other partition of harddisk and external drives. But as far as I know HAL error is not Wubi problem (?).

Maybe a look at: [http://ubuntuforums.org/showthread.php?t=580951](http://ubuntuforums.org/showthread.php?t=580951) could be helpful.

---

### Post by Wesley on 2007-11-08
hi

downloading the wubi xubuntu 7.04 now, looks very interesting

but got a question, i'm a little confused why many people having problem with upgrading 7.04 to 7.10. i understand wubi use virtual disk within XP partition. VMWare, virtual PC and virtualbox also use 1 virtual disk per an OS and works fine when upgrading ubuntu to latest version. 

so the question is why wubi couldnt do that?

thanks

---

### Post by ago on 2007-11-08
Because wubi is not a VM...

---

### Post by Wesley on 2007-11-08
lol very good answer ;)

just installed xubuntu 7.04, no driver for netgear wireless cardbus so no internet, the wireless worked with 7.10 LIVE CD. 

so i guess i'll have to wait for 7.10 stable version

i like your project a lot :)

thanks

---

