---
title: "Expanding Wubi &quot;Partition&quot; Size"
date: 2007-09-07
forum: General Help
---

### Post by xm1014 on 2007-09-07
Is there any way to expand the size of your Wubi Virtual Disk? I only let Wubi use 4gb initially, but is there a way to expand this to, lets say 10 gb , without losing all of the data thats already in the Virtual Disk? I know that its not really a "Partition" so partition tools are already out of the question.

Thank you! :)

---

### Post by tuxcantfly on 2007-09-07
[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

If you're running out of room on /home, then use the "resizehome" option, otherwise, if you're running out of room on /, use the "resizeroot" option

---

### Post by lvleph on 2007-11-26
Sorry for my ignorance, and this may sound strange but bare with me.

I am unsure which I need to expand. What I want to do is install VMware, so that I can have a virtual Windows install. This is the final thing I want to do, before I trash my Windows partition. However, I want to do this first to make sure it works like I want. Anyway, I am unsure where the virtual install will be located at this point. I am inclined to believe it will be on the root file system. Is this correct?

---

### Post by mas_sergio on 2010-09-24
This is strictly Genious, I've never heard of it... im going to try this in a few weeks. I to was running out of space in my WUBI install this will let me keep my settings im so happy i dont have to reinstall just to get a larger partition. :) Thank you **_TUXCANTFLY_**! :guitar:

---

### Post by Sonic132 on 2010-11-10
Used LVPM to *transfer* Ubuntu from Wubi to an actual partition. Oddly enough it didn't ask where to mount the swap.
Anyway, now the computer wont boot to either Windows or Ubuntu.
It just hangs with a blinking cursor on black.
I was thinking I would try to fix grub or something. But I don't really know how. Anyone have any better suggestions?

---

### Post by bcbc on 2010-11-10
> **Sonic132 said:**
> Used LVPM to *transfer* Ubuntu from Wubi to an actual partition. Oddly enough it didn't ask where to mount the swap.
Anyway, now the computer wont boot to either Windows or Ubuntu.
It just hangs with a blinking cursor on black.
I was thinking I would try to fix grub or something. But I don't really know how. Anyone have any better suggestions?

Yes, 
This is fixable, but it helps to see what you've got so I can get the instuctions right. So boot a live CD and run the [bootinfoscript]("http://bootinfoscript.sourceforge.net") and post back.

If you want to get windows back, just install the windows bootloader. Or use lilo from a live CD as follows:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

---

### Post by Sonic132 on 2010-11-10
> **bcbc said:**
> Yes, 
This is fixable, but it helps to see what you've got so I can get the instuctions right. So boot a live CD and run the [bootinfoscript]("http://bootinfoscript.sourceforge.net") and post back.

If you want to get windows back, just install the windows bootloader. Or use lilo from a live CD as follows:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
That's the weird thing. It wont even boot off the Ubuntu Live CD either. I found that out after I posted my first message.
It hangs at the Ubuntu splash screen. I will boot from the Gparted Live CD but I doubt that'd help. Although it has terminal. It doesn't seem to have networking (I may be mistaken).
Also, how would I install the windows bootloader? I'd have to reinstall Windows again correct? Also, I'd want to get rid of Virtual Ubuntu and completely replace it with the *Has it's own partition* Ubuntu. I'm sorry. I wrote a lot of disorganized ideas.
Did that all make sense?

---

### Post by bcbc on 2010-11-10
> **Sonic132 said:**
> That's the weird thing. It wont even boot off the Ubuntu Live CD either. I found that out after I posted my first message.
It hangs at the Ubuntu splash screen. I will boot from the Gparted Live CD but I doubt that'd help. Although it has terminal. It doesn't seem to have networking (I may be mistaken).
Also, how would I install the windows bootloader? I'd have to reinstall Windows again correct? Also, I'd want to get rid of Virtual Ubuntu and completely replace it with the *Has it's own partition* Ubuntu. I'm sorry. I wrote a lot of disorganized ideas.
Did that all make sense?

You don't have to reinstall windows to replace the bootloader. Just boot a windows repair CD to a command line and run fixmbr (for xp) and bootrec.exe /fixmbr (for vista/7). 

Try to get the Ubuntu CD to boot - when you see the little keyboard icon in the bottom centre, press a key, then it will take you to a more advanced menu where you can try some boot workarounds by pressing the F6 key (try nomodeset if you have an nvidia card, for instance).

---

### Post by Sonic132 on 2010-11-12
Tried to use the WinXP Lite disk that we used to install it with. But it's so limited that it wouldn't work. So I tried our WinXP Pro x64 disk. It asked me for an administrator password. I don't have that. My idiot brother and his friend installed it.
So any way I could fix the mbr without the password. Also, is there a point? Because I turned on the laptop today and it actually works with Windows. But not Ubuntu. I guess there's a conflict or something.
Going to see what I can do with the Ubuntu disk. Wish me luck.

---

### Post by Sonic132 on 2010-11-12
Ok tried your suggestion of using the menu to modify the parameters on the live CD. But it still doesn't boot. Doesn't help that I don't know what any of them do.
Also, I did the disc checker function and it found an error in 1 file. To which Ubuntu declares with an exclamation mark. So it must be a good thing lol. I'm betting it's the squash filesystem file. I tied to make a USB bootable flash drive with that disc several times before the crash and it failed at that file every time.
What now? Anyway of modding mbr to include Ubuntu rather than fixing grub?

---

### Post by bcbc on 2010-11-12
if you can boot windows again, can you boot the Wubi install? That should still be operational. Run it and then post the result of the bootinfoscript.

---

