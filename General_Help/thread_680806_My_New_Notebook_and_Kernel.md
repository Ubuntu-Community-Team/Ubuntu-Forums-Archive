---
title: "My New Notebook and Kernel"
date: 2008-01-28
forum: General Help
---

### Post by TorchlightJay on 2008-01-28
Hello,

So I just purchased an HP tx2000, the upgrade to their tx1000 and I am having hardware issues. I have tried Ubuntu 7.10, openSuSE 10.3, and Fedora 8, all of which have been giving me problems. I am tempted to send it back but I once heard that all hardware eventually works with Linux.

I was thinking, maybe I can update to the latest stable kernel and maybe it'll work. All the hardware on here is standard, it even has Wacom and a touchscreen (it's a tablet of course) and Broadcom wifi. I think maybe it's the chipset or something that doesn't work with the precompiled kernels on these distros. 

Do you guys think I should update to the latest kernel, Alsa, and other software (wacom and egalax for example, hold out for the latest releases of these distros, or just return the notebook. It's a pretty decent notebook so it'd be a shame to take it back. What do you guys think? Keep in mind, this notebook was released 01/08/08 so ya, most hardware and stuff is new on it. 

Thanks

---

### Post by Mikecore on 2008-01-28
HP is horrible about its BIOS. I have and HP dv2210us and until they released a updated BIOS I also had issues with any linux distro that I tried to run on it. But your right most of the time with a little time or the correct boot options you can get laptops running linux.
It took about six months. ( So if your willing to run Windows or have a unstable linux ) that whole time keep it. I was not willing for I gave it to my wife and purchased a Toshiba which ran linux without any trouble, everything worked but the built in SD card readers.

---

### Post by ir0nman on 2008-02-01
Have you looked at the tx1000 series, and tried the boot parameters and stuff? It sounds like the tx2000 is very similar internally to the tx1000 except for the active digitizer. I would take a quick look at this tread [HPtx1000]("http://ubuntuforums.org/showthread.php?t=442483&highlight=tx1000")

---

### Post by TorchlightJay on 2008-02-02
Ya, I've tried some of the things and they have worked. There are some slight difference though. I think the tx2000 has a different chipset than the tx1000. They were developed 9 months apart I think.  So ya, this one has some slightly different hardware. One thing that I think is different is the chipset. 
In the past, I have had a more advanced chipset to where the kernel couldn't support it. New kernel gets released with a new distro and things work close to perfectly.

Right now the majro things that don't work is the touchscreen, the digitizer, the soundcard, and the wireless won't work (though I think the card has sustained some damage). It is being read when I do lspci, I need to use ndiswrapper and when I modprobe, it works..... just for that boot. When I reboot, it doesn't work. I figure "Okay, I'll just modprobe ndiswrapper again and it'll work", doesn't happen that way. Not sure what to think. I am using bcmwl5.inf, maybe I should use bcmwl5a.inf? I don't know. 

For the touchscreen and digitizer, I think I need to user software like egalax or evtouch and then the linuxwacom program coupled with a new kernel. The sound, I think is alsa related. Right now alsa is in it' 1.0.16rc1 state, maybe with the next rc or two, it'll work properly. I don't know, share your thoughts. 

Thanks

---

### Post by Murphy2712 on 2008-02-15
Hi,
I've got a this tabletpc (I'm using Debian) and I've the same problems except for the sound/microphone, try this :
#modprobe -r snd-hda-intel
#modprobe snd-hda-intel model=3stack
and for saving the parameters, add :
options snd-hda-intel model=3stack
in
#nano /etc/modprobe.d/sound (new file for me)

([http://ubuntuforums.org/showthread.php?p=4335089#post4335089](http://ubuntuforums.org/showthread.php?p=4335089#post4335089))

---

