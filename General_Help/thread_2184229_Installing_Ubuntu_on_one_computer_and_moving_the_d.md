---
title: "Installing Ubuntu on one computer and moving the drive to another"
date: 2013-10-28
forum: General Help
---

### Post by jesus-freak on 2013-10-28
Hello,
Well, I have posted several times on the forum about a laptop that doesn't have a DVD drive anymore and I can't get to boot from a USB device. I've now come to the point where I MUST get a good clean install on this computer. I've been told that it is possible to take the hard drive out of the problem computer and place it in another machine, install Ubuntu and then place it back in the original machine. Is this a hard thing to do? I'm not talking about the actual removing discs, that is the easy part. But what exactly do you have to do once you install ubuntu on the drive in the second computer and then take it out and place it back in the first computer with different hardware? Is it a difficult process, is it automatic? Please, someone tell me what is involved. I was told back in my windows days that this was an easy task with windows, but every time I tried it, it was a disaster that never worked for me.

---

### Post by westie457 on 2013-10-28
> **jesus-freak said:**
> Hello,
Well, I have posted several times on the forum about a laptop that doesn't have a DVD drive anymore and I can't get to boot from a USB device. I've now come to the point where I MUST get a good clean install on this computer. I've been told that it is possible to take the hard drive out of the problem computer and place it in another machine, install Ubuntu and then place it back in the original machine. Is this a hard thing to do? I'm not talking about the actual removing discs, that is the easy part. But what exactly do you have to do once you install ubuntu on the drive in the second computer and then take it out and place it back in the first computer with different hardware? Is it a difficult process, is it automatic? Please, someone tell me what is involved. I was told back in my windows days that this was an easy task with windows, but every time I tried it, it was a disaster that never worked for me.
It is really that easy, plug and play, i think is the phrase.
The first boot might be a little slower as the kernel has to reconfigure itself to different hardware. That should be the only issue.

On a side-note, the main reason it does not work well with Windows is the change in hardware and Windows activation. Windows 'thinks' it has been installed to two computers which the terms of the EULA says is not allowed. You then have to go through hoops to get it re-activated.
None of those problems with an Ubuntu/Linux OS.

---

### Post by jesus-freak on 2013-10-28
Thanks!! That really encourages me!! Someone on here once said in response to the idea of doing this "You'll have to jump through a lot of hoops to make it work" so that is what has kept me from trying it to this point.

---

### Post by westie457 on 2013-10-28
If you install a 32-bit distro it should run on any machine architecture, the 64 -bit will only run on 64-bit machines.
Other issues might be the need to fix graphic card drivers and wireless network drivers. Those issues are covered in detail on these Forums.

---

### Post by sudodus on 2013-10-28
Feel free to ask even about what might seem to be small things, and there are several people around here to help you. I have done what you intend to do several times. I have even made an installation method, that takes advantage of the portability of Ubuntu, the [One Button Installer, 'OBI']("http://ubuntuforums.org/showthread.php?t=2172971")

---

### Post by jesus-freak on 2013-10-28
> **westie457 said:**
> If you install a 32-bit distro it should run on any machine architecture, the 64 -bit will only run on 64-bit machines.
Other issues might be the need to fix graphic card drivers and wireless network drivers. Those issues are covered in detail on these Forums.

So in regards to the graphics and wireless driver issues, what exactly would I search for on the forum to see how to do that? Can someone provide links to that information? I just need to know how to do everything before I start because I have to make sure this computer is up and fully functional in a very short time. Once I start this process I won't have time to play around with it or search for information after the fact. Our work depends on us both having functional computers, that is why I have been so hesitant to do it up until now.

---

### Post by warp99 on 2013-10-28
When you do the install on the first machine just make sure you do not install any proprietary modules (Nvidia, ATI, Intel, etc...), use only the open source versions. Once the install is completed and working properly do the following:

```
sudo rm /etc/udev/rules.d/*.rules
```

Shut it down, take the drive out and re-install the drive into the target computer. After booting you can install any proprietary modules you may need. I've upgraded all of my computers for the past 8 years with this method. It's so easy in Linux to do this.

---

### Post by jesus-freak on 2013-10-29
On my computer and my wife's computer we never need to install any graphics drivers or wireless drivers.  The defaults that are used when Ubuntu first installs work fine for both of ours. So that is okay? Just after install I run that code and then shut down and switch the drives back? Sounds easy enough :) Thanks!

---

### Post by sudodus on 2013-10-29
With the built-in drivers Ubuntu is portable to other computers where the built in drivers also work.

If you want to be are sure as can be without really testing, you can let us know about the hardware in the target computer

- Brand name and model
- CPU, RAM (size), graphics chip/card, wifi chip/card

And you can ***backup*** your present system (clone it or make an image), that you can restore from, if something goes wrong or does not work in spite of all the preparations.

---

### Post by jesus-freak on 2013-10-30
Here are the specs for the target computer 

[http://www.cnet.com/laptops/toshiba-satellite-a305d-s6848/4507-3121_7-33088925.html](http://www.cnet.com/laptops/toshiba-satellite-a305d-s6848/4507-3121_7-33088925.html)

The video card is an issue as there are no great drivers for it but Ubuntu installs the best one possible automatically. The video card didn't run well on 13.04 64 bit but just for the heck of it I ran the upgrade to 13.10. During the install there was an error. It restarted and I opened synaptic. It found some broken packages and I fixed them and ran a bunch of updates. Everything says that it is a full 13.10 install. When I can get it to run right 13.10 out performs 13.04 massively on this computer. Unfortunately it's hard to get it to run correctly, probably because of the error installing. It's pretty hit and miss with it missing most of the time. So I downloaded the 32 bit versions on 13.10, 13.04 and 12.04. I will install one and if  it won't work, I'll move on to the next. Like I said, once I start I have to be able to finish this thing in one go so I'm doing everything to get ready.

All files are backed up but I didn't make a clone of the system because it's a mess.

---

### Post by sudodus on 2013-10-30
Yes, there are known issues with the ATI Mobility RADEON processors. Otherwise I have good experiences with Toshiba computers and linux.

You might succeed with 12.04 LTS, and in that case I suggest that you keep that system instead of trying to get the latest and greatest, because sometimes support for middle-aged and old hardware is dropped or incomplete in new versions. (Edit: I would say that your computer is middle-aged.)

If you feel that Ubuntu with Unity is slow, you can try some other desktop environment. The Ubuntu flavours ***Lubuntu*** with LXDE and ***Xubuntu*** with XFCE have desktop environments (LXDE and XFCE) with smaller foot-prints, and they work better if there is not enough horsepower for Unity of standard Ubuntu or KDE of Kubuntu.

If you like gnome, you can also try [https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)

---

### Post by jesus-freak on 2013-10-31
Okay, I have one more question before I do this. During install it gives two options "install third party software" and "Run update during install" Should I select either of these or not. Someone earlier said not to install extra graphics or wireless drivers until you place the drive back in it's original computer. I didn't know if selecting these options might automatically do just that and place drivers on it that I will have to fight with later. Thanks so much everyone for your help!!

---

### Post by sudodus on 2013-10-31
I don't think "install third party software" and "Run update during install" will install any extra  graphics or wireless drivers for you. It is a matter of choice. Some people think it is convenient to do as much as possible at once during the installation, so people want a simple installation and add software afterwards.

So if I should suggest something: It is easier to get something that works without "install third party software" and "Run update during install". Then you can add what you need for best performance playing multimedia and make the system up to date afterwards.

---

### Post by warp99 on 2013-10-31
I would install those components after you move the drive to the new computer to reduce less variables. That would be my suggestion.

---

