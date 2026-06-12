---
title: "'text' grub option doesn't get me to a terminal"
date: 2015-04-25
forum: General Help
---

### Post by doriad on 2015-04-25
I have been having trouble getting Ubuntu installed (it seems like a video driver issue, but all of the tutorials I read about installing nvidia drivers don't seem to help). This question is hopefully more general though. When I hold "shift" at boot time to get to the grub interface, press 'e' to edit the kernel arguments, and replace "quiet splash" with "text", I thought it was supposed to skip all of the graphical stuff and just bring me to a text-only terminal. However, it just boots and hangs at the same black screen with a cursor that it does when I don't modify these arguments. I have also tried appending "single" to the end of this argument list, with no change.

Can anyone comment on why this isn't working (because at this point, I can't continue messing with the drivers, because I can't get to a terminal)?

Thanks,

David

---

### Post by SeijiSensei on 2015-04-25
Just add a space followed by the word "single" at the end of the kernel line to boot into the terminal.  You're entering "single-user mode."

If you need to make changes to the filesystem, first remount it as read/write like this:
```
# mount -o remount,rw /
```

---

### Post by grahammechanical on 2015-04-26
If Ubuntu is installed and you get a Grub boot menu, you can try Recovery mode. The Resume option may load to a working desktop using a fall back open source video driver.

There is also a recovery mode Network option that will set up an internet connection and put the file system into read and write mode. Then you can go to Root. That will drop you to a shell. When you have finished with entering commands typing exit will bring you back to the recovery menu.

This command will install the current proprietary video driver

```
ubuntu-drivers autoinstall
```

Regards.

---

### Post by doriad on 2015-04-26
[**[COLOR=#000000]SeijiSensei[/COLOR]**]("http://ubuntuforums.org/member.php?u=698195")
As I mentioned, I tried that and it didn't seem to work.

[**[COLOR=#000000]grahammechanical[/COLOR]**]("http://ubuntuforums.org/member.php?u=1087323")
I tried several of the things in the resume mode that you suggested, and here are the results:
1) Recovery mode Resume: X actually loaded, but when I move the mouse the screen flickers from the correct display to black. Very strange.
2) Network+Root brought me to a terminal (finally!). I tried 'ubuntu-drivers autoinstall' which seemed to complete successfully, but when I rebooted I was brought to the same black screen as before.
3) I used Network+Root to download and try to install the driver from the nvidia website (NVIDIA-Linux-x86_64-304.125.run : note, ubuntu-drivers also recommended 304). However, I got "Nvidia: Can't install (unable to build kernel module)". I already had linux-headers installed, and I installed linux-source with no change.
4) When I use Recovery mode FailsafeX, I get a dialog box that said something about "your video settings were not detected correctly, what do you want to do." I waited here for a long time (minutes) before I finally got a cursor. I tried many of the options on multiple reboots, but nothing seemed to fix it.

Any other thoughts?

Thanks for your help!

David

---

