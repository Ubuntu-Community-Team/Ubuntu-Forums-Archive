---
title: "Just a Few General Questions"
date: 2008-06-25
forum: General Help
---

### Post by Brifry on 2008-06-25
Hey, I was thinking of using Wubi because I used a live cd and thought it was pretty cool. So the computer that I'm installing it on doesn't have a internet connection, so I downloaded Wubi 8.04 and a Live CD 8.04 Desktop. So I just empty the files into a folder with wubi.exe right? Or do I need to put these files in a specific folder like C:\Ubuntu? Also, I wanted to mainly use this for games, so I can install just like a normal Ubuntu installation would require right? And finally, when I was looking at some of the applications I didn't notice Wine there, do I have to install this manually? If I could get some answers to these questions I would greatly appreciate it.

Oh, and by the way, I think under the system requirements of Wubi, you should tell them they need a internet connection, because someone could just download it and try to install it on a different computer, and it might not have an internet connection.

---

### Post by prshah on 2008-06-25
> **Brifry said:**
> 
so I downloaded Wubi 8.04 and a Live CD 8.04 Desktop. So I just empty the files into a folder with wubi.exe right? 

Oh, and by the way, I think under the system requirements of Wubi, you should tell them they need a internet connection


You don't need an internet connection to install Ubuntu 8.04 using Wubi.

8.04 Live Desktop CD includes Wubi; you shouldn't download it separately. If you run the Wubi off the 8.04 CD, it will use the CD to install ubuntu and not your Internet connection.

To use the Wubi that comes with the CD, just put your CD in the drive and choose the 2nd (?) option that gives you the option to install Ubuntu in Windows.

---

### Post by Brifry on 2008-06-25
Thanks for that, but what about wine?

And can you install games to ubuntu (wubi) just the same way as if that was your only os on the computer?



And this is why I am going to use the CD, and the Downloaded Wubi.exe

"Safe installation procedure
   1. Uninstall any previous Wubi installation. Feel free to back it up.
   2. Run chkdsk /r on the target drive. Open a dos box and go into the drive where you plan to install Wubi, then run the command: chkdsk /r
   3. Defragment you disk. Download and install jkdefrag, and defragment the drive where you want to install Wubi.
   4. Use the ISO directly instead of the CD. This way you avoid all burning issues. Place both the ISO and Wubi in the same folder and run wubi.exe from there. You can also let Wubi download the ISO for you (it will do so if it cannot find any ISO in the same folder of Wubi.exe and in /ubuntu-backup)
   5. The ISO must be an 8.04 CD Desktop ISO. Do not use a DVD ISO or the Alternate ISO. If you have other ISOs around make sure they are not in the same folder of wubi.exe or in /ubuntu-backup
   6. Now run the Wubi installer
   7. If you have problems booting or experience a black screen, press ESC after selecting "Ubuntu" at boot and try one of the other options"

It's in your Faq quide.

---

### Post by avtolle on 2008-06-25
Yes, you would need to install wine under Ubuntu as in all other cases. Same with games, etc.

A bit of confusion here, I believe, so I'll add to it: the FAQ section that the OP posted discusses using wubi.exe to install Ubuntu in a situation where the option available on the 8.04 Live CD is not chosen. However, as was pointed out by prshah, the 8.04 Live CD specifically has an option to install "within windows", which merely requires booting the Live CD and selecting the option.

---

### Post by Brifry on 2008-06-25
> **avtolle said:**
> Yes, you would need to install wine under Ubuntu as in all other cases. Same with games, etc.

A bit of confusion here, I believe, so I'll add to it: the FAQ section that the OP posted discusses using wubi.exe to install Ubuntu in a situation where the option available on the 8.04 Live CD is not chosen. However, as was pointed out by prshah, the 8.04 Live CD specifically has an option to install "within windows", which merely requires booting the Live CD and selecting the option.

Well, it just said safe install so I assumed it'd be the safest way to install Ubuntu without messing up any Windows file. If I choose the option of Installing Ubuntu in Windows, it won't touch any files that I already have on my computer, and it won't make Ubuntu take over as the OS right? Cause I want the whole Dual Boot option, and I'll be really pissed if Windows doesn't work after this.

---

### Post by prshah on 2008-06-26
> **Brifry said:**
> Thanks for that, but what about wine?
And can you install games to ubuntu (wubi) just the same way as if that was your only os on the computer?



There is no connection between these questions and the method of installation. Whether you install using downloaded Wubi or using the 8.04 live CD (in Windows, do _not_ boot off it!), it's all the same. You can still install wine and/or games as though Ubuntu was/is the only OS. I repeat, it's all the same whether you download and use Wubi or use the Wubi off the Live CD. In any case, there is no such requirement in Ubuntu that a certain program will work _only_ if ubuntu is the _only_ OS on the system. 

The advantage of downloading Wubi and the live ISO separately is only to avoid situations such as a bad CD (coaster), etc. If you are fairly confident of your CD writer, you can burn the image to CD, then remove and re-insert the CD and wait for the autorun program to come up. From that, choose the second option "Install inside Windows"

> **avtolle said:**
> 
the 8.04 Live CD specifically has an option to install "within windows", which merely requires **booting the Live CD and selecting the option.**

Sorry, but that's not the way it's done... if you "boot" from the CD, you cannot do a Wubi install. 

I think you must have meant that you should put the CD in the drive when windows is running and then wait for the autorun program to kick in.

---

### Post by Brifry on 2008-06-26
> Sorry, but that's not the way it's done... if you "boot" from the CD, you cannot do a Wubi install.

I think you must have meant that you should put the CD in the drive when windows is running and then wait for the autorun program to kick in.

Thanks that answered my question. I have a problem though, I have 256mb ram and it won't let me install it because it says it needs at least 256mb ram to install, what's up with that? I'm booting windows and trying to install inside there, so how would I fix that?

EDIT: Oops, I just saw this post:[http://ubuntuforums.org/showthread.php?t=836206]("http://ubuntuforums.org/showthread.php?t=836206") I think I'll just install Wubi 7.04, it'll probably run better too.

---

### Post by ago on 2008-06-26
> **Brifry said:**
> Thanks that answered my question. I have a problem though, I have 256mb ram and it won't let me install it because it says it needs at least 256mb ram to install, what's up with that? I'm booting windows and trying to install inside there, so how would I fix that?

That is becasue not all of your memory might actually be available.
Please use 8.04.1, you will see a worning but you will be able to continue.
Note that 8.04.1 requires a new iso

---

### Post by Brifry on 2008-06-26
> **ago said:**
> That is becasue not all of your memory might actually be available.
Please use 8.04.1, you will see a worning but you will be able to continue.
Note that 8.04.1 requires a new iso

What are the differences between 7.04 and 8.04.1 (Ubuntu)? I mean, I want it to run as fast as possible, so I'm thinking a older version would work out better. Is it just program updates or is there something really big that changed?

---

