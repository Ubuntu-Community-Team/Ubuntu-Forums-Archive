---
title: "Hacked with win95?"
date: 2008-06-20
forum: General Help
---

### Post by isomorph on 2008-06-20
Dear All,

I do not know any other place to address this issue so I  put it here to General.


An unauthorized person had access to my laptop that is running Ubuntu Hardy in the standard installation. The laptop was off so I was not logged in.

The person obviously installed win95, that was put into another partition. So the ubuntu installation was still ok beside a problem of an unallocated partition.
Is my data, that is safed in home, compromised or not. Was it possible for the person to read out my files, either by dos or by win95?

Thanks for the information

cheers

Iso

---

### Post by myromance123 on 2008-06-20
OMG!! How did your laptop get into the hands of a win95 hacker??(online?)

        Sounds pretty worrisome. If he was a hacker, most probably he had no problem accessing your files, but ubuntu permitting access to win95 doesnt sound possible especially when you are not logged on. Hope everything is ok for you. Then again I am no hacker, so keep an eye on your rig :)

---

### Post by Zeotronic on 2008-06-20
In my experiance in the interaction between Windows and Linux, Windows in incapable of reading the normal partition formats of Linux... in fact its incapable (as far as I know) of reading anything beyond NTFS, and the FATs. But anyone with any skill could have installed a program to read EXT formats, or the such. Provided I am understanding you correctly, and you mean to say that the person hacked your computer by installing Windows 95, and, assumably, tried to read the files on the other partition? Its gotta be the weirdest thing I've ever heard of.

edit:
I'd check the 95 partition for any programs which are capable of understanding ext... I used to be familure with them, but a google search should help you find some names anyways.

---

### Post by iaculallad on 2008-06-20
I don't think you're /home data security had been compromised just by installing windoze 95 on another partition. Unless, you could try to boot on that win95 and see it for yourself if that unauthorized user installed a software w/c could read Ext3/Ext2 filesystem such as the Explore2fs application.

-You're data should be safe.

---

### Post by jrusso2 on 2008-06-20
Seems like a backwards way of doing things.  Almost like a prank more then a hack. Why wouldn't he use a Linux Live cd to access Linux instead he uses Windows 95?

---

### Post by Zeotronic on 2008-06-20
> Why wouldn't he use a Linux Live cd to access Linux instead he uses Windows 95?
You make do with what you have...

Most people arn't familure with Linux?

Take your pick, they both make sense to me.

---

### Post by lisati on 2008-06-20
How could the prankster install Win95 if your laptop was off?

---

### Post by Zeotronic on 2008-06-20
What I'm curious about, why do people assume this was online? I admit, I have never heard of anyone installing an OS from the other side of the internet... but perhaps I haven't gotten deep enough into the wild world of internet activities because of my limited connection.

---

### Post by jrusso2 on 2008-06-20
> **Zeotronic said:**
> What I'm curious about, why do people assume this was online? I admit, I have never heard of anyone installing an OS from the other side of the internet... but perhaps I haven't gotten deep enough into the wild world of internet activities because of my limited connection.

I am not assuming it was online he stated the laptop was off. So I figured he left it unattended.

---

### Post by jrusso2 on 2008-06-20
> **Zeotronic said:**
> You make do with what you have...

Most people arn't familure with Linux?

Take your pick, they both make sense to me.

Someone unfamiliar with Linux just happens to have a Windows 95 cd with them that can only read fat 16 and fat 32 and figures that can hack linux?

That makes sense.

---

### Post by VMC on 2008-06-20
The very fact that he installed Windows should be telling enough. If he wanted to compromise your Linux files he would have just booted into Linux and then done something.

---

### Post by lisati on 2008-06-20
> **Zeotronic said:**
> What I'm curious about, why do people assume this was online? I admit, I have never heard of anyone installing an OS from the other side of the internet... but perhaps I haven't gotten deep enough into the wild world of internet activities because of my limited connection.

Is it possible that some suitably knowlegable had physical access to your machine and was able to sneak Win95 on while you weren't looking?

---

### Post by Zeotronic on 2008-06-20
> Someone unfamiliar with Linux just happens to have a Windows 95 cd with them that can only read fat 16 and fat 32 and figures that can hack linux?

That makes sense. 
We're talking your run of the mill idiot... someone unfamilure with NTFS and FAT and such? You think their not out there? I know quite a few of them... some of which would try something like this. One of which in particular who would have probably messed this much up.

Edit:
But I should probably reserve further comment until more information is given.

---

### Post by nig_nig_the_conqueror on 2008-06-20
Yeah...how exactly did an "unauthorized person" have access to your computer if it was turned off?  I'm assuming someone had physical access to your computer.  And like Zeotronic said, Windows can't read ext2 and ext3 by default (it would need a special app to do that) so I don't really know what the benefit of going through all that work would be.  Are you some sort of secret agent?  Why would somebody go through all this work to access your files?  You might want to stop looking for a phantom hacker and start looking for a joker with access to your pc.

---

### Post by iaculallad on 2008-06-20
And maybe, the laptop's default booting sequence was to boot first on it's CD/DVDROM before reading it's HDD, or, that unauthorized user knew the BIOS setup password, change the boot sequence and had the windoze 95 installed.

Point is: **If it's just the windoze 95 installed**, /home data is SAFE for FAT32 OS cannot access Ubuntu supported Filesystems (Ext2/Ext3/ReiserFS..etc..).

---

### Post by claschxtreme on 2008-06-20
Hahaha! is this a joke? 

If this is true i'd say it's some achievement. Come on, the fdisk that comes with win95 was "pure manure" when it comes to handle non-Dos partitions. I remember that i used to boot up with OS/2 startdisks to make any changes before installing dos/win. As far as i know it's imposible to do it without some more modern tools, and then the question would be : why to do such a thing? 
I can only think of very negative/destructive reasons, win95 is like leaving your door open and a big sign on your front yard that says "Nobody home".

And then again, if this is true i would advice you to resize your ext3-partition and get rid of win95 as soon as posible. And don't even think of booting win95.

---

### Post by isomorph on 2008-06-21
Hey Folks thanks for the information that far.

It sounds like I was lucky and my data is still save.

But I think I have to clarify some things.

The laptop was in the office overnight and it was naturally shutdown during this time. Unfortunately the BIOS Password was off. Only the normal Ubuntu login was activated.

So someone sneaked into my office started the laptop and installed Win95 beside my Ubuntu installation to access my files, obviously he tried to install Win95 in the laptop because I found this partition.

In my mind there are two possibilities why it was Win95
1. it was a total idiot who has no idea about computer or 
2. there is a special hack with win95 to access Linux files.

My guess is  1. because a pro would have taken care of the win95 installation afterwards.

I realised that something is wrong the next morning when I started the laptop and I get a message that windows/blablabla was not found please insert the disk and afterwards I get GRUB errors.

The biggest problem for me was to allocate the unallocated partition again (i am a total noob) to safe my files. Then formated the whole laptop and installed a clean ubuntu (Just to be safe that there is no way to get to my files).

I learned a few things about linux up to now. My BIOS password is activated again. The laptop goes to the safe overnight and I just started reading about encryption of Folders.

cheers

Iso

---

### Post by myromance123 on 2008-06-21
I'm glad for you mate :)
     Why not get some forensic equipment and check the fingerprints of the person who meddled with your pc ?? (just kiddin XD  )

    But now you know there is someone who wants your job, so stay safe and keep your laptop with you whenever you can (especially if you have kids!!)

  Ubuntu saved the day eh. This story should be something all people who are interested in ubuntu should read about :D

  Congrats ~

---

### Post by Peter09 on 2008-06-21
Just a thought, are you sure that the win95 was not in an existing partition that was on the laptop when you installed Ubuntu?

PC

---

### Post by isomorph on 2008-06-21
> **Peter09 said:**
> Just a thought, are you sure that the win95 was not in an existing partition that was on the laptop when you installed Ubuntu?

PC

The laptop was bought end of 2006 running XP from the start. Then I installed Ubuntu by formating the HD. No I am pretty sure there was no 95 on;)

cheers

Iso

---

### Post by VMC on 2008-06-21
This is the strangest thing I've ever heard.

Usually someone breaks into an office an steals a laptop, not installs Windows 95.

Maybe the guy works for Microsoft and was offended knowing you were using Linux :)

---

### Post by myromance123 on 2008-06-21
HAhahahahahahah, that could be true !! XD

  Good thinking mate ~
Maybe it was a belated happy birthday present :P
   Anyhow, he gave you a free windows OS XD

:guitar:    (why use Win95 when theres XP?? Noob hacker? Ubuntu hater?dumb?)

---

### Post by Fingel on 2008-06-21
Sounds like someone's idea of dumb joke.

---

### Post by Zeotronic on 2008-06-21
> Usually someone breaks into an office an steals a laptop, not installs Windows 95.
I agree... this has got to be the oddest thing I have ever heard of.

---

