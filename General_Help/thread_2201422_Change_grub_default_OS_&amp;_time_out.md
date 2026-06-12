---
title: "Change grub default OS &amp; time out?"
date: 2014-01-24
forum: General Help
---

### Post by mips on 2014-01-24
Posting this in the cafe as I'm in a major rush (need to drop this laptop off in 1hr) and this place gets more views.

I need to make Windows 7 the default OS and appear at the top of the list in grub, also need to change the time out to 1sec.

Ubuntu 14.04 daily (yes I know it's not stable yet)

Edit: There's no PPA for grub customiser in case someone wants to mention that.

---

### Post by Elfy on 2014-01-24
/etc/default/grub

change GRUB_TIMEOUT=1

make sure #GRUB_HIDDEN_TIMEOUT=0 is commented

I've found that adding 

GRUB_SAVEDEFAULT=true (it should boot the last booted OS)

works

remember to update grub

then try booting windows - then, it should save it as the default

---

### Post by mips on 2014-01-24
Will give it a bash once I put the hdd back in the laptop, just busy restoring data via sata port on my desktop which is much faster when you need copy hundreds of gigs.

---

### Post by mikewhatever on 2014-01-24
Oh dear, quick, here we go! :)

You'd usually just edit /etc/default/grub, ...the first four lines:
```

GRUB_DEFAULT="insert menu entry here"
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT=1

```
To get the menuentry for W7, run cat /boot/grub/grub.cfg | grep menuentry.
Update grub when done.

PS: Not sure it would work in 14.04, as grub is newer there, and things may have changed.

---

### Post by Elfy on 2014-01-24
> **Elfy said:**
> /etc/default/grub

change GRUB_TIMEOUT=1

make sure #GRUB_HIDDEN_TIMEOUT=0 is commented

I've found that adding 

GRUB_SAVEDEFAULT=true (it should boot the last booted OS)

works

remember to update grub

then try booting windows - then, it should save it as the default
GRUB_DEFAULT=saved

need that as well I think - just checking

---

### Post by Elfy on 2014-01-24
> **Elfy said:**
> GRUB_DEFAULT=saved

need that as well I think - just checking

works for me

GRUB_DEFAULT=saved
GRUB_SAVEDEFAULT=true

and 

#GRUB_HIDDEN_TIMEOUT=0
GRUB_TIMEOUT=1

then update-grub

works fine in 14.04 here - with the normal grub, which I assume you've got

---

### Post by mips on 2014-01-24
Guys thanks! You definitely pointed me in the right direction. The GRUB_DEFAULT=saved works to the extent that it will use the same previously selected option at each boot until you change the selection in grub. This works fine but for someone new I would prefer it if they did not have to manually change it after a reboot, I want it to default to win7 all the time. Your method does work fine though and on closer inspection this is the default setup on my manjaro box (yeah I should have looked there first, lol) so nothing wrong with it and it does answer my question.

Anyway what you provided me with was great as I punched it into google and found this which is a good guide [http://askubuntu.com/questions/52963/how-do-i-set-windows-to-boot-as-the-default-in-the-boot-loader](http://askubuntu.com/questions/52963/how-do-i-set-windows-to-boot-as-the-default-in-the-boot-loader)

Summary, in a cli do,

```
grep menuentry /boot/grub/grub.cfg
```

which will spit out all the grub entries, look for the windows one which on my desktop looks like,

```
menuentry 'Windows 7 (loader) (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-A4AE5922AE58EE74' {
    menuentry "Memory Tester (memtest86+)" --class memtest86 --class gnu --class tool {
```

From that we only need the **Windows 7 (loader) (on /dev/sda1)** part.

Next we need to edit /etc/default/grub and change the following two lines for what I need to achieve,
```
sudo gedit /etc/default/grub
```

```
GRUB_DEFAULT="Windows 7 (loader) (on /dev/sda1)"
GRUB_TIMEOUT=1
```

Then update grub,
```
sudo update-grub
```

And voila all is good!

Gonna drop the laptop off now at the pub so I will have a beer for you guys! Thanks again for the very prompt assistance ;)

Elfy feel free to move this thread to the appropriate section of forum, thx!

---

### Post by philinux on 2014-01-24
Moved to general help.

@mips, general help and beginners forum are far more active than cafe.

You also have IRC #ubuntu channel for very swift help.

{also marked as solved)

---

### Post by mips on 2014-01-24
Thank you.

---

