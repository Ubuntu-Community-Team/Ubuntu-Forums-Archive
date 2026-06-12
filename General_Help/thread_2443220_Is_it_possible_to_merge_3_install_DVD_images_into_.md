---
title: "Is it possible to merge 3 install DVD images into ONE .iso"
date: 2020-05-12
forum: General Help
---

### Post by 777funk on 2020-05-12
the title says it all. I have 3 DVDs that I ripped to iso files and I'd like to put them together. It's one program but so bitg it requires 3 DVDs and requests:

"please insert disk 2" after partial install followed by "please insert disk 3" for the finish. 


I'd like to merge these 3 to one single file if it's possible. Can this be done?

---

### Post by monkeybrain20122 on 2020-05-12
You don't need to merge the isos. When you see the 'please insert disk x' just unmount the current iso and mount the next (need open a new terminal instance) then it will continue. 

See [this]("https://karibe.co.ke/2018/11/installing-matlab-2018a-from-two-iso-images-in-ubuntu-18-04/").

That said, I think k3b can merge isos, but haven't used it for years.

---

### Post by 777funk on 2020-05-12
It's actually a windows install with 3 DVDs. I have the install discs and can still install via my real discs, but when I tried using my iso files it crashes during the install.

I used WinCDEmu to emulate and mount the img files.

It's a Win XP program I will probably never see CDs for again so it'd sure be nice to have the disc images useable.

---

### Post by monkeybrain20122 on 2020-05-12
> **777funk said:**
> It's actually a windows install with 3 DVDs. I have the install discs and can still install via my real discs, but when I tried using my iso files it crashes during the install.

I used WinCDEmu to emulate and mount the img files.

It's a Win XP program I will probably never see CDs for again so it'd sure be nice to have the disc images useable.


I think you might need to mount the iso with command line then run the Windows installer (the .exe) with wine like [here]("https://askubuntu.com/questions/160396/how-do-i-install-a-windows-program-in-an-iso-into-wine"). See the first and last answers. I don't think the GUI works because of permission issues. If wine works (which is kind of a hit and miss) then it shouldn't matter how many isos you have, just unmount and remount like in the link I gave you in last post.

---

### Post by ActionParsnip on 2020-05-13
Do you mean something like this?

[https://fossbytes.com/how-to-put-multiple-iso-files-in-one-bootable-usb-disk-create-multiboot-usb-disk/](https://fossbytes.com/how-to-put-multiple-iso-files-in-one-bootable-usb-disk-create-multiboot-usb-disk/)

---

### Post by 777funk on 2020-05-13
> **monkeybrain20122 said:**
> I think you might need to mount the iso with command line then run the Windows installer (the .exe) with wine like [here]("https://askubuntu.com/questions/160396/how-do-i-install-a-windows-program-in-an-iso-into-wine"). See the first and last answers. I don't think the GUI works because of permission issues. If wine works (which is kind of a hit and miss) then it shouldn't matter how many isos you have, just unmount and remount like in the link I gave you in last post.

This is in Windows XP (actual windows)  that the iso will be run. I'm having trouble with the iso though since it isn't on an actual DVD. I think if it were one iso (vs 3 iso files from 3 separate DVDs) it may work. This is why I would like to combine them.

---

### Post by monkeybrain20122 on 2020-05-13
> **777funk said:**
> This is in Windows XP (actual windows)  that the iso will be run. I'm having trouble with the iso though since it isn't on an actual DVD. I think if it were one iso (vs 3 iso files from 3 separate DVDs) it may work. This is why I would like to combine them.


Try[ here]("https://forum.winehq.org/viewtopic.php?t=322") and [here]("https://forum.winehq.org/viewtopic.php?t=13409").

---

### Post by 777funk on 2020-05-14
> **monkeybrain20122 said:**
> Try[ here]("https://forum.winehq.org/viewtopic.php?t=322") and [here]("https://forum.winehq.org/viewtopic.php?t=13409").

Doesn't that apply to WINE only (and not actual Windows)?

---

### Post by monkeybrain20122 on 2020-05-14
> **777funk said:**
> Doesn't that apply to WINE only (and not actual Windows)?

I think you are trying to install a Windows program on Ubuntu (with wine) If you are trying to install it on Windows you are on the wrong forum.

---

### Post by 777funk on 2020-05-16
> **monkeybrain20122 said:**
> I think you are trying to install a Windows program on Ubuntu (with wine) If you are trying to install it on Windows you are on the wrong forum.

I'm actually trying to create or merge 3 files into a single file in Linux (that will later be installed in Windows).

I think this applies to Linux as Linux is doing the heavy lifting and the work in question.

---

### Post by monkeybrain20122 on 2020-05-16
> **777funk said:**
> I'm actually trying to create or merge 3 files into a single file in Linux (that will later be installed in Windows).

I think this applies to Linux as Linux is doing the heavy lifting and the work in question.

Try k3b, it is in the repository. Though I don't think you need to combine the iso in Windows either. I haven't used Windows for 10 years but I remember I used to use[ magiciso]("http://www.magiciso.com/") to mount iso to install software, when prompted for next iso just unmount the current iso and mount the next one and so on just like in Linux except it uses a gui rather than cli. Magiciso also merges isos. (Oops it is not a freeware, don't ask me how I got it on Windows, it was looong time ago in my XP days. ;))

---

