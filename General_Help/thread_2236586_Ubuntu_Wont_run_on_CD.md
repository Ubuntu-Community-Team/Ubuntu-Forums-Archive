---
title: "Ubuntu Wont run on CD"
date: 2014-07-27
forum: General Help
---

### Post by daniell59 on 2014-07-27
I am trying to run Ubuntu off of a CD on my wife's computer. I have tried both 12.04 and 14.04. They both will not run. I have no trouble running them on my computer.
The specs on her computer include AMD Athlon 64 X 2 Dual Core processor 4400+ 1.87 GB RAM

Her present OS is Windows XP. I would eventually want to dual boot it with Ubuntu.

Any suggestions will be appreciated.

---

### Post by buzzingrobot on 2014-07-27
> **daniell59 said:**
> I am trying to run Ubuntu off of a CD on my wife's computer. I have tried both 12.04 and 14.04. They both will not run...


Do they boot at all?  If so, what do you see on screen before they stop?

Also, what video card is in the machine?

---

### Post by daniell59 on 2014-07-27
I should have included the fact that it is a Biostar Motherboard. I googled it and found that there are others with the same problem.

---

### Post by yancek on 2014-07-27
You really need to post more information to get help.  Saying it will not run doesn't give us much to work with.  Specifically, what happens when you boot?  Do you get a black screen?  a black screen with a blinking cursor?  get to a Desktop but can't install, lots of possibilities.

---

### Post by daniell59 on 2014-07-28
> **buzzingrobot said:**
> Do they boot at all?  If so, what do you see on screen before they stop?

Also, what video card is in the machine?

Yes they both booted up to the point that I select the language. Perhaps a little further. For a moment I saw the arrow, then I got a blank screen with distorted colors.

The video card is built into the motherboard.

Thanks for your input.

---

### Post by daniell59 on 2014-07-28
I emailed the MB manufacture and received the following reply.

We do not provide direct support for Linux since there are many versions out there but we are aware that customers do use Linux based OS with this model

So why does the one I am working on not function with Ubuntu?

Maybe I should try adding a video card.

---

### Post by coffeecat on 2014-07-28
> **daniell59 said:**
> 
The video card is built into the motherboard.


Yes, and what is it? The actual chipset might help in pinpointing the problem.

---

### Post by daniell59 on 2014-07-28
> **coffeecat said:**
> Yes, and what is it? The actual chipset might help in pinpointing the problem.

Can I determine the chipset without examining the MB?

---

### Post by mörgæs on 2014-07-28
Booting from a CD is often troublesome. Better to use a USB stick if your BIOS supports it.

---

### Post by coffeecat on 2014-07-28
> **daniell59 said:**
> Can I determine the chipset without examining the MB?

You have Windows XP installed? Simply have a look under display adapters in the device manager.

[http://support.microsoft.com/kb/283658](http://support.microsoft.com/kb/283658)

```
To access Device Manager, use any of the following methods:

    Click Start, click Run, and then type devmgmt.msc.
    Right-click My Computer, click Manage, and then click Device Manager.
    Right-click My Computer, click Properties, click the Hardware tab, and then click Device Manager.
    Type the following command at a command prompt:
        start devmgmt.msc
```

---

### Post by daniell59 on 2014-07-28
> **coffeecat said:**
> You have Windows XP installed? Simply have a look under display adapters in the device manager.

[http://support.microsoft.com/kb/283658](http://support.microsoft.com/kb/283658)

```
To access Device Manager, use any of the following methods:

    Click Start, click Run, and then type devmgmt.msc.
    Right-click My Computer, click Manage, and then click Device Manager.
    Right-click My Computer, click Properties, click the Hardware tab, and then click Device Manager.
    Type the following command at a command prompt:
        start devmgmt.msc
```

Thanks

---

### Post by daniell59 on 2014-07-28
Nvidia chipset

NVIDIA GeForce 6150 / nforce430a

 Do you think that this is the problem?

---

### Post by coffeecat on 2014-07-28
> **daniell59 said:**
> Nvidia chipset

NVIDIA GeForce 6150 / nforce430a

 Do you think that this is the problem?

That's quite an old GPU which I haven't used for years, so I have no experience of it with recent releases of Ubuntu. That being said, it's worth trying the "nomodeset" boot option, particularly as you are seeing a blank screen on bootup. This is somewhat old, but have a look here:

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Look at the bit under nomodeset, and then for the live CD session, scroll down to "How to enable kernel options on the livecd (before install)". Take note of what it says about this kernel option only being temporary for one live session. 

Earlier, you mentioned adding a video card. Do you have one spare to use? If so, what is it?

---

### Post by daniell59 on 2014-07-28
Earlier, you mentioned adding a video card. Do you have one spare to use? If so, what is it?[/QUOTE]

Radeon X550 256MB

---

### Post by coffeecat on 2014-07-28
> **daniell59 said:**
> 
Radeon X550 256MB

Hmm -  that's a similar vintage to the nvidia 6150, perhaps even earlier. If it's convenient to fit it to your motherboard, then it is worth trying to see if you can actually boot up the live CD. But whichever you use, I think Ubuntu with Unity is going to be too heavy and graphics intensive for those old graphics cards. By all means try the Unity version of Ubuntu, but you might find it too sluggish even if you do manage to boot it to a live desktop.

Lubuntu - [http://lubuntu.net/](http://lubuntu.net/) - or Xubuntu - [http://xubuntu.org/](http://xubuntu.org/) - are lighter alternatives. Your CPU is capable enough, and you have sufficient RAM for Ubuntu, but if I were in your situation, I would prepare both Lubuntu and Xubuntu CDs and try each of the three variants of Ubuntu with both video cards. I think you will get the same blank screen problem in Lubuntu and Xubuntu with the nvidia card, unless you use the nomodeset option, but try them all out. Bear in mind that a live session will be slower than an installed operating system, but trying all those variations may give you a good idea what is best to install on the machine, and with which video card.

---

### Post by daniell59 on 2014-07-28
> **coffeecat said:**
> Hmm -  that's a similar vintage to the nvidia 6150, perhaps even earlier. If it's convenient to fit it to your motherboard, then it is worth trying to see if you can actually boot up the live CD. But whichever you use, I think Ubuntu with Unity is going to be too heavy and graphics intensive for those old graphics cards. By all means try the Unity version of Ubuntu, but you might find it too sluggish even if you do manage to boot it to a live desktop.

Lubuntu - [http://lubuntu.net/](http://lubuntu.net/) - or Xubuntu - [http://xubuntu.org/](http://xubuntu.org/) - are lighter alternatives. Your CPU is capable enough, and you have sufficient RAM for Ubuntu, but if I were in your situation, I would prepare both Lubuntu and Xubuntu CDs and try each of the three variants of Ubuntu with both video cards. I think you will get the same blank screen problem in Lubuntu and Xubuntu with the nvidia card, unless you use the nomodeset option, but try them all out. Bear in mind that a live session will be slower than an installed operating system, but trying all those variations may give you a good idea what is best to install on the machine, and with which video card.

Thank you for your informative reply.
Perhaps it would be better to build my wife a new computer. I have not built one in quite a few years. I am not familair with the new components.
Her present computer with XP is working reasonably well. I am concerned that it is not secure.

---

### Post by coffeecat on 2014-07-28
> **daniell59 said:**
> 
Her present computer with XP is working reasonably well. I am concerned that it is not secure.

That's a valid concern, since XP is no longer supported. If you wish to give that hardware a new lease of life, then one of the combinations I suggested will hopefully work. Rather than jump in with all six, and considering the blank screen problem with the onboard nvidia graphics, why not try Lubuntu 14.04 with the Radeon card?

---

### Post by daniell59 on 2014-07-29
I was able to run Lubuntu off of the CD using the onboard video card. I must say however, I like the look of Ubuntu better. If I add an updated video card to the MB, do you think that I will be able to run Ubuntu?

---

### Post by coffeecat on 2014-07-29
> **daniell59 said:**
> I was able to run Lubuntu off of the CD using the onboard video card. I must say however, I like the look of Ubuntu better. If I add an updated video card to the MB, do you think that I will be able to run Ubuntu?

To be honest, I'm not sure. I used to use your AMD CPU a few years ago, and it was capable of running Ubuntu with compiz with an adequate video card, but I think that was before Unity. Unity has a reputation for being graphics heavy, but I don't know how much of this is attributable to compiz or to Unity itself. There's a lot of unreasonable anti-Unity prejudice around, even on this forum, so it's worth taking some of the "Unity is too heavy" comments with caution.

If it's any help, I'm using an AMD card - Radeon HD6450 - with the default open source driver, and it has no problems at all running Ubuntu with Unity. I simply don't bother even thinking about the proprietary AMD driver. Whether you can still get that card on an adapter which your motherboard has, I don't know. Your motherboard is a few years old. Does it have an AGP or PCIe slot for a video card?

---

### Post by daniell59 on 2014-07-29
Your motherboard is a few years old. Does it have an AGP or PCIe slot for a video card?[/QUOTE]

It has a PCIe slot.

---

### Post by coffeecat on 2014-07-29
A couple of UK suppliers are still selling Radeon HD 6450 PCIe cards so I'm sure that would be the case for where you are. I'm not suggesting you do get a HD6450 - I'm merely saying that it works for me, and others may have better suggestions for your particular motherboard. You do need to be sure that you buy one with the correct connector for the slot in your motherboard. The wikipedia page has more details on the different slots and cross-compatibility:

[http://en.wikipedia.org/wiki/PCI_Express#Form_factors](http://en.wikipedia.org/wiki/PCI_Express#Form_factors)

---

### Post by daniell59 on 2014-07-29
Thanks, I am in the US. I will look into it.

---

### Post by daniell59 on 2014-08-02
This morning I installed the old Video card that I had laying around. I was able to run Ubuntu 14.04 32 off of the DVD.

I then booted into Windows still attached to the installed video card. The mouse lit up, but the cursor would not respond. Next I rebooted into windows using the built in video card. No video output. I then removed the video card and tried again. For a while the cursor would not respond. A short time later it returned to normal.
I have some questions.

1. How can I install drivers for the Video card if I do not have a functional mouse?

2. If a video card is in the machine not connected, could it affect the workings of the computer?[/SIZE]

---

### Post by daniell59 on 2014-08-02
I think that I may have figured it out. I need to go into the BIOS and disable the onboard video card. But at least I know that it will now run Ubuntu 14.04.

---

