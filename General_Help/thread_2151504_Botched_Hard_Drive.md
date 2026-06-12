---
title: "Botched Hard Drive?"
date: 2013-06-04
forum: General Help
---

### Post by popejeremy on 2013-06-04
Hi! I have Ubuntu on my laptop. It was installed by ASUS at the factory. There's also an emergency partition or something that I don't really understand, but it's there, probably as a panic button to reinstal from the factory defaults.

Anyway, one day my laptop just wouldn't boot. It would kernel panic. The actual words "kernel panic" (not syncinc) were in the readout on the screen, and then it would just freeze up before booting into Ubuntu.

So, I'm trying to fix it, or at least rescue some of the data from my home folder. I made an XUbuntu USB stick, and booted it live, and ran Xubuntu from it. I got Internet access via my phone, so I can get online from within XUbuntu Live.

Then I mounted my hard drive. Here's where it gets weird. The fdisk -l reads something like

[FONT=Courier New]"
Device      Boot    Start            End           Blocks          Id   System
/dev/sda1            1                 38914        312571223+ ee    GPT
Partition 1 does not start on physical sector boundary.
/dev/sda3     *     1                 1               0                0    Empty
Partition 3 does not end on cylinder boundary.
"[/FONT]

To my non-expert eyes, that looks bad.

I was able to mount sda3 from within XUbuntu, but it works really slowly. Like when I go into a directory, it takes a long time to even give me a list of what's in it. This happens when I use the gui or just ls from the shell, or try to get a file out of it to upload from the Web browser with the gui.

Basically, something is really borked. I'm not sure what exactly do to now, but I'd really like to rescue at least a few files from the home directory. What should I do?

Thanks!

---

### Post by abyrne on 2013-06-04
Just to rule out that the drive may actually be failing, could you try installing SMART hard drive diagnostics and run them?
```

sudo apt-get install smartmontools
sudo smartctl --test=short /dev/sda

```
Then wait about 3 minutes for the short test to complete. Then run 
```

sudo smartctl --all /dev/sda

```
And post the output of that (it might be a good idea to redact the serial number)

---

### Post by ajgreeny on 2013-06-04
I once managed to get rid of this problem by booting to a live system and running ```
sudo e2fsck /dev/sda1
``` on my system root partition.  It found and repaired whatever problem the partition had and booted fine after that.

Worth a try, I think, even if it does not work it will certainly do no harm.

---

