---
title: "ISO creation, do you know any?"
date: 2007-08-17
forum: General Help
---

### Post by gimpguy2000 on 2007-08-17
Hi all

 I simply want to know how to turn my backp.gz <or whatever, my ubuntu system backup into an ISO file. This is needed in case of recovery correct? If not, and I can burn it as is, i'll be happy :)

The file is 1.9 gig so it will be going to DVD. 

Thanks a bunch,

Paul

---

### Post by Amazona aestiva on 2007-08-17
Try this:;)
[http://www.getdeb.net/download.php?release=1020&fpos=0]("http://www.getdeb.net/download.php?release=1020&fpos=0")

---

### Post by gimpguy2000 on 2007-08-17
Hi thanks. I got a surprise, it says the same package is already installed but I can't find it. I assume it's in the bin or share so will have to take a look. :confused: 

Thanks

Also, if i'm right , it'll be a blue gear and it may lurk in other areas besides media?

---

### Post by gimpguy2000 on 2007-08-17
Ok, found it, all is well. iso master will only add or extract the tgz. It won't create an iso nor is there an option to create it. :(

Thanks

---

### Post by Amazona aestiva on 2007-08-17
It makes iso!

1.Image->New
2.add files
3.Image->Save as

What's the matter?

---

### Post by gimpguy2000 on 2007-08-17
Well, when I save it says, something like problem creating and blinks out of existence. I wonder if I do a complete uninstall and re-install, maybe the detected file was corrupt...I'll give it a whirl..

TX

Paul

---

### Post by gimpguy2000 on 2007-08-17
Ok, it still won't work so I used the DD if =/backup.tgz of=/dvdrom. yadda yadda and created the iso, which i'm now burning to disk. When I chose to write files it said not a valid dvd image but when I opened brasero, it's not having a problem. Should I be concerned? Or is that typical of the default burner? 

Thanks,

Paul

---

### Post by Amazona aestiva on 2007-08-17
Also try K3B for iso creating.
1. New CD/DVD
2. add files
3. Burn
4. Tick: Create only image,the text isn't exactly this(I use other language)

---

### Post by gimpguy2000 on 2007-08-17
Hey, thanks for all the help. I will check into that and then get to bed.....yawn...but hopefully tomorrow I can get this set up. But seriously thanks for the help and with any luck, i'll have my backup iso tomorrow. :)  


TC
Paul

---

### Post by gimpguy2000 on 2007-08-17
Well, so far failure. I cannot find a way to create an iso out of the tgz file. ISOmaster says it can't, Kb3 only burns image as do many...

So, with all the open source out there, is there a way to make an iso of my backup at all? :(

Thanks,

Paul

---

### Post by bonzodog on 2007-08-17
Have you tried using Growisofs on the command line?

That will run mkisofs (to create the ISO file), then burn it to DVD. I used growisofs to back up my home dir on to DVD from raw directories, rather than a tgz file, but I suspect it should work.

---

### Post by gimpguy2000 on 2007-08-17
> **bonzodog said:**
> Have you tried using Growisofs on the command line?

That will run mkisofs (to create the ISO file), then burn it to DVD. I used growisofs to back up my home dir on to DVD from raw directories, rather than a tgz file, but I suspect it should work.

Hi thanks. no I haven't tried it yet. I'll look up how to use the command and see how it goes :)

Thanks,

Paul

---

### Post by Amazona aestiva on 2007-08-17
New Data DVD
add files
press 1
tick 2
add save path 3
Create ISO 4

---

### Post by Amazona aestiva on 2007-08-17
Dear gipmguy2000!
You didn't understand me! I know that K3B _CAN_ write ISO to HDD.
Example: K3B saved DVD ISO image as /home/nandor/capture001.iso

---

### Post by gimpguy2000 on 2007-08-17
> **Amazona aestiva said:**
> Dear gipmguy2000!
You didn't understand me! I know that K3B _CAN_ write ISO to HDD.
Example: K3B saved DVD ISO image as /home/nandor/capture001.iso

Hi, well what threw me off was that the option isn't enabled until you click burn. Typically, being a previous "windows weenie" most programs had the option before clicking a burn button. That's most likely where my confusion came in. 

On a side note, mkisofs made my whole system go nutty. It began showing pages of weird characters and doing something in terminal and was beeping terribly. Probably something I did, lol. 

Good news though, your last suggestion and screen shot is what did it. :) I did create the iso ! I apologize for missing that last time,  as I stated, i'm still trying to get used to everything.  #-o

So thanks very much, that worked and I appreciate the help from everyone yet again =D>

Cheers,

Paul

---

### Post by Amazona aestiva on 2007-08-17
Congratulation and good luck!
=D>=D>=D>=D>=D>

---

### Post by Sweet Spot on 2007-08-23
Question: I downloaded ISO master, and want to make a copy of Win XP for my cousin as a back up for her laptop, since I'll be attempting to install Feisty, first. She's going away to college, so I don't want her to be screwed if Ubuntu isn't her thing...

Question is then, what directories to I need to copy if I want to make the Win xp disc bootable ? I basically want an image of the XP disc I have. 

Doug

---

### Post by whereareyoutakingme on 2007-09-15
i just tried to save an .iso of a movie dvd in k3b, and 7% into the process it had an error, stating it failed to read the DVD.  i've tried using iso master and it does something similar.  the error occurs around the same time as the k3b error, but instead it says that it failed to read the expected number of bytes.  can anyone offer assistance on this??

---

