---
title: "Hello, I'm a new switcher..."
date: 2008-04-24
forum: General Help
---

### Post by LolItsGriff on 2008-04-24
Hi there. First, some getting to knowing..

My name is Griffin, I'm a 15 year old and I enjoy using my computer a lot. I've always though linux was cool (when I was introduced to it by my friends brother, who used Gentoo. This was when I was about 10 I think..)

I thought it would be cool to make the jump to linux Now. I've waited quite a while, and I just got a new computer. I'm running Vista SP1 as I type this.


Anyway, I was wondering, as a first time user, What should I expect, and what are some things I'm going to have to do/learn to make my linux experience as fun as possible?

Thanks for all the help, before hand. I also apologize if this doesn't belong here!

---

### Post by jpeddicord on 2008-04-24
What to expect? Something new. A completely different experience from Windows. There are tons and tons of features and differences in Ubuntu that make it unique, even among Linux distributions. All I can say is give it a try, and don't be afraid to ask questions.

You might hit some snags along the way, but just keep trying and it will all work out.

:)

---

### Post by LolItsGriff on 2008-04-24
! sweet, A quick replyer!

This might seem like a bizarre question, but it just popped into my head as I was waiting for a reply.

Am I going to have to do a bunch of fancy computing to get my internet connection to work and such? I'm wired through broadband and such.

---

### Post by jpeddicord on 2008-04-24
> **LolItsGriff said:**
> ! sweet, A quick replyer!

This might seem like a bizarre question, but it just popped into my head as I was waiting for a reply.

Am I going to have to do a bunch of fancy computing to get my internet connection to work and such? I'm wired through broadband and such.

If you're wired in? Nah, that should be plug in play, unless you have some bizarre network configuration. :)

---

### Post by oboedad55 on 2008-04-24
> **LolItsGriff said:**
> ! sweet, A quick replyer!

This might seem like a bizarre question, but it just popped into my head as I was waiting for a reply.

Am I going to have to do a bunch of fancy computing to get my internet connection to work and such? I'm wired through broadband and such.

The best thing to do is download the latest .iso and burn a CD. You can boot from the CD without installing anything and get an idea of what you're in for. If you decide to install it we can tell you how to dual boot, if that's your choice.

Cheers,

---

### Post by LolItsGriff on 2008-04-24
Alrighty. thanks.


I've already began installing. I've booted from a CD for the last Ubuntu distro.. But I was on a wireless network using a really old computer. It was quite a while ago and the computer kinda didn't work halfway through it.

Just an FYI I'm installing using Wubi. I should be using that installer, right?

---

### Post by jpeddicord on 2008-04-24
> **LolItsGriff said:**
> Alrighty. thanks.


I've already began installing. I've booted from a CD for the last Ubuntu distro.. But I was on a wireless network using a really old computer. It was quite a while ago and the computer kinda didn't work halfway through it.

Just an FYI I'm installing using Wubi. I should be using that installer, right?

You *can* install using Wubi, but it is not the recommended installer if you want the full setup. Wubi, while easier, will not provide the full speed a standard install will.

The standard way to install is to boot directly from the CD, and open the installer from the live Ubuntu desktop.

---

### Post by LolItsGriff on 2008-04-24
> **jacobmp92 said:**
> You *can* install using Wubi, but it is not the recommended installer if you want the full setup. Wubi, while easier, will not provide the full speed a standard install will.

The standard way to install is to boot directly from the CD, and open the installer from the live Ubuntu desktop.

Aah, Okay.

is there any like.. Partitioning I need to do for that or such?

---

### Post by Tyke91 on 2008-04-24
it depends on whether you want a dual boot or a single boot install of ubuntu.

dual boot will require only a little bit of partitioning and single will require none at all.

single - just select *guided - use entire disk*

dual boot is best to go into manual, if you don't want to use manual so much, shrink your windows partition down, select *keep changes to partitions* and then go back to guided and this time use *guided - use largest contiguous free space*

  f you just want to manually set up a dual boot, go to manual and do this

-shrink your windows partition
-create a new partition, make it an extended one
-create 3 logical partitions inside of this extended one
---partition 1 should be mounted as " / "  also known as root. it should be 10-20 gigs, depending on how much space you have
---partition 2 should be mounted as swap, it should be 2x your ram
---partition 3 should be mounted as /home, it should be the rest of your free space. this is where you will keep all your personal files, music, videos, documents... etc.

---

### Post by LolItsGriff on 2008-04-24
> **Tyke91 said:**
> it depends on whether you want a dual boot or a single boot install of ubuntu.

dual boot will require only a little bit of partitioning and single will require none at all.

single - just select *guided - use entire disk*

dual boot is best to go into manual, if you don't want to use manual so much, shrink your windows partition down, select *keep changes to partitions* and then go back to guided and this time use *guided - use largest contiguous free space*

  f you just want to manually set up a dual boot, go to manual and do this

-shrink your windows partition
-create a new partition, make it an extended one
-create 3 logical partitions inside of this extended one
---partition 1 should be mounted as " / "  also known as root. it should be 10-20 gigs, depending on how much space you have
---partition 2 should be mounted as swap, it should be 2x your ram
---partition 3 should be mounted as /home, it should be the rest of your free space. this is where you will keep all your personal files, music, videos, documents... etc.

What exactly is Manual and such?

I really kinda want to get rid of my windows partition and stuff.

like, a freeswipe of my computer. o-o. Not quite positive w/ all this tech knowledge.

---

### Post by zach382 on 2008-04-24
One tip I'd reccomend if you decide to go the partitioning route is to do the partitioning inside windows vista. I had problems resizing a vista partion with the ubuntu installer. In vista click the start "orb" go to computer right click "manage" and then look for the disk management section on the side I believe. From there you can shrink windows partition and just leave it as free space. Then when you use the ubuntu installer you can select the "use largest continuous free space" option which makes things one step simpler.

Edit: PM if you need any more info about the vista partitioning. I dont know if I missed a step in there as I am in ubuntu at the moment and giving instructions from memory. :D

---

### Post by natrixgli on 2008-04-24
Hi,

If you want to start fresh, it's easiest. When you get to the partitioning step, you just select "guided - use entire disk" and away you go.

THIS WILL, of course ERASE ALL YOUR STUFF. 

But if you have all your important secret space plans, CIA dossiers, and mp3's of The Arcade Fire and Barry Manilow backed up, it's all good - go nuts.

As for doing a dual boot, make sure you fully shut down Windows, not hibernate or suspend... And also might be worth doing a defrag first. Ubuntu's installer will figure out how much you can shrink your partition.

-n8

---

### Post by neodude237 on 2008-04-24
I just dual booted myself, and I am enjoying it, lots! It is very much like Mac and Windows after you get any driver issues sorted, which, with some forum help and searching is quite easy! Many programs will work under Wine, and many of my favorite programs already have a Linux version to start! So, you will definetly love it, and it has worked very nicely for me, as I just upgraded to Gusty, and I did a clean dual boot with Hardy today, and am now trying to get the updates, but the server is very busy :X

---

### Post by LolItsGriff on 2008-04-24
Sweet, thank you all for the help!

Sorry if this reply was wicked late... I've been playing xbox. Someway or another I gotta support microsoft!

Cool. This is gonna be great.

---

### Post by mk_kano on 2008-04-24
Just select use entire disk if you want to kill Vista. This will basically reformat and install Ubuntu. I just switched myself and Ubuntu runs clean and fast even on my prehistoric laptop.

---

### Post by LolItsGriff on 2008-04-24
> **mk_kano said:**
> Just select use entire disk if you want to kill Vista. This will basically reformat and install Ubuntu. I just switched myself and Ubuntu runs clean and fast even on my prehistoric laptop.

Aah, Okay.

---

### Post by LolItsGriff on 2008-04-24
Alright, I'm going for the install right now.

I'll be back in a while :3

may the force be with me o-o

---

### Post by LolItsGriff on 2008-04-24
alrighty, so I'm booting from the CD and I like what I'm seeing.

but I have one question...

is there anyway to restore my windows Screen resolution. I have to scroll a lot more here in linux than I did in windows.. I think my resolution was...1366x768 (I'm running a widescreen monitor)

EDIT: also, I like to Call my Girlfriend using Skype.. but when I tried to use my mic w/ soundcapture, it didn't pick up anything from any inputs.

what should I do?

---

### Post by natrixgli on 2008-04-24
1) After you install, you will probably need to use the 'restricted drivers manager' to install drivers for your video card, if your video card is NVidia or ATI.

2) Skype is available and you should be able to get sound working once you install and tinker a bit, with some help from these forums. 


OR you could always get the girlfriend to switch too, then you can both use Ekiga ;)

Cheers,

-n8

---

### Post by LolItsGriff on 2008-04-24
> **natrixgli said:**
> 1) After you install, you will probably need to use the 'restricted drivers manager' to install drivers for your video card, if your video card is NVidia or ATI.

2) Skype is available and you should be able to get sound working once you install and tinker a bit, with some help from these forums. 


OR you could always get the girlfriend to switch too, then you can both use Ekiga ;)

Cheers,

-n8
Haha. Thanks for the help. I'm going to run the fullinstall now, and if anything goes wrong, atleast I learned something, and I can just re-install windows w/ my vista CD

alrighty guys. Here I go.

---

### Post by masticate on 2008-04-25
Hi =)

Linux takes some getting used to; so don't let the learning curve scare you. It's a fun journey. When I first started to learn linux, I was so confused. I asked questions for every little problem I had. So be sure to do the same if you get lost. =)


You probably don't have the restricted drivers enabled. 
> System -> Administration -> Hardware Drivers This lets you enable your proprietary video card driver. Make sure it's enabled and in use (green icon).



Next, open up your Package Manager:
> System -> Administration -> Synaptic Package Manager
[LIST=1]
[*]In Options -> Repositories, 
[LIST]
[*]enable all check boxes in the "Third-Party Software" tab.
[*]Make sure at least the first four check boxes are checked in "Ubuntu Software" tab.
[*]Click "Close".
[/LIST]
[*]Click "Reload".
[*] If you have nvidia,
[LIST]
[*]search for 'nvidia-settings'
[*]right click on it and mark for install
[*]click Apply.
[*]Application -> Accessories -> Terminal
[LIST]
[*]type in 'sudo nvidia-settings'. it will prompt u for your password
[*]click on 'X Server Display Configuration'
[*]set your resolution
[*]click apply
[*]click 'save to x configuration file'
[*]quit
[/LIST]
[/LIST]
[*] If you have ati, i don't know b/c I have never used ati. sorry.
[/LIST]

---

### Post by LolItsGriff on 2008-04-25
Not positive how to get to the Third party software part.. .I might be missing something. But i used the xrandr command earlier and it seemed that my resolution was the same as before o-o

---

### Post by LolItsGriff on 2008-04-25
Ooh! new question!

what is the deal with tar.gz files?

I'm trying to download flashplayer, for youtube and niconicodouga, and I just dunno how to run it o-o

Do I extract it? :3

---

### Post by ubuntu27 on 2008-04-25
> **LolItsGriff said:**
> Ooh! new question!

what is the deal with tar.gz files?

I'm trying to download flashplayer, for youtube and niconicodouga, and I just dunno how to run it o-o

Do I extract it? :3

You can download Adobe's Flash Player using Synaptic package Manager. Or using the terminal. 

Go to Applications menu/Accessories/Terminal
And then type (You can copy and paste) the following command:

```
sudo apt-get install ubuntu-restricted-extras
```

That will download and install codecs such as mpeg, avi, wmv, mp3, and stuff such as Flash Player and Sun's Java.

For more information go to

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by LolItsGriff on 2008-04-25
> **ubuntu27 said:**
> You can download Adobe's Flash Player using Synaptic package Manager. Or using the terminal. 

Go to Applications menu/Accessories/Terminal
And then type (You can copy and paste) the following command:

```
sudo apt-get install ubuntu-restricted-extras
```

That will download and install codecs such as mpeg, avi, wmv, mp3, and stuff such as Flash Player and Sun's Java.

For more information go to

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Ooh, thanks.

I'm having another problem though. It's still not recognizing my microphone.

I have a GE full headset, and It's plugged into the microphone port out back. All of Skype's input options have been tried with no luck. I've also enabled all captures in the volume thing. I also tried the alsamixer w/ my terminal with no luck.

On the good side, they work fine as headphones!

---

### Post by natrixgli on 2008-04-25
EDIT: Duh, I should have read more carefully...

In the volume control, did you go to File > Change Device and look for a capture device? Also if you go to Edit > Preferences there are checkboxes to display additional options.


Give that a whirl.

---

### Post by LolItsGriff on 2008-04-25
> **natrixgli said:**
> EDIT: Duh, I should have read more carefully...

In the volume control, did you go to File > Change Device and look for a capture device? Also if you go to Edit > Preferences there are checkboxes to display additional options.


Give that a whirl.

Yeah, I've added them all and tried unmuting them..

I'm confused though. I went to the volume control preferences and it gave me my old audio codec (sigmatel)

Not positive how to work it

---

