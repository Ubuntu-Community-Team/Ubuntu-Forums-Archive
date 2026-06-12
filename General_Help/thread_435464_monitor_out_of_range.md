---
title: "monitor out of range"
date: 2007-05-06
forum: General Help
---

### Post by rome32 on 2007-05-06
Im dual booting kubuntu fiesty with xp. At times during bootup and shutdown, i get a flickering message on my monitor saying that it is out of range. It shows resolution, refresh rate and one more thing i can remember. When its out of range i cant see anything on the screen except for the message.
 Its goes out of range:
before grub bootloader
xp bootscreen (didnt have this at first, just happened for some reason)
kubuntu shut down screen

its a problem because sometimes it doesnt snap out of it, and just gives me that flickering message. I have to restart and hope for it to work. Im aware that it could be a issue with my monitor, but this has never been a problem before. If you need it my monitors a viewsonic vg500 and all the specs are **[here]("http://www.viewsonic.com/support/desktopdisplays/lcddisplays/graphicseries/vg500/#specs")**.

help would be appreciated,
rome32

---

### Post by rome32 on 2007-05-10
bump
im still not having any luck with this. 
I just need to force the video settings during the post screens somehow.

any help would be great, even a bump in the right direction
thanks,
rome32

---

### Post by Nythain on 2007-05-10
a quick easy fix that also allows you to see whats going on during boot is to nix the splash alltogether...
gksudo gedit (or kdesu kate) /boot/grub/menu.lst
remove
quiet splash
add
vga=792
in thier place
that will cause your system to load verbosely without a splash screen at a decent resolution, and will stop the annoying Out of Range issue (wich by the way is an issue with the refresh rate and resolution that grub is trying to use, you could probably just add vga=792 after quiet splash, leaving them, and fix the problem also, keeping your splash screen, but im not sure)

---

### Post by Wim Sturkenboom on 2007-05-11
I doubt if I can help you (I know what is wrong but don't know how to solve it), but can you tell us make and model of the video card.
More important, can you give the exact out of range message? It's probably resolution (640x480 I assume), vertical refresh (something like 60Hz) and horizontal refresh (somewhere around 30 kHz).
Did you change anything when the problem started (e.g. added a kvm switch to share monitor between 2 computers)? Or did it start after you installed kubuntu.

If I have my numbers correct (see above), your horizontal refresh is around 30 kHz at bootup which might be critical as the spec of your monitor gives 30 kHz as the minimum for the horizontal refresh rate (one moment monitor is happy with signal from video card, next moment it's not). Be aware that it can be a monitor issue but also that it can be a video card issue. Two possible causes:
one or more components in the monitor or the video card are die-ing (how the hack do you spell that word) or there might be a temperature problem in the monitor or video card.

> I have to restart and hope for it to workWhat happens after a real power cycle (disconnect power cord to make sure) of the computer? What happens when you let the computer or monitor cool down?

@Nythain: As I understand it, the problem already starts before GRUB

---

### Post by rome32 on 2007-05-12
> **Nythain said:**
> a quick easy fix that also allows you to see whats going on during boot is to nix the splash alltogether...
gksudo gedit (or kdesu kate) /boot/grub/menu.lst
remove
quiet splash
add
vga=792


ive tried editing menu.lst and added defoptions=vga=0x316 resume=/dev/hda2 but it didnt help. Should i try that too?

> **Wim Sturkenboom said:**
> I doubt if I can help you (I know what is wrong but don't know how to solve it), but can you tell us make and model of the video card.
More important, can you give the exact out of range message? It's probably resolution (640x480 I assume), vertical refresh (something like 60Hz) and horizontal refresh (somewhere around 30 kHz).
Did you change anything when the problem started (e.g. added a kvm switch to share monitor between 2 computers)? Or did it start after you installed kubuntu.

If I have my numbers correct (see above), your horizontal refresh is around 30 kHz at bootup which might be critical as the spec of your monitor gives 30 kHz as the minimum for the horizontal refresh rate (one moment monitor is happy with signal from video card, next moment it's not). Be aware that it can be a monitor issue but also that it can be a video card issue. Two possible causes:
one or more components in the monitor or the video card are die-ing (how the hack do you spell that word) or there might be a temperature problem in the monitor or video card.

What happens after a real power cycle (disconnect power cord to make sure) of the computer? What happens when you let the computer or monitor cool down?

@Nythain: As I understand it, the problem already starts before GRUB
well its a ati radeon 7200, old i know, but it worked fine before. I didnt change anything like that, just installed kubuntu and the grub bootloader. I cant see the out of range messege clearly becuast its flickering so fast, but i can tell that its coming from the monitor. Its giving me the vertical and horizontal frequencies. But i tihnk the vertical freq is in the hundreds?

Power cycle doesnt do anything, and its the same even if the computers been off all night, so i dont think its a heat issue. And yes, the problem starts before grub, and then starts again after i select xp. At least i can see Grub...

thanks for you responses guys,
rome32

---

### Post by namanbagga on 2007-11-13
[This]("http://www.namanb.com/2007/11/ubuntu-710-bootup-resolution-problem.html") will work.

---

### Post by namanbagga on 2007-11-13
This[http://www.namanb.com/2007/11/ubuntu-710-bootup-resolution-problem.html]("http://www.namanb.com/2007/11/ubuntu-710-bootup-resolution-problem.html") is a good solution and you'll not need to disable the splash screen to do it.

---

### Post by taurus on 2007-11-13
> **namanbagga said:**
> This[http://www.namanb.com/2007/11/ubuntu-710-bootup-resolution-problem.html]("http://www.namanb.com/2007/11/ubuntu-710-bootup-resolution-problem.html") is a good solution and you'll not need to disable the splash screen to do it.

You should consider using _gksudo_ when you use gedit GUI editor.

---

