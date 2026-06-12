---
title: "[SOLVED] Update problem"
date: 2007-12-19
forum: General Help
---

### Post by el escocés on 2007-12-19
I downloaded the recent updates, the truth is I never really pat attention as to what they are, click update, go make my breakfast tea and usually when I get back to my desk everything is done.

I think this last update was some new kernel headers, well when I restarted ubuntu (after the updater asked me to) I found that my menu.lst had been edited; me windows partition had been removed and the current linux headers had the wrong root hd configured.

It is all working correctly now but why didn't grub detect correctly the root hd and windows partition??

Has this happened to anyone else??

---

### Post by geirha on 2007-12-19
Have you edited menu.lst yourself? There are some special comments in that file, like ```
### START AUTOMAGIC KERNELS LIST
...
### END AUTOMAGIC KERNELS LIST
``` Everything inside there is maintained by ubuntu. Windows and other OS entries must be either before that section, or after it, or else they will be removed when the "update-grub" script is run. The "update-grub" script is run whenever a new kernel is installed, to add the new kernel to the automagic kernels list, which is probably what has happened here.

When you edit menu.lst, always run ```
sudo update-grub
``` afterwards and check that it looks the same afterwards.

---

### Post by el escocés on 2007-12-19
thanks for replying.

Yes I edited the menu.lst file myself prior to the updating and possibly my window partition was inside the automatic kernels list, so that most likely was the reason my windows entry was removed.  Why didn't grub recognise my windows partition and automatically generate an entry for it?

As you suggested I also ran the:

```
update-grub
```

And it changed the linux root back to hd0,1 when it should be hd0,0

Any ideas why?

---

### Post by geirha on 2007-12-19
There should be a line in menu.lst that looks like this:
```
# groot=(hd0,1)
```
Change that to
```
# groot=(hd0,0)
```
and run update-grub which will change the root on all the automagic kernels to what groot= says. (Note that the # at the beginning should be there, do not remove it)

---

### Post by el escocés on 2007-12-19
That was it, never really paid attention to the other options in Grub apart 'timeout' 'default' and 'color' options, I also, while I was at it, I changed the

> # defoptions=splashSo I don't have to change every line to get rid of the 'quiet'.

Thanks for your help!

---

### Post by TheLions on 2007-12-19
i got same problem here, after updates my loader for vista vanished!
Also i lost sound, it says that my sound card isn't connected:confused:

I use onboard soundcard (Nforce4 - realtek)

---

### Post by el escocés on 2007-12-19
I can help you with your vista loader but have no idea why your sound is gone, I would open a new thread about that.

print out the results of

```
sudo fdisk -l
```

and post also your /boot/grub/menu.lst file

---

### Post by TheLions on 2007-12-19
ok, problem solved, i found my backed up menu.lst

but sound is the problem.

i'll open a new thread for that.

---

