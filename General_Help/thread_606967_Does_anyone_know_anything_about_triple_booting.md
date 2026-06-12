---
title: "Does anyone know anything about triple booting?"
date: 2007-11-08
forum: General Help
---

### Post by kdarkentity on 2007-11-08
I am currently booting vista and ubuntu on my laptop, and i wish to install the mac os as well, however when  i boot up my mac os install disk it cannot detect my hard drive anywhere. When i type "mount" into the terminal it finds three disks ... disk1, disk 2, and disk three, however i cannot mount them and i am unsure how to format them as a mac os file system... does anyone have any information that could assist me?

---

### Post by Niniel on 2007-11-08
I read somewhere that MacOS wants its own drive, otherwise it won't work.

But better read some of the guides yourself. Here's one:

[http://www.osx86.theplaceforitall.com/howto/]("http://www.osx86.theplaceforitall.com/howto/")

---

### Post by aldenhg on 2007-11-08
I can't help you with your problem, but I do have a word of advice: Be careful while installing OSX. The latest version of their disk utility has some problems and can destroy your everything on your hard drive. Seriously - partition BEFORE you try and install. Shrink the last partition on your drive and leave the empty space empty for the installer to deal with.

Also, GRUB should be able to boot OSX no problem, You might need a chainloader file, though.

---

### Post by kdarkentity on 2007-11-08
Thanks i appreciate it, its too bad that i might have to format my hard drive to make it tripple boot though... i just wish i was able to reformat my 10 gig partiton as a mac file system and then simply just install it...

---

### Post by Fire_Chief on 2007-11-08
You don't have to reformat the whole drive. Like aldenhg said, use a tool like gparted to format the 10GB partition as HFS+. You can also remove all formatting from that partition and leave it blank. The OSX installer should detect the partition and allow you to install to it.

---

### Post by kdarkentity on 2007-11-08
> **Fire_Chief said:**
> You don't have to reformat the whole drive. Like aldenhg said, use a tool like gparted to format the 10GB partition as HFS+. You can also remove all formatting from that partition and leave it blank. The OSX installer should detect the partition and allow you to install to it.

I actually have already tried to install onto my 10 gig partition of completely unallocated space but the mac os doesn't see it when i fire up the install disk, but i will try making it a hfs+ filesystem. I

 have gparted installed on my computer and when i select my 10 gig partition and select format to there is an option to format as hfs+ however its shadec in and i cant use it, any idea's on how to allow that option?

---

### Post by Shazaam on 2007-11-08
Boot your Ubuntu Livecd, then partition/format the unallocated space.

---

### Post by fjgaude on 2007-11-08
Gparted cannot format partitions to HFS or HFS+. I do believe that parted can but that program is not for the faint of hearts.

---

### Post by kdarkentity on 2007-11-08
i there anything other than parted i  could try?

---

### Post by fjgaude on 2007-11-08
I don't know of a user friendly interface formatter... it would be maybe one of the live CD type programs that don't use Gparted, like System Rescue or Knoppix. I'm at a loss...

---

### Post by fjgaude on 2007-11-08
> **kdarkentity said:**
> i there anything other than parted i  could try?

I found it: it's Parted Magic, which has a later version of Gparted on it which creates HFS partitions. I've just run version 1.4 of it and it looks good. Do a google and I'm sure you'll find where to download the ISO and then you can create a bootable CD to run live.

---

### Post by kdarkentity on 2007-11-08
Thank you fjgaude i will look into parted magic, if that doesn't work do you know if partition magic can format as hfs+  ?

---

### Post by fjgaude on 2007-11-08
It only shows HFS, not HFS+, which is greyed out.

---

### Post by kdarkentity on 2007-11-08
you say you tried out version 1.4? isn't the newest version 1.9?

---

### Post by fjgaude on 2007-11-08
> **kdarkentity said:**
> you say you tried out version 1.4? isn't the newest version 1.9?

I only have 1.4, if you have 1.9 maybe HFS+ is there. Give it a go.

---

### Post by kdarkentity on 2007-11-08
whats the difference between hfs and hfs+ ?

---

### Post by fjgaude on 2007-11-08
Gosh, I don't remember... it is likely that one the "+" is a journalling filesystem and the other is not.

Here we go:

[http://en.wikipedia.org/wiki/HFS_Plus](http://en.wikipedia.org/wiki/HFS_Plus)

We see that you likely will have to use HFS+ to run the later versions of Mac. Live and learn.

---

### Post by kdarkentity on 2007-11-08
Thank you again, im not going to be able to make a Parted magic disk until tomorrow tho, i will let you know how it goes.

---

### Post by #Reistlehr- on 2007-11-09
From what i remember, the only time osx will let you partition the drive it's on, is when you have and EFI based loader. But, of course, the best bet is to get a mac book. OSX is very iffy especially the newer versions as to non-mac standard hardware. It's compiled specifically for the hardware that is supplied by default from the mfr/apple. 

One cool thing to check out if your laptop supports EFI is, rEFIt. Aamazing program, i use it on my one laptop.

---

### Post by kdarkentity on 2007-11-09
Err!!.... well parted magic worked and my drive is split into three partitions with an hfs+ formated file system but still when i boot up the mac os x cd it does not detect my hard drive!, what can i do now?

---

### Post by bulldog on 2007-11-09
Is your computer a  MAC?
Otherwise you aren't aloud to install MAC OSX if I'm correct.
The license is quite clear about that as I'm told,not a MAC user myself though.

---

### Post by Fire_Chief on 2007-11-09
> **kdarkentity said:**
> Err!!.... well parted magic worked and my drive is split into three partitions with an hfs+ formated file system but still when i boot up the mac os x cd it does not detect my hard drive!, what can i do now?

It sounds like OS X does not have drivers for your motherboard chipset (IDE/SATA specifically). You may be able to find more info at the osx86project.org site.

---

### Post by fjgaude on 2007-11-09
The more I remember the more I think Apple doesn't permit their install disks to be used on anything other than their hardware. You talk about closed. <sile>

So we have this problem, this issue... what to do now?

---

### Post by Niniel on 2007-11-09
I saw a website that's dedicated to this subject. But of course I didn't save the URL... sorry. Anyway, it may be technically illegal, but people are doing it, and they are having success. Even with AMD chips. Takes patched installation ISOs though, if I remember correctly. 
I thought that forum was on that x86 website, but I'm not sure. Google for x86 and OSX.

Here's another site for you to check out (it also says that OSX wants its own drive)

[http://uneasysilence.com/os-x-proven-hacked-and-running-on-an-ordinary-pc/]("http://uneasysilence.com/os-x-proven-hacked-and-running-on-an-ordinary-pc/")

---

### Post by tech9 on 2007-11-09
> **kdarkentity said:**
> I am currently booting vista and ubuntu on my laptop, and i wish to install the mac os as well, however when  i boot up my mac os install disk it cannot detect my hard drive anywhere. When i type "mount" into the terminal it finds three disks ... disk1, disk 2, and disk three, however i cannot mount them and i am unsure how to format them as a mac os file system... does anyone have any information that could assist me?

as long as you separate partitions for each OS, you should be able to boot as many OS your HD can handle

---

### Post by kdarkentity on 2007-11-09
> **Fire_Chief said:**
> It sounds like OS X does not have drivers for your motherboard chipset (IDE/SATA specifically). You may be able to find more info at the osx86project.org site.

I do beleive my hard drive is a sata drive soo maybe thats the problem then

---

### Post by Fire_Chief on 2007-11-09
It's not so much the hard drive as the SATA controller...I've had 10.4 boot successfully on my ThinkPad T60 and it's got SATA.

Have a look at [http://wiki.osx86project.org]("http://wiki.osx86project.org")

---

### Post by kdarkentity on 2007-11-09
> **Fire_Chief said:**
> It's not so much the hard drive as the SATA controller...I've had 10.4 boot successfully on my ThinkPad T60 and it's got SATA.

Have a look at [http://wiki.osx86project.org]("http://wiki.osx86project.org")

Yea i'll look around there a little bit , but i have a question for you, are you dual booting or triple booting on your thinkpad?

---

### Post by Fire_Chief on 2007-11-09
When I did have OS X installed, I was quad booting between Vista, XP, Linux Mint, and OS X. I've since trimmed back a small bit to Vista, XP, and Ubuntu Gutsy. I have always used GRUB to manage the boot process for all the OSes installed.

---

### Post by kdarkentity on 2007-11-09
> **Fire_Chief said:**
> It's not so much the hard drive as the SATA controller...I've had 10.4 boot successfully on my ThinkPad T60 and it's got SATA.

Have a look at [http://wiki.osx86project.org]("http://wiki.osx86project.org")

Yea i'll look around there a little bit , but i have a question for you, are you dual booting or triple booting on your thinkpad?

---

### Post by reverend_HH on 2007-11-09
hey everyone, to avoid another thread i may as well ask here. i plan on installing vista on my machine and i currently have kubuntu 7.04 and xp pro, the thing is that i dont want the installation to wipe my grub settings, is there anyway to go about doing this? i havent done a vista installation before but i imagine its more or less the same as an xp installation whereas it overwrites anything in the mbr. help is greatly appreciated!

---

### Post by Fire_Chief on 2007-11-09
Take a look [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by kdarkentity on 2007-11-09
> **reverend_HH said:**
> hey everyone, to avoid another thread i may as well ask here. i plan on installing vista on my machine and i currently have kubuntu 7.04 and xp pro, the thing is that i dont want the installation to wipe my grub settings, is there anyway to go about doing this? i havent done a vista installation before but i imagine its more or less the same as an xp installation whereas it overwrites anything in the mbr. help is greatly appreciated!

Actually go ahead and install vista, it will activate he longhorn loader and you wont be able to boot into your other operating systems, however you can use Super grub disk to simply reactivate your grub, the only thing is you will have to make a custom entry for vista in your grub list which i can help you with if you need it.

If you want to try it this way here is a link to super grub disks home page[http://supergrub.forjamari.linex.org/]("http://supergrub.forjamari.linex.org/")

---

### Post by reverend_HH on 2007-11-09
thanks for the suggestions, as far as the vista entry in grub i assume it'll look more or less the same as the xp entry except different (hd0,#), right?

---

### Post by kdarkentity on 2007-11-10
> **reverend_HH said:**
> thanks for the suggestions, as far as the vista entry in grub i assume it'll look more or less the same as the xp entry except different (hd0,#), right?

Yes you are correct. good luck.

---

### Post by aldenhg on 2007-11-11
Perhaps I was a little too encouraging in my initial post. DON'T INSTALL OSX. It's just plain against the EULA and if we're going to give Linux and Ubuntu any credit at all we can't condone illegally/immoraly installing an operating system. I know, I obviously tried and it was wrong, It also obviously borked my HD and I had to reinstall 7.10. And it wasn't easy. Search for my threads and you'll see that.
It's really important to remember that while Apple hasn't sued any individual person over the OSX86 project we don't want to inadvertently implicate Ubuntu or Cannonical in any ill deeds, percieved or not. In other words, I recommend this thread be closed spiffidy quick and if you really think that OSX has any advantages over Ubuntu you take the discussion elsewhere.
I don't mean to sound like a legal fuddy duddy, but I learned my lesson and I'd rather not make any one else a party to my mistakes/misdeeds, least of all this distribution that will eventually rule the world.

---

### Post by reverend_HH on 2007-11-11
> **aldenhg said:**
> Perhaps I was a little too encouraging in my initial post. DON'T INSTALL OSX. It's just plain against the EULA and if we're going to give Linux and Ubuntu any credit at all we can't condone illegally/immoraly installing an operating system. I know, I obviously tried and it was wrong, It also obviously borked my HD and I had to reinstall 7.10. And it wasn't easy. Search for my threads and you'll see that.
It's really important to remember that while Apple hasn't sued any individual person over the OSX86 project we don't want to inadvertently implicate Ubuntu or Cannonical in any ill deeds, percieved or not. In other words, I recommend this thread be closed spiffidy quick and if you really think that OSX has any advantages over Ubuntu you take the discussion elsewhere.
I don't mean to sound like a legal fuddy duddy, but I learned my lesson and I'd rather not make any one else a party to my mistakes/misdeeds, least of all this distribution that will eventually rule the world.

lol "spiffidy"

---

### Post by kdarkentity on 2007-11-11
> **aldenhg said:**
> Perhaps I was a little too encouraging in my initial post. DON'T INSTALL OSX. It's just plain against the EULA and if we're going to give Linux and Ubuntu any credit at all we can't condone illegally/immoraly installing an operating system. I know, I obviously tried and it was wrong, It also obviously borked my HD and I had to reinstall 7.10. And it wasn't easy. Search for my threads and you'll see that.
It's really important to remember that while Apple hasn't sued any individual person over the OSX86 project we don't want to inadvertently implicate Ubuntu or Cannonical in any ill deeds, percieved or not. In other words, I recommend this thread be closed spiffidy quick and if you really think that OSX has any advantages over Ubuntu you take the discussion elsewhere.
I don't mean to sound like a legal fuddy duddy, but I learned my lesson and I'd rather not make any one else a party to my mistakes/misdeeds, least of all this distribution that will eventually rule the world.

I hear you, i understand where your coming from on this and its not that i think there are advantages to osx, i just wanted to see if triple booting with osx is possible, even tho apparently it is because people have done it. What bothers me the most about osx is that it was built off of unix, therefore it should be allowed to be used on pc's.

---

### Post by Niniel on 2007-11-11
Why "should" it be allowed? Unix is not a free software.

---

### Post by kdarkentity on 2007-11-11
> **Niniel said:**
> Why "should" it be allowed? Unix is not a free software.

oh its not?, well than i apologize on behalf of my ignorance. I thought unix was open source just as linux.

---

### Post by Niniel on 2007-11-12
Man, where have you been? :)
Never heard of the epic battle SCO has been waging to sue everybody and their grandmother over the ownership of Unix and the Unix source code? And how some of those sued supposedly stole it and incorporated it into Linux (in the case of IBM)?

OSX, to my knowledge, is based on BSD, which is not free either, although there are free versions of it, and not just one, but at least 3 (FreeBSD, NetBSD and OpenBSD - [http://cbbrowne.com/info/bsd.html]("http://cbbrowne.com/info/bsd.html")). (That's a pretty interesting read for those interested in this subject.)

---

### Post by kdarkentity on 2007-11-12
> **Niniel said:**
> Man, where have you been? :)
Never heard of the epic battle SCO has been waging to sue everybody and their grandmother over the ownership of Unix and the Unix source code? And how some of those sued supposedly stole it and incorporated it into Linux (in the case of IBM)?

OSX, to my knowledge, is based on BSD, which is not free either, although there are free versions of it, and not just one, but at least 3 (FreeBSD, NetBSD and OpenBSD - [http://cbbrowne.com/info/bsd.html]("http://cbbrowne.com/info/bsd.html")). (That's a pretty interesting read for those interested in this subject.)

Wow no kidding, where have i been? lol, thank you for sharing this knowledge.

---

