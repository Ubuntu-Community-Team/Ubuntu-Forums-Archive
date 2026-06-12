---
title: "GRUB Menu entries out of control (4 entries for windows, a hundred kernels, ...)"
date: 2014-11-13
forum: General Help
---

### Post by sendbrianspam on 2014-11-13
Hi,
  I'm a novice with enough knowledge to be dangerous.  I spend all day recovering from a mistake that made my dual boot (win8 and ubuntu) unable to see Windows.  I only have two OSs (one version of Win8 and one version of Ubuntu).  I finally got it fixed, but now I have four entries for windows in grub (on two different sdas), and they all seem to work.  I guess that's fine, but I'm afraid that something bad might happen eventually.  While I'm at it, there's all the kernels I've ever had on there.  Is this normal?  I'd like to clean up, but am afraid that I'd wreck something and go back to another full day of doing nothing but trying to figure out how to fix it again.
  I'm sure there's an easier way to post what's on my computer.  Please let me know how if you're willing to help.

---

### Post by ajgreeny on 2014-11-13
I can't help with Windows any more as I've not used it for years, but for the mass of unnecessary kernels that you now have, try running terminal command ```
sudo apt-get -s autoremove
```
This will not actually do anything, but will show you what the command (simulate) would have done without the **-s** option.  I am hopeful that it may list for removal all the kernels except the last two installed.

If it does list them, and the command does not look as if it will also remove something you want to keep, run the command again without the -s option.```
sudo apt-get autoremove
```

---

### Post by nerdtron on 2014-11-13
Don't forget to run update-grub to update your grub entries.
```
sudo update-grub
```

---

### Post by ajgreeny on 2014-11-13
> **nerdtron said:**
> Don't forget to run update-grub to update your grub entries.
```
sudo update-grub
```
Surely that will happen by default if kernels are removed when you run the **sudo apt-get autoremove** command?

---

### Post by sendbrianspam on 2014-11-13
Thanks,


  I'm more concerned about the windows thing.  I try to avoid windows, but there's a few things I can't give up on windows.  For the autoremove, I only get:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-3.13.0-32-generic linux-image-extra-3.13.0-32-generic
  python-appindicator
0 upgraded, 0 newly installed, 3 to remove and 11 not upgraded.
Remv linux-image-extra-3.13.0-32-generic [3.13.0-32.57]
Remv linux-image-3.13.0-32-generic [3.13.0-32.57]
Remv python-appindicator [12.10.1+13.10.20130920-0ubuntu4]


If I'm reading this correctly, it would only remove one old linux kernel, and one other package (python-appindicator)

---

### Post by westie457 on 2014-11-13
Ignoring the Linux kernels for the moment, focussing on the Windows entries /sda1 and /sda2.
/sda1 is (should be) the Windows Recovery CD/environment. It should be about 700MB in size. This should be used to repair Windows.
Depending on the computer maker it might be the 'Factory Restore' partition. Only use if you need to restore the computer to how it left the factory.

/sda2 should be the normal Windows Boot partition. Get into the habit of selecting the last entry in the 'Grub' menu to boot Windows.

For the extra kernels in your list you might have to manually delete them. Are you able to boot the machine using any of those older kernels?

---

### Post by nerdtron on 2014-11-13
I think that is safe to remove.
From the man page of apt-get:
>     autoremove
           autoremove is used to remove packages that were automatically installed to satisfy
           dependencies for other packages and are now no longer needed.



---

### Post by sendbrianspam on 2014-11-14
I can boot to any of the listed Linux kernels.

Sda1 probably used to be the recovery drive, as its only 350mb, but I accidentally deleted its contents.  I think I over-did it trying to ger windows back, and now either sda1 or sda2 boot to windows in a manner that appear identical to me.  Also, there are two entries for win8 sda1 and two entries for win8 sda2.  I'm afraid if I leave them all, something will get corrupted.  I'm also afraid if I try to clean up, I'll lose the ability to boot to windows again.  Should I just leave it as is?

---

### Post by westie457 on 2014-11-14
> **sendbrianspam said:**
> I can boot to any of the listed Linux kernels.

Sda1 probably used to be the recovery drive, as its only 350mb, but I accidentally deleted its contents.  I think I over-did it trying to ger windows back, and now either sda1 or sda2 boot to windows in a manner that appear identical to me.  Also, there are two entries for win8 sda1 and two entries for win8 sda2.  I'm afraid if I leave them all, something will get corrupted.  I'm also afraid if I try to clean up, I'll lose the ability to boot to windows again.  Should I just leave it as is?
If everything starts as it should then leave well alone and adapt to what the Grub menu you shows. I have never used 'Grub Customizer' so cannot give advice about it.

As for the excess kernels, if you want to remove some of those and ```
sudo apt-get autoremove
``` does not work they will have to be removed manually either a 'safe' way or a 'not so safe' way.
We can guide you through both ways, the safe one first.

---

### Post by ajgreeny on 2014-11-14
Just so we are sure about kernels you have on the system, can you run the command ```
ls /boot/ | grep vmlinuz
```which will list all that are still sitting in your OS.

You can then remove all but the two most recent with command line, or synaptic, or software-center, though I never use the latter so I'm not sure how easily that can do the job.

---

### Post by sendbrianspam on 2014-11-17
Here's the results of : [COLOR=#000000][FONT=Ubuntu Mono]ls /boot/ | grep vmlinuz[/FONT][/COLOR]


vmlinuz-3.13.0-32-generic
vmlinuz-3.13.0-33-generic
vmlinuz-3.13.0-34-generic
vmlinuz-3.13.0-35-generic
vmlinuz-3.13.0-36-generic
vmlinuz-3.13.0-37-generic
vmlinuz-3.13.0-39-generic
vmlinuz-3.8.0-29-generic
vmlinuz-3.8.0-31-generic
vmlinuz-3.8.0-32-generic
vmlinuz-3.8.0-33-generic
vmlinuz-3.8.0-34-generic
vmlinuz-3.8.0-35-generic
vmlinuz-3.8.0-36-generic
vmlinuz-3.8.0-37-generic
vmlinuz-3.8.0-38-generic
vmlinuz-3.8.0-39-generic
vmlinuz-3.8.0-41-generic
vmlinuz-3.8.0-42-generic
vmlinuz-3.8.0-44-generic

Did I have something set strangely that keeps all of these, or is this normal?

---

