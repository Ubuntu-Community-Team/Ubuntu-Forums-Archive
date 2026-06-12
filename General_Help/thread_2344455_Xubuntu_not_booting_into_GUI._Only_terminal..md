---
title: "Xubuntu not booting into GUI. Only terminal."
date: 2016-11-25
forum: General Help
---

### Post by laggger164 on 2016-11-25
So I have installed Xubuntu on a USB flash drive as I wanted some personal portable OS that I can plug into any computer and work on some lighter things like text editing and stuff. Just something I can have with me on an environment I am familiar with.

It has so far worked quite well, I tested it on 4 machines so far, one machine had Windows 8 with UEFI and I wasnt really able to boot into it because it didnt show up in the boot menu, but a topic about that is already going and I will test a few things before asking any more.

So the problem is that whenever I boot into a different computer than mine and then boot into my computer, it wont boot normally into a GUI, just a terminal interface (please correct me with the appropriate term for this). I log in and everything seems to work.
I figured out that the problem is most likely my second GPU from AMD (HD7750) that I am not using right now, but I was using it when doing virtualization. Pretty awesome stuff actually.

When I take out that GPU and boot into Xubuntu, it works normally. When I shut it down, put the GPU back into the PCIe slot, it works as it should. But again, if I boot from that USB stick on any other computer it works fine, but then I boot into my main PC, it is the same thing again. Terminal only.

I was wondering if I could set something in Grub, or anything that can solve this, since I dont feel like taking the GPU out and back in every time I want to do stuff.

Thank you so much for any and all help that you can give me!

---

### Post by sudodus on 2016-11-25
If you want a portable USB pendrive with an ***installed*** system, you should avoid proprietary drivers, and I think you need a proprietary driver (or at least some special tweak) when you use that second GPU. This is a problem, that can only be solved by removing either the second GPU or the driver/tweak for it. It is probably easier to add/remove software than hardware.

- Have you tried how it works with a live system (not installed)?

- Would it be enough with a boot option (which can be used both in a live system and an installed system)?

---

### Post by laggger164 on 2016-11-25
> **sudodus said:**
> If you want a portable USB pendrive with an ***installed*** system, you should avoid proprietary drivers, and I think you need a proprietary driver (or at least some special tweak) when you use that second GPU. This is a problem, that can only be solved by removing either the second GPU or the driver/tweak for it. It is probably easier to add/remove software than hardware.

- Have you tried how it works with a live system (not installed)?

- Would it be enough with a boot option (which can be used both in a live system and an installed system)?

I do not have proprietary drivers installed for the second AMD GPU, just for my main primary Nvidia GTX 960, which works really well.

I will try to install a live system, but I don't know...

---

### Post by sudodus on 2016-11-25
- Does the pendrive that works with your main primary Nvidia GTX 960 also work with the other computers? (Or is it another pendrive?)

- Is the second GPU also an Nvidia chip (but another model)?

---

### Post by laggger164 on 2016-11-26
> **sudodus said:**
> - Does the pendrive that works with your main primary Nvidia GTX 960 also work with the other computers? (Or is it another pendrive?)

- Is the second GPU also an Nvidia chip (but another model)?
 Alright then, I will clarify it for you:

My main GPU, the first one is an Nvidia GTX 960 with an Nvidia chip. Proprietary drivers installed via Additional drivers program.
My Second GPU is the AMD HD7750 which is an AMD chip. No proprietary drivers installed for that one.
Other computers that I used with the same USB stick are working no problem. I am not installing any proprietary drivers whatsoever.

It is still the same USB Flash drive.

---

### Post by sudodus on 2016-11-26
I see. The proprietary driver Nvidia GTX 960 can create problems in other computers, if it is selected for a graphics card/chip, that does not work with it. I don't know how the system manages a setup with two different kinds of graphic cards, where one of them needs a proprietary driver, and I am afraid, that I cannot help much more than pointing to this problem.

There are other people here, who use advanced systems with more than one graphics card. Let us hope that they will see this thread, and chip in to help you :-)

---

### Post by laggger164 on 2016-11-27
> **sudodus said:**
> I see. The proprietary driver Nvidia GTX 960 can create problems in other computers, if it is selected for a graphics card/chip, that does not work with it. I don't know how the system manages a setup with two different kinds of graphic cards, where one of them needs a proprietary driver, and I am afraid, that I cannot help much more than pointing to this problem.

There are other people here, who use advanced systems with more than one graphics card. Let us hope that they will see this thread, and chip in to help you :-)

I am not using the second GPU on my Xubuntu USB stick at all. It most likely does need a proprietary driver tho.
I was thinking that maybe if I would install the proprietary driver for that second GPU too, maybe it would work? (questionmark=?)

---

### Post by oldfred on 2016-11-27
I have this in my notes, but now very old. Not sure it would work. Link is to post back in 2009.
They have been trying to do away with xorg.cong, so that may not work either.

 Create Portable Ubuntu for 2 different Video Cards - script
[http://ubuntuforums.org/showthread.php?p=8107778](http://ubuntuforums.org/showthread.php?p=8107778)
There is a application named switchconf that lets you choose between xorg.conf files at boot.
[http://meandubuntu.wordpress.com/2008/05/07/changing-system-configuration-switchconf/](http://meandubuntu.wordpress.com/2008/05/07/changing-system-configuration-switchconf/)

---

### Post by laggger164 on 2016-11-29
> **sudodus said:**
> I see. The proprietary driver Nvidia GTX 960 can create problems in other computers, if it is selected for a graphics card/chip, that does not work with it. I don't know how the system manages a setup with two different kinds of graphic cards, where one of them needs a proprietary driver, and I am afraid, that I cannot help much more than pointing to this problem.

There are other people here, who use advanced systems with more than one graphics card. Let us hope that they will see this thread, and chip in to help you :-)

So I was thinking I would make a USB stick bootable into 2 OSes with 64-bit and a 32-bit OS according to your guide (thanks BTW, much appreciated!)

But I would like it encrypted, so nobody can mess with mah stuff! I don't see you mentioning anything like that in your guide. Is it even possible?

Also, I can normally install programs, take it out, boot with another PC and use those programs normally right? And can I use Xubuntu instead of Ubuntu?

Thank you so much for all the help!

---

### Post by sudodus on 2016-11-29
If you use my already prepared systems (in compressed image files), you cannot get 'encrypted disk', but you can create a new user with encrypted home, which might be good enough.

Yes, it should work like that. If you want another desktop environment, I suggest that you start from a mini system and add it (for example the package xubuntu-desktop rather than trying to mix it with an already installed desktop environment.

---

### Post by laggger164 on 2016-11-29
> **sudodus said:**
> If you use my already prepared systems (in compressed image files), you cannot get 'encrypted disk', but you can create a new user with encrypted home, which might be good enough.

Yes, it should work like that. If you want another desktop environment, I suggest that you start from a mini system and add it (for example the package xubuntu-desktop rather than trying to mix it with an already installed desktop environment.

Yup! Encrypted Home will do, I got no real hackers in a 30Km radius anyways XD.

So... you're saying that I should just add XCFE to your Ubuntu image? Or am I getting confused here?

---

### Post by sudodus on 2016-11-29
It depends which image you have (I have uploaded many images).

- ***If you have a mini-system with only a text screen, you can install xubuntu-desktop.***

- I have mixed Xubuntu and Lubuntu, and it works rather well for me, but other people say that you should definitely ***not*** mix two desktop environment.

- If you have a system with standard Ubuntu with the Unity desktop environment, you should ***not*** install xubuntu-desktop.

---

### Post by laggger164 on 2016-11-30
> **sudodus said:**
> It depends which image you have (I have uploaded many images).

- ***If you have a mini-system with only a text screen, you can install xubuntu-desktop.***

- I have mixed Xubuntu and Lubuntu, and it works rather well for me, but other people say that you should definitely ***not*** mix two desktop environment.

- If you have a system with standard Ubuntu with the Unity desktop environment, you should ***not*** install xubuntu-desktop.

Just to be clear, I was talking about this guide in particular: [https://ubuntuforums.org/showthread.php?t=2259682](https://ubuntuforums.org/showthread.php?t=2259682)

It's still relevant right? Also, can I update anything when using those iso images?

---

### Post by sudodus on 2016-11-30
It is probably best to start with current versions of the iso files, rather than getting an image file which contains old iso files.

For example, [post #8 in that thread, 'Build your own single boot or multiboot pendrive for all PC (Intel/AMD) computers'](http://ubuntuforums.org/showthread.php?t=2259682&p=13302278#post13302278) shows how you can build your system, and you should grab current iso files (16.04.1 LTS and 16.10 when this post is written).

---

### Post by laggger164 on 2016-11-30
> **sudodus said:**
> It is probably best to start with current versions of the iso files, rather than getting an image file which contains old iso files.

For example, [post #8 in that thread, 'Build your own single boot or multiboot pendrive for all PC (Intel/AMD) computers'](http://ubuntuforums.org/showthread.php?t=2259682&p=13302278#post13302278) shows how you can build your system, and you should grab current iso files (16.04.1 LTS and 16.10 when this post is written).

Will do! I will reply when I try it, thanks! 

Also, do you live in Europe too? Anytime I ask something, you reply in an hour. Seems too awesome to me!

---

### Post by sudodus on 2016-11-30
In Sweden :-)

---

### Post by laggger164 on 2016-11-30
> **sudodus said:**
> In Sweden :-)

Slovakia here!

---

