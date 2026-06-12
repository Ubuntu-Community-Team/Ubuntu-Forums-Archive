---
title: "wubi SUCKS"
date: 2007-06-06
forum: General Help
---

### Post by ReaLitaliano on 2007-06-06
looks like no one is able to help.i told people how it happen, i told u the error messages that i am getting but nothing. what more could u want? stop leaving me in the dust and help me out i am not asking 4 much.i should of never install this crap in the first place because there is no help when its needed.i been posting about the same problem from the start and i am at the same place as i started. i don't want to format my hard drive because i have some important files that i must keep.well i will be here posting more crap about the same thing forever and ever until u people get tired of reading this and maybe just maybe u will finish what u started and not just leave me in the dust.

---

### Post by meng on 2007-06-06
Getting angry isn't going to do any good. I read over your other posts, and obviously you received many suggestions but this is a two-way street and it would help if you:
1. described more clearly what was happening, and
2. followed instructions precisely
Also, wubi isn't the only way to transition from Windows to Ubuntu. If you are having so many problems, you should consider an official Ubuntu installation disk.

Another thing to consider is that if you are easily frustrated by a few setbacks, perhaps Ubuntu is not for you. Not everyone makes the change successfully the first time, don't feel bad about it.

---

### Post by ReaLitaliano on 2007-06-06
> **meng said:**
> Getting angry isn't going to do any good. I read over your other posts, and obviously you received many suggestions but this is a two-way street and it would help if you:
1. described more clearly what was happening, and
2. followed instructions precisely
Also, wubi isn't the only way to transition from Windows to Ubuntu. If you are having so many problems, you should consider an official Ubuntu installation disk.

Another thing to consider is that if you are easily frustrated by a few setbacks, perhaps Ubuntu is not for you. Not everyone makes the change successfully the first time, don't feel bad about it.

i have described it clearly,why shouldn't i be mad? i cant boot to windows or linux. i using that damn linux cd to use the net. i followed all the instructions and it dose not work people 4get about the whole thing.

---

### Post by meng on 2007-06-06
The folks who were trying to help you asked for clearer descriptions, and you didn't comply. Sometimes more information is required to understand the problem. There's an art to asking for technical help in a forum setting, and I've found it helps to swallow your pride and try to help others to help you. I'm also suggesting you realize that using an unofficial installer is not necessarily the best way to do things.

---

### Post by ReaLitaliano on 2007-06-06
hey do u know what i am seeing?huh? do u? i know u cant because that would mean your right and i  didnt comply. i dont have any more info to give ok.what i see is what u get. i think dell can do a better job.

---

### Post by meng on 2007-06-06
Good luck!

---

### Post by ago on 2007-06-06
Wubi does not touch the MBR or the partition table. It's as simple as that. If you ended up with a borked system  there are other reasons (not least hard reboots) and more likely than not the use of wubi was coincidental. If you want to recover it is generally possible and you have to rebuild the partition table and/or MBR. There are hundreds of sites on the topic and several tools,  believe it or not these things happens whether you use wubi or not.

---

### Post by ReaLitaliano on 2007-06-06
i like ubuntu i just want my windows back because of some files are important and i cant lose them thats what i first. i want to install ubuntu on a different hard drive when i get it

---

### Post by MikeM709 on 2007-06-06
People also seem to not notice that Wubi is still in it's BETA testing stages. That means that it is still not ready for the masses yet. People, like myself, are still testing it and every little bit of info or problem the developers get is good for the longrun. I highly suggest you keep up with the development of Wubi and in the future, once it is no longer beta software, you can have another go. Remember, Rome wasn't built in a day. And Wubi is not perfected in a week. Also, there is no reason to get mad because the delelopers are here helping you directly. They do not have to do that, but they do to try and help out the users and make Wubi a better program.

---

### Post by Joshiii-Kun on 2007-06-07
Exactly. Wubi is still in beta phase and thus there is a big chance that the software isn't 100% bugfree yet. By choosing to install beta software, you take full responsibility for the damage that could be done to your computer, after all, you choose to install unfinished software in the first place. The developers didn't make you do it.

But seeing what you're typing, you really did something wrong here. Wubi almost doesn't touch the system, and yet you somehow lost Windows. Did you perhaps mess around with the boot.ini?
Anyway, if your boot menu or MBR has been messed up, boot up from your Windows XP disk and get into the recovery console (At the "Welcome to Setup" screen, press R). You might be asked for what installation you want to recover (shouldn't be hard) and you will be asked for the administrator password (if you hadn't set it up before, it might be blank).
When you get into this dos-like environment, type **fixmbr c:**, or replace the c: with the drive you use. Most of the times it's c:

That should fix the MBR. Then reboot (type 'exit' or 'reboot' or something like that). This method worked for me when I had Fedora Core installed and I accidentally removed the Windows entry out of the GRUB menu (I would've fixed that manually, if I knew how :P)

---

### Post by Negeva on 2007-06-07
Sorry to hear you're having problems ReaLitaliano. I'm just about to embark on my first Linux adventure and after reading about Wubi I think this is the easiest route for me.

However, before I start I'm doing a few things first. Main item on my check list is to backup all and data and settings to removable media (CD). Then I'm making a disk image of my Windows XP partition using Acronis products - again to CD media. Then I'll be doing a few disk checks and some defragging. And while all this is being done I'm doing a few bits of research. Doesn't help you now but it might have been beneficial if you did a few of these steps yourself.

However, if you can use a live 'nix CD or even a BartPE disk then I don't see why you can't use that to browse your Windows partition and burn the data to CD/DVD. I've used [UBCD4Win]("http://www.ubcd4win.com/") in the line of business many times to recover data from a broken boot drive. The other route you can take is  to remove the hard-drive from your machine and install it another PC to remove/copy the data. While it might not fix the machine it will at least get that precious data.

---

### Post by Vadi on 2007-06-07
Just a suggestion also - how much free space did you have before you installed Wubi? I was smart enough to go by the minimum at one time, and with Windows also not warning that the hibernate file was 1gig, at the end there was only 200 mb left on my hdd, not enough for windows to load up even. I had to take the hd out and delete some of the big files to get it working again.

---

### Post by ReaLitaliano on 2007-06-07
when i installed linux it used only 5 GB

---

### Post by ReaLitaliano on 2007-06-07
i might of had 30 GB before wubi

---

### Post by ReaLitaliano on 2007-06-07
the recovery console dose not ask me which installation i want fix it goes to command line thats it.

---

### Post by rnelson on 2007-06-07
Wow! I understand frustration about these blasted 'puters, but I'm not sure that is warranted.

Wubi is still beta - the filename even says "test"

We have to be willing to break out computers to test things, or we can simply wait for Mr. Gates and M$ to sell us a solution.

Don't use beta on a machine you're not willing to handicap.

I've had my frustrations - with a Compas Pressario 2100 in particular. The other machines worked OK, but test 2 didn't work correctly at first with my new Toshiba (XP).

I'd love for Wubi to work with the Compaq, but don't have time each day to fool with it.

I'll do what I can.

Sorry to here this was so frustrating for you.

Test 2 and test 3 worked great on my desktop.

--------------

Many thanks to the herculean efforts from the Wubi development team.

You guys are brilliant and generous, and most of us really appreciate your efforts, despite the occasional frustration.

Peace,

r


------------------
"Gentlemen, you can't fight in here. This is the war room."
--(Stanley Kubrick/Peter Sellers - Dr. Strangelove, 1964)

---

### Post by minhmeoke on 2007-06-07
The "strike F1 to retry boot, F2 for setup utility" message means that there might be a hardware problem on your computer. These errors also occur on computers running Windows only, so it may not be Wubi's fault.

The first thing to do is to run the Dell Diagnostics test; see this website on how to do that:
[http://www.cs.utexas.edu/users/deke/laptopsupport/manuals/d600/diag.htm#1103353]("http://www.cs.utexas.edu/users/deke/laptopsupport/manuals/d600/diag.htm#1103353")

Run the extended test. List any errors here, with all of the details. If there are no errors, then tell us also. This will allow us to narrow down the source of the error.
Once you perform this step, we will be able to help you further.

---

### Post by ReaLitaliano on 2007-06-07
i get this error now: Caution:this hard disk may be infected by virus!

---

### Post by MikeM709 on 2007-06-07
could you explain when you get that error? wubi has no viruses, so i'm guessing that if that is true then you might have picked up a virus browsing the internet in the recent time before you installed wubi

---

### Post by Joshiii-Kun on 2007-06-07
> **ReaLitaliano said:**
> i get this error now: Caution:this hard disk may be infected by virus!

That's an awkward error message. Is it a message from your antivirus program?
If not, I suggest scanning for spyware.

---

### Post by ReaLitaliano on 2007-06-08
well i get that massage when i try to boot up

---

### Post by jimbom on 2008-02-11
I concur. Wubi sucks and is quite a shitty piece of crap.

I hope newer versions of wubi dont come with the albatross named wubi.

---

### Post by kupaka on 2008-02-14
well that's just mean... its in **BETA** fro christ's sake! 	[-X

also: what do you mean by albatross?:confused:

---

### Post by rocthrttle on 2011-01-26
> **ReaLitaliano said:**
> i like ubuntu i just want my windows back because of some files are important and i cant lose them thats what i first. i want to install ubuntu on a different hard drive when i get it

your files should show up in the livecd desktop under "places". i would do a full backup to an external drive just in case. they are not expensive. under $100 should get you a big external drive. save your files then try the following

pop in a bootable windows install cd. get to a command prompt and enter the following commands

fixmbr
fixboot

also it could be viral and unrelated to wubi/ubuntu like everyone is telling you. try trinity rescue kit to clean up your system.

[http://trinityhome.org/Home/index.php?content=TRINITY_RESCUE_KIT____CPR_FOR_YOUR_COMPUTER&front_id=12&lang=en&locale=en](http://trinityhome.org/Home/index.php?content=TRINITY_RESCUE_KIT____CPR_FOR_YOUR_COMPUTER&front_id=12&lang=en&locale=en)

if you cant handle this then pony up some money with an independent computer repair tech you find through google. 
DO NOT GO TO GEEKSQUAD THEY WILL CHARGE YOU HUNDREDS TO FORMAT AND REINSTALL YOUR OS AND LOSE ALL YOUR DATA.

---

### Post by Elfy on 2011-01-26
Hi, thanks for trying to help - but did you see the date on the previous posts. The Op has not been back since they posted in 2007.

Things in linux can move quite quickly, wubi today is somewhat different than it was in 2007.

Thread closed.

---

