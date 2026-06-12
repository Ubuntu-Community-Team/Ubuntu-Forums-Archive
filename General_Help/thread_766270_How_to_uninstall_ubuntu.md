---
title: "How to uninstall ubuntu?"
date: 2008-04-25
forum: General Help
---

### Post by Pokeh on 2008-04-25
Okay, long story as short as I can get it:
2 days ago I decided to install Ubuntu (Yeah, 7.10 or whatever it's called) just to see if I could install another operating system on my machine at once without messing anything up. With a bit of luck, screaming and swearing, I managed to get it to work. So the next day (Yesterday) I decided to upgrade it. This also worked without any problems. The only reason I upgraded was to use the "Easy to uninstall" feature that's advertised on the front page. I never intended on keeping Ubuntu, it was one of those little "test yourself" things (Although I might re-install it on a smaller partition some other time).

So yeah, I kind of can't find the uninstall feature. It's not in the System>>Administration folder (From what I can see). Nothing comes up when I search for it in the help box and nothing really comes up in the search box either. Some help would be great.

---

### Post by TeoBigusGeekus on 2008-04-25
Assuming you wanna keep working with window$:
Boot up with the live cd and use gparted to format the Ubuntu partition to ntfs. Use the same program to add the partition to your win partition.
Next, boot up with the window$ cd and go to recovery mode. Type
```
fixmbr
```
to get rid of grub.
Restart and you're done.

---

### Post by Pokeh on 2008-04-25
> **TeoBigusGeekus said:**
> Assuming you wanna keep working with window$:
Boot up with the live cd and use gparted to format the Ubuntu partition to ntfs. Use the same program to add the partition to your win partition.
Next, boot up with the window$ cd and go to recovery mode. Type
```
fixmbr
```
to get rid of grub.
Restart and you're done.I assume the Live CD is the one that I had to burn myself?

Also, my laptop didn't come with a windows disk. If it helps, the version of windows that I was using was Vista (Which still has its own partition on my hard drive).

---

### Post by TeoBigusGeekus on 2008-04-25
The live cd is indeed the one you burnt yourself.
But don't delete Ubuntu unless you find a win cd. Otherwise, your grub menu will be erased and you won't be able to boot into vista.

---

### Post by Pokeh on 2008-04-25
> **TeoBigusGeekus said:**
> But don't delete Ubuntu unless you find a win cd. Otherwise, your grub menu will be erased and you won't be able to boot into vista.Yeah, I learned that the hard way. x_X

Seeing as I have Vista home basic, would buying a Vista Home Premium disk work (Hey if you've got to buy a new disk you might as well upgrade, right?).

---

### Post by HunterThomson on 2008-04-25
"""""Seeing as I have Vista home basic, would buying a Vista Home Premium disk work (Hey if you've got to buy a new disk you might as well upgrade, right?)."""""":(:(:(:

Boy O' Boy, You should really really try out Linux more.... VISTA.................:(:(:(:(:(

---

### Post by HunterThomson on 2008-04-25
Premium is not really a "Upgrade" they just charge you more $ stick you with a bunch more crappy programs that eat up all your RAM, Hard Drive space, CPU time, GPU time... and you have to delete after the 30 free trial so you can download Good programs that Surprise Surprise are Open Source. If anything download a Cracked XP and install that.

You know I have a Vista Home CD that came with my computer I will give it you... Were do you want me to mail it to???

---

### Post by Pokeh on 2008-04-25
> **HunterThomson said:**
> Boy O' Boy, You should really really try out Linux more.... VISTA.................:(:(:(:(:(Considering that Ubuntu doesn't even have support for Wireless (Not for me anyway), I think i'd rather stick to Vista, which allows me to move around my house rather than being confined to a metre radius of my router.

I have to sit in the main computer room, putting up with my sisters God-awful music. Not fun.

And could we actually help here? Flaming Vista doesn't exactly help, it works fine for me. Would buying a Vista Premium upgrade CD work? Yes or no.

---

### Post by HunterThomson on 2008-04-25
I really will mail you my vista cd. I mite be able to make a Iso and you could download it but I bet M$ put some stuff on there to stop me. 

What wireless card do you have? Should be able to get it to work no problem:) I bet you have a Broadcom chipset if it is not being automaticly set up. Try and type this in the terminal.

ifconfig -a

dose it show Wlan0 ??

And come on nobody likes Vista.:wink:

(I was just upset that widow$ didn't even give you a CD that you already paid for, ~$100 in the price of your computer, and now you are thinking about buying it again... I just hate to see people getting F'd over)

If you can still boot into window$ I bet there is a program to burn your own recovery CD's that is normally what they do if they don't give them to you.

---

### Post by Separ on 2008-04-25
The "Easy to Uninstall" thing was meaning the wubi installer which would not even have to partition your drive and would install inside windows.

If you have any sort of windows recovery disk (You should be able to even get one cheap at a local computer store or ebay or something) then you can boot into a prompt and do as suggested above.

Hope that helps :D

---

### Post by Pokeh on 2008-04-25
> **HunterThomson said:**
> I really will mail you my vista cd.I live in Britishland, you live in (According to your profile) Hawaii, it'd cost you quite a bit of cash to ship that all the way over here wouldn't it?

> **HunterThomson said:**
> What wireless card do you have?It's '**Atheros 5007EG Wireless Network Adapter**'. Couldn't find any links to places selling it or anything on Google but it's what came with the laptop.

> **HunterThomson said:**
> And come on nobody likes Vista.:wink:It's not perfect, I admit, but I just prefer it to Ubuntu. *shrug*

---

### Post by priegog on 2008-04-25
If you can still boot into Vista I believe there should be an option somewhere to create a recovery disk. You might want to ask vista help, because it's been a long time since I've used Windows and never have used Vista anyways.

---

### Post by HunterThomson on 2008-04-25
Ya I edited my post there should be that burn your own recovery cd.

And I know were to get the atheros drivers hold on.....

It is one of the best wireless cards!!!! You can crack WPA!!!

---

### Post by Pokeh on 2008-04-25
> **priegog said:**
> If you can still boot into Vista I believe there should be an option somewhere to create a recovery disk. You might want to ask vista help, because it's been a long time since I've used Windows and never have used Vista anyways.All I can really see is the Backup Utility, which skips System and Program files. I'll have a look though.

**Edit:** I found [this](http://blogs.techrepublic.com.com/window-on-windows/?p=622), just wondering if that'll work.

---

### Post by HunterThomson on 2008-04-25
No will not cost too much to mail you the CD. I'll pay for it myself just give me a address.

One Min for the drivers......

---

### Post by priegog on 2008-04-25
Most computer manufacturers have a proprietary program to create these recovery discs. I found this one for HP for instance: [http://www.wikihow.com/Create-Recovery-Discs-for-Windows-Vista-in-HP-Recovery-Manager](http://www.wikihow.com/Create-Recovery-Discs-for-Windows-Vista-in-HP-Recovery-Manager)
What brand is yur computer?

---

### Post by HunterThomson on 2008-04-25
Here are the drivers 

[http://sourceforge.net/forum/forum.php?forum_id=675820](http://sourceforge.net/forum/forum.php?forum_id=675820)

---

### Post by priegog on 2008-04-25
OK, did some more research and apparently you can do this in a generic Vista install, as long as you have SP1. If you don't I guess you could do a windows update.
And if you do, here's where you find it: click on the Start menu, All programs, Maintenance, and Create a Recovery Disc.

---

### Post by Pokeh on 2008-04-25
> **HunterThomson said:**
> No will not cost too much to mail you the CD. I'll pay for it myself just give me a address.Well, if you *really* want to send me the CD, then add me on MSN or send me a PM (My MSN's in my profile) and i'll give it to you there.

> **priegog said:**
> Most computer manufacturers have a proprietary program to create these recovery discs. I found this one for HP for instance: [http://www.wikihow.com/Create-Recovery-Discs-for-Windows-Vista-in-HP-Recovery-Manager](http://www.wikihow.com/Create-Recovery-Discs-for-Windows-Vista-in-HP-Recovery-Manager)
What brand is yur computer?The brand is Acer. I know, sucks, right?

---

### Post by grannyw on 2008-04-25
> **Pokeh said:**
> Considering that Ubuntu doesn't even have support for Wireless (Not for me anyway), I think i'd rather stick to Vista, which allows me to move around my house rather than being confined to a metre radius of my router.

I have to sit in the main computer room, putting up with my sisters God-awful music. Not fun.

And could we actually help here? Flaming Vista doesn't exactly help, it works fine for me. Would buying a Vista Premium upgrade CD work? Yes or no.

it has u just have to configure it

---

### Post by HunterThomson on 2008-04-25
here are the drivers 

[http://sourceforge.net/forum/forum.php?forum_id=675820](http://sourceforge.net/forum/forum.php?forum_id=675820)

---

### Post by priegog on 2008-04-25
> **HunterThomson said:**
> Here are the drivers 

[http://sourceforge.net/projects/madwifi/](http://sourceforge.net/projects/madwifi/)

I have to make a disclaimer and say that I'm as sad as you are that this guy wants to go back to windows, but since you took the way of helping him with his ubuntu problems, I am trying to give him what he wants so that we won't come off as a telephone company who won't let you sign-off with them :)
Anyways I hope he gives Ubuntu another chance, because we all know what it's like not to feel "at home" the first few weeks of using Ubuntu, but eventually just the idea of using a Windows PC becomes unberarable.

---

### Post by HunterThomson on 2008-04-25
Sorry man.... I told him that he should be able to burn his own recovery cd's too.... And I got him alsom wireless drivers so now I'll go to another post....

---

### Post by Pokeh on 2008-04-25
> **priegog said:**
> OK, did some more research and apparently you can do this in a generic Vista install, as long as you have SP1. If you don't I guess you could do a windows update.
And if you do, here's where you find it: click on the Start menu, All programs, Maintenance, and Create a Recovery Disc.It's not there. o_O

[img]http://img509.imageshack.us/img509/9035/thingeray0.jpg[/img]

And thanks for the Dirvers, i'll download them when (if) I next boot up Ubuntu.

---

### Post by priegog on 2008-04-25
humm... are you positive you got service pack 1 installed? I found it on this page
[http://www.techticles.com/how-to-guide-create-windows-vista-recovery-disk.page](http://www.techticles.com/how-to-guide-create-windows-vista-recovery-disk.page)
(horible page, but that's what there is)

---

### Post by Pokeh on 2008-04-25
> **priegog said:**
> humm... are you positive you got service pack 1 installed? I found it on this page
[http://www.techticles.com/how-to-guide-create-windows-vista-recovery-disk.page](http://www.techticles.com/how-to-guide-create-windows-vista-recovery-disk.page)
(horible page, but that's what there is)I'm pretty certain I have. Especially with all the trouble I had installing it.

**Edit:** I do have SP1 installed. It says so when I Right-Click > Properties in My Computer.

---

### Post by priegog on 2008-04-25
I guess you could download and burn a recovery disc
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
I'm willing to keep researching, so if for some reason you won't settle for this let me know

---

### Post by Pokeh on 2008-04-25
> **priegog said:**
> I guess you could download and burn a recovery disc
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
I'm willing to keep researching, so if for some reason you won't settle for this let me knowStupid Question: Do you know where I can get a BitTorrent client from? The 'official' one messes-up my Internet for some reason.

---

### Post by priegog on 2008-04-25
Apparently there's also something called acer recovery management. Give that a try.

---

### Post by priegog on 2008-04-25
> **Pokeh said:**
> Stupid Question: Do you know where I can get a BitTorrent client from? The 'official' one messes-up my Internet for some reason.

You're on you ubuntu install right now? :) If that's the case, open a terminal and type
sudo apt-get install deluge
If you're on Windows, you can always use utorrent

edit: The reason transmission hoses your connection is PROBABLY becauseyou need to cap the upload speed to something slightly lower than what your ISP gives you, thus not "clogging" it. You would have the same problem with deluge if that's the case

---

### Post by Pokeh on 2008-04-25
> **priegog said:**
> You're on you ubuntu install right now? :)Hellz no. xD

> **priegog said:**
> If you're on Windows, you can always use utorrentI'll take a look for that then.


And earlier I found this, i'm just wondering if they're both the same thing (This one doesn't require BitTorrent):
[http://blogs.techrepublic.com.com/window-on-windows/?p=622](http://blogs.techrepublic.com.com/window-on-windows/?p=622)

---

### Post by priegog on 2008-04-25
> **Pokeh said:**
> Hellz no. xD

I'll take a look for that then.


And earlier I found this, i'm just wondering if they're both the same thing (This one doesn't require BitTorrent):
[http://blogs.techrepublic.com.com/window-on-windows/?p=622](http://blogs.techrepublic.com.com/window-on-windows/?p=622)

Not sure, but I guess that'll work too. I didn't know Vista came with an "official" bt client, that's weird.
Anyways, how can you NOT use bittorrent in this day and age? You don't know what you're missing!:)

---

### Post by Pokeh on 2008-04-25
> **priegog said:**
> Not sure, but I guess that'll work too. I didn't know Vista came with an "official" bt client, that's weird.
Anyways, how can you NOT use bittorrent in this day and age? You don't know what you're missing!:)Vista doesn't come with a BitTorrent client, I was referring to [this](http://www.bittorrent.com/download), I just assumed it was the official version.

And yeah, I think I used BitTorrent like, once. o_O

---

### Post by geethalakshmi on 2008-04-25
Hi,
   The link given below describes you how to uninstall ubuntu.
[http://hiox.org/bypass/index.php?id=234]("http://hiox.org/bypass/index.php?id=234")

With regards
Geethalakshmi
[http://www.hiox.org/]("http://www.hiox.org/")
[http://www.mnbvcxz.org/]("http://www.mnbvcxz.org/")

---

### Post by Pokeh on 2008-04-25
> **geethalakshmi said:**
> Hi,
   The link given below describes you how to uninstall ubuntu.
[http://hiox.org/bypass/index.php?id=234]("http://hiox.org/bypass/index.php?id=234")I have Windows Vista, but not Windows XP. Thanks anyway though.

---

### Post by priegog on 2008-04-25
> **Pokeh said:**
> Vista doesn't come with a BitTorrent client, I was referring to [this](http://www.bittorrent.com/download), I just assumed it was the official version.

And yeah, I think I used BitTorrent like, once. o_O

Oh, yeah, it kind of is but nobody uses it anyways :P
Also, disregard the post above me, as it is not for Vista and it will come down to having to use a recovery cd also. But try and cap the upload on the "official" client anyways.

---

### Post by Pokeh on 2008-04-25
Well, I just finished downloading the ISO file so i'm burning it to a disk now. Tum Te Tum...

---

### Post by priegog on 2008-04-25
> **Pokeh said:**
> Well, I just finished downloading the ISO file so i'm burning it to a disk now. Tum Te Tum...

Once you get it done, you can try ubuntu installing wubi, which is what you had read about it being easily uninstallable and not needing to repartition. I'm REALLY sure it would be a matter of you getting a little used to it to start loving it. Anyways, remember we're here to help :)

---

### Post by Pokeh on 2008-04-25
> **priegog said:**
> Once you get it done, you can try ubuntu installing wubi, which is what you had read about it being easily uninstallable and not needing to repartition. I'm REALLY sure it would be a matter of you getting a little used to it to start loving it. Anyways, remember we're here to help :)So wait, it's just finished burning, so what do I do now exactly?

---

### Post by priegog on 2008-04-25
> **TeoBigusGeekus said:**
> Assuming you wanna keep working with window$:
Boot up with the live cd and use gparted to format the Ubuntu partition to ntfs. Use the same program to add the partition to your win partition.
Next, boot up with the window$ cd and go to recovery mode. Type
```
fixmbr
```
to get rid of grub.
Restart and you're done.

This
But I'm not sure if Vista would work in the same way. I guess it's worth a shot?

---

### Post by Pokeh on 2008-04-25
> **priegog said:**
> This
But I'm not sure if Vista would work in the same way. I guess it's worth a shot?I'll give it a go now, i'll use my other PC to keep in touch if my laptop explodes or something.

---

### Post by priegog on 2008-04-25
:lolflag: I'll be standing by.

---

### Post by Pokeh on 2008-04-25
Questions before I begin:

1- What's *gparted*, or will this become clear to me while i'm booting up or whatever?

2- There is no #2, I thought I had more. Whoops. xD

---

### Post by priegog on 2008-04-25
gparted is the ubuntu partition editor. I'm not sure if you can acces it with the live-cd, tho (i guess you can if the guy who wrote it said you could). To acces it (if available) go to the menu System>Administration>Partition Editor. If you can't find it let me know

---

### Post by priegog on 2008-04-25
More info: apparently you CAN'T acces it from the live cd. So what you're gonna do is make sure you have internet acces while on the live cd, open up a terminal and paste:
sudo apt-get install ntfsprogs gparted
After that you should be able to find it and carry on.

edit: make that 
sudo apt-get update && sudo apt-get install ntfsprogs gparted

---

### Post by Pokeh on 2008-04-25
> **priegog said:**
> More info: apparently you CAN'T acces it from the live cd.Well, I just did, so yeah. o-O

---

### Post by priegog on 2008-04-25
Even better :)

---

### Post by Pokeh on 2008-04-25
> **priegog said:**
> Even better :)Yup, so I just did the partition thinger so now i'm about to put the Windows CD in.

---

### Post by Pokeh on 2008-04-25
And now I have absolutely no idea what i'm doing at all. -_-

---

### Post by priegog on 2008-04-25
So describe it to us.

---

### Post by Pokeh on 2008-04-25
Right

I start the CD - Tells me to press Any Key to boot from the CD. 

Then it says Windows is Loading files, I wait a little while, and you get the normal 'startup' thing with the moving bars.

Then I get a blue background come up with an 'Install Windows' box come up. I select the Language - English, Time & Currency Format - English (United Kingdom), and the Keyboard Layout - United Kingdom. I click on Next.

I'm given 3 options:

1- Install Windows

2- What to know before installing Windows

3- Repair your computer

So I clicked on Option 1 - Install Windows. I'm asked to enter a serial number on the back of my laptop - I do this but then it says the Install file cannot be found because it doesn't exist. How useful.

So I click on Option 3 - Repair your computer. It searches for Vista installations and after while it comes up with the installation on the laptop. I select it and click on Next. I'm given a number of options, and this is one of them:

- Startup Repair (Automatically fix problems that prevent windows from starting)

I select this, and it scans for problems. After a while, it tells me that there aren't any problems present at all.

There was also an option for command promt. I clicked on this and typed in that *fixmbr* thing you were on about earlier. This didn't do anything.

I restarted the computer anyway, but that Grub thing's still there.

---

### Post by TeoBigusGeekus on 2008-04-25
Alright, apparently vista does not work like xp. What you need is super grub.
[http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/")

---

### Post by Pokeh on 2008-04-25
*headtodesk*

---

### Post by Pokeh on 2008-04-25
Can someone please explain to me wtf I have to do before I go nuts? =/

---

### Post by priegog on 2008-04-25
> **Pokeh said:**
> Can someone please explain to me wtf I have to do before I go nuts? =/

Haha, hopefully you won't need supergrub. I'm currently researching, but have a look here [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by TeoBigusGeekus on 2008-04-25
> **priegog said:**
> Haha, hopefully you won't need supergrub. I'm currently researching, but have a look here [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

That link is another testimony of why Vista sucks...

---

### Post by priegog on 2008-04-25
appaerntly from that link i gave you, you have to:
1)click repair your computer
2)click vista
3)In the System Recovery Options dialog box, click Command Prompt.
4)Type Bootrec.exe, and then press ENTER
5) use the option /FixBoot (not sure how to do that, either select it, type it, or something along those lines) hopefully this will be the end of this

---

### Post by Pokeh on 2008-04-25
"/FixBoot is not recognised as an internal or external command, operatable program or batch file"

Just buying an Upgrade CD is just looking a lot more tempting, regardless of the cost. x-X

---

### Post by priegog on 2008-04-25
> **Pokeh said:**
> "/FixBoot is not recognised as an internal or external command, operatable program or batch file"

Just buying an Upgrade CD is just looking a lot more tempting, regardless of the cost. x-X

Well, yeah, but the upgrade CD would not work either, except for doing a clean install )and if that's what you're after, heck download a vista ultimate iso)
So tell me, what happens when you type Bootrec.exe? Does it give you any options?
Oh nevermind, apparently what you have to do after entering bootrec.exe is type
bootrec /FixBoot
Not sure if caps are important but try that and see what happens

---

### Post by TeoBigusGeekus on 2008-04-25
Go to the page I gave you and download the supergrub cd. Burn it and boot with it. For more info
[http://www.supergrubdisk.org/wiki/Main_Page]("http://www.supergrubdisk.org/wiki/Main_Page")

---

### Post by priegog on 2008-04-25
> **TeoBigusGeekus said:**
> Go to the page I gave you and download the supergrub cd. Burn it and boot with it. For more info
[http://www.supergrubdisk.org/wiki/Main_Page]("http://www.supergrubdisk.org/wiki/Main_Page")

Could we leave this solution for an if-all-else-fails approach? 
He doesn't want to run ubuntu or any other OS's anymore, apart from windows. The standard bootloader from windows itself should be more than enough

---

### Post by Pokeh on 2008-04-25
> **priegog said:**
> Well, yeah, but the upgrade CD would not work either, except for doing a clean install )and if that's what you're after, heck download a vista ultimate iso)
So tell me, what happens when you type Bootrec.exe? Does it give you any options?
Oh nevermind, apparently what you have to do after entering bootrec.exe is type
bootrec /FixBoot
Not sure if caps are important but try that and see what happensThat didn't work either. It said "The volume does not contain a recognised file system".

Yeah, i'm going to download that SuperGrub thing. x_X Anyone got a download link? That page confuses me.

---

### Post by Pokeh on 2008-04-25
And yeah, I kind of can't run Ubuntu anymore because it's not on my Hard Drive anymore. And there's no way i'm installing that again.

---

### Post by priegog on 2008-04-25
> **Pokeh said:**
> That didn't work either. It said "The volume does not contain a recognised file system".

Yeah, i'm going to download that SuperGrub thing. x_X Anyone got a download link? That page confuses me.

That error message makes me think you probably hosed your system:confused:. Try and boot into Vista just to be sure

---

### Post by Pokeh on 2008-04-25
> **priegog said:**
> That error message makes me think you probably hosed your system:confused:. Try and boot into Vista just to be sureI can't. Grub hates me (And I hate it back), so I can't boot anything off my hard drive.

If this helps, here's what the screen says when I try to boot-up without starting up the CD:

GRUB Loading Stage 1.5

GRUB Loading, Please wait...
Error 22

I can't type anything in at all.

---

### Post by priegog on 2008-04-25
> **Pokeh said:**
> I can't. Grub hates me (And I hate it back), so I can't boot anything off my hard drive.

If this helps, here's what the screen says when I try to boot-up without starting up the CD:

GRUB Loading Stage 1.5

GRUB Loading, Please wait...
Error 22

I can't type anything in at all.

I'm not familiar with grub error messages... but that error message in the recovery console makes me think it all went to s**t somewhere along the way. So I guess unless you can prove your windows partition is still there and intact, it doesn't make sense to keep trying. You'll just have to do a clean install. Most manufacturers will mail you a Windows CD if you ask for it.

---

### Post by Pokeh on 2008-04-25
> **priegog said:**
> I'm not familiar with grub error messages... but that error message in the recovery console makes me think it all went to s**t somewhere along the way. So I guess unless you can prove your windows partition is still there and intact, it doesn't make sense to keep trying. You'll just have to do a clean install. Most manufacturers will mail you a Windows CD if you ask for it.Yeah, i'll try asking them for a disk or something...

---

### Post by adrian15 on 2008-04-25
> **priegog said:**
> I'm not familiar with grub error messages... but that error message in the recovery console makes me think it all went to s**t somewhere along the way. So I guess unless you can prove your windows partition is still there and intact, it doesn't make sense to keep trying. You'll just have to do a clean install. Most manufacturers will mail you a Windows CD if you ask for it.

He has not lost anything. He can [boot Windows](http://www.supergrubdisk.org/wiki/SGDWindowsMenu) or [Fix Boot of Windows](http://www.supergrubdisk.org/wiki/SGDWindowsMenu) with Super Grub Disk.

[Need a direct link](http://forjamari.linex.org/frs/download.php/924/super_grub_disk_0.9711.iso) or some [more downloads](http://www.supergrubdisk.org/)?

adrian15

---

### Post by Pokeh on 2008-04-25
Just posting to let you know that everything's sorted out now. That Super Grub thing worked fine.

Thanks for the help guys, you're a bunch of lifesavers.

---

### Post by priegog on 2008-04-25
Good to hear that :D

---

