---
title: "[Lubuntu] Frozen on live boot"
date: 2016-02-02
forum: General Help
---

### Post by ken71 on 2016-02-02
Old pc, trying to run it with a Lubuntu Live usb (Pentium D 805 with 1.5GB RAM). It prevously ran WinXP fine, then sat around for a long time. Now I try to boot Lubuntu 15.10 64-bit, but it freezes after it loads the DE. Mouse/keyboard stop working, but the clock keeps ticking.

I ran the checkdisk and it says 2 errors every time, even though I can run the live USB on my main pc. I rewrote it with both Pendrivelinux & rufus, and even tried the LTS with the same problems (and 2 errors again).

Memtest returns no errors, just checkdisk. What now?

---

### Post by sudodus on 2016-02-02
Welcome to the Ubuntu Forums :-)

Since your main computer can boot and run Lubuntu from the pendrive, I think it is good. The problem is to make it cooperate with this old computer. Maybe your computer cannot run a 64-bit operating system. You might try a 32-bit version of Lubuntu. I would recommend that you try the version 14.04.[COLOR="#FF0000"]**1**[/COLOR] LTS (and make it up to date after installing)

Browse to [this link](http://cdimage.ubuntu.com/lubuntu/releases/14.04.1/release/) and scroll down until you find
[B]
lubuntu-14.04.1-desktop-i386.iso[/B] and also the ***md5sum*** for checking that the download is good.

-o-

- Please try to identify the error output to the screen and write them down in a reply.

Also, please specify your computer

- Brand name and model
- CPU (already known: Pentium D 805)
- RAM (already known: 1.5 GB)
- graphics chip/card
- wifi chip/card

It will help us help you.

---

### Post by ken71 on 2016-02-02
I'll try running the 32-bit LTS when I'm home (at 2:30pm EST). I googled the cpu and the intel spec sheet said 64-bit, so I thought I'd be fine.

But there is no gpu or wifi card. Just the cpu/ram/mobo/psu on a piece of cardboard. Although I will put a GTS 250 into it if it boots, but I removed it to troubleshoot.

---

### Post by sudodus on 2016-02-02
> **ken71 said:**
> I'll try running the 32-bit LTS when I'm home (at 2:30pm EST). I googled the cpu and the intel spec sheet said 64-bit, so I thought I'd be fine.

But there is no gpu or wifi card. Just the cpu/ram/mobo/psu on a piece of cardboard. Although I will put a GTS 250 into it if it boots, but I removed it to troubleshoot.

It might work with a 64-bit operating system, but the motherboard might be the bottleneck even if the CPU would manage to run. The problem might be somewhere else, for example the graphics. I guess there is a graphics chip on the motherboard, and maybe it is hard to find out what it is - you can test several versions and also other linux distros in order to find something that works.

On the other hand the GTS 250 card will probably boot with the boot option **nomodeset**. After that I hope and think you can install an nvidia proprietary driver and get good performance.

See these links for more details

[Boot options](http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808)

[Old hardware brought back to life](http://ubuntuforums.org/showthread.php?t=2130640)

-o-

If Lubuntu version **14.04.1** with the Trusty kernel does not work, you can try **14.04.2** with the Utopic kernel and **14.04.3** with the Vivid kernel. The next step would be to test a community respin based on Ubuntu **12.04 LTS**, for example **Bento**, **Bodhi** or **LXLE**. If you have to continue testing, you can try **Knoppix**, **Wary Puppy** and **TahrPup**.

---

### Post by ken71 on 2016-02-02
32-bit Lubuntu didn't work, but it finally booted SlackoPuppy 64-bit. Good enough, thanks :)

---

### Post by sudodus on 2016-02-03
I'm glad that you found a linux distro that works in your computer :-)

If you think that your problem is solved, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

### Post by mörgæs on 2016-02-03
In case other people find the thread: If one tries to run a 64 bit Buntu on a 32 bit computer there will be an explicit error message stating what's wrong. 

In other words: No error message, no problem with 64 bit :-)

---

