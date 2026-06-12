---
title: "irregular crashes -- need early boot messages"
date: 2013-01-21
forum: General Help
---

### Post by rpm13 on 2013-01-21
My machine crashes once in a while at boot. That is after grub a few messages flash by -- the last one usually is starting kernel -- and then it hangs.

This happens once every 5 to 10 boots so it may be a h/w problem.

/var/log/messages and dmesg dont show anything strange (on the next boot)

So is there some way of turning on early-boot messages?

---

### Post by ibjsb4 on 2013-01-21
To turn it on

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=turn+on+boot+log&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=turn+on+boot+log&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by Bashing-om on 2013-01-21
rpm13; Hi !

The short answer is no, with the implementation of upstart, there is no method available to log the startup messages. However one may see the boot messages. In 12.04 I do it like this:
Edit /etc/default/grub (make a backup copy first, Murphy's law applies to computers too)
```
sudo cp /etc/default/grub /etc/default/grub-orig
gksudo gedit /etc/default/grub

```Change these lines to this:
> GRUB_CMDLINE_LINUX_DEFAULT=""

GRUB_GFXMODE=textSave and exit
update grub:
```
sudo update-grub
```
On boot; ctl-s will pause, ctl-o resume boot (maybe). Might try the scroll lock key.
Other means: after booted to the gui, start a terminal and stop lightdm:
```
sudo service lightdm stop
```Then ctl-alt-f7 will have boot messages on what was the GUI interface.
```
sudo service lightdm start
``` to restart the desktop.[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by rpm13 on 2013-01-22
> **Bashing-om said:**
> rpm13; Hi !

The short answer is no, with the implementation of upstart, there is no method available to log the startup messages. 

Yes as you've predicted bootlogd does not work. I get an (almost) empty file containing these 2 lines:

```

(Nothing has been logged yet.)
Tue Jan 22 00:16:47 2013: INIT: Switching to runlevel: 6

```


> 
However one may see the boot messages. In 12.04 I do it like this:
Edit /etc/default/grub (make a backup copy first, Murphy's law applies to computers too)
```
sudo cp /etc/default/grub /etc/default/grub-orig
gksudo gedit /etc/default/grub

```Change these lines to this:
Save and exit
update grub:
```
sudo update-grub
```
On boot; ctl-s will pause, ctl-o resume boot (maybe). Might try the scroll lock key.
Other means: after booted to the gui, start a terminal and stop lightdm:
```
sudo service lightdm stop
```Then ctl-alt-f7 will have boot messages on what was the GUI interface.
```
sudo service lightdm start
``` to restart the desktop.[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

No crash from my question. So dont have any new data yet.

I was contemplating a BIOS reflash. Seems quite risky though&#8230;

---

### Post by Bashing-om on 2013-01-22
rpm13;

I also am somewhat hesitant about messing around with a bios update by flashing it. It can be done, I have contemplated such before I got all my hitchs worked out on my primary system. The conclusion I reached at that time was to purchase a up-to-date bios chip (my boards are AMD based)  the chip is cheap. Then in the event the new bios introduced other problems I could easily revert back to the old chip.

On the subject of intermittent crashes, might keep an eye on the .xsessions-errors log in your home directory, and of course look at  /var/log/Xorg.0.log. A likely candidate is xserver seeing a difficulty at times.

[INDENT][INDENT]my 2 pints worth

[/INDENT][/INDENT]

---

### Post by rpm13 on 2013-01-22
> **Bashing-om said:**
> rpm13;

I also am somewhat hesitant about messing around with a bios update by flashing it. It can be done, I have contemplated such before I got all my hitchs worked out on my primary system. The conclusion I reached at that time was to purchase a up-to-date bios chip (my boards are AMD based)  the chip is cheap. Then in the event the new bios introduced other problems I could easily revert back to the old chip.

On the subject of intermittent crashes, might keep an eye on the .xsessions-errors log in your home directory, and of course look at  /var/log/Xorg.0.log. A likely candidate is xserver seeing a difficulty at times.

[INDENT][INDENT]my 2 pints worth

[/INDENT][/INDENT]

Ok heres a crash picture.
Note its long before X starts --probably before filesystems are mounted.
Its just after grub starts loading the OS.

Since Ive no success in capturing a log file, here is some hand copied stuff from the console when the system hung.  Note nn means some number that I did not copy.
```

Pid 63 comm: udevd Tainted G
n n panic/n
n n oops/n
n n no_context/n
n n __bad_no_semaphore/n
etc
do_page_fault
do_page_fault
do_page_fault
bad_area_no_semaphore
error_code
io_read
ata_sff_data_xfer
ata_pio_sector
ata_pio_sectors
ata<something>
ata<something>
common_interrupt
<bottom of screen>


```

---

### Post by Bashing-om on 2013-01-23
rpm13;

It does look like the error appears early on in the boot process. A stab at this, rebuild the initramfs:
```
sudo update-initramfs -u
```If that still results in problems, next is to re-write /boot/initrd.img

update-initramfs: failed for /boot/initrd.img… error message. Some have success with the following commands, so you can try them first:
```
sudo dpkg --configure -a
sudo apt-get update
```But don’t be surprised to find yourself back where you started, but here is a trick that seems rather unlikely, but has worked before: move or delete initrd.img. If that file is corrupted, you would think it would just get overwritten in the update, yet deleting (or moving, if you want to play it safe) initrd.img has made all the difference in some instances.

It’s probably safer just to move the file, since if a replacement is successfully generated, you can delete it later. To move it to your home folder, enter the following command, remembering to replace the kernel number with the one you’re moving:

```
sudo mv /boot/initrd.img-2.6.32-22-generic ~/
```[INDENT]poke'n see what results
[/INDENT]

---

### Post by rpm13 on 2013-01-24
> **Bashing-om said:**
> rpm13;

It does look like the error appears early on in the boot process. A stab at this, rebuild the initramfs:
<snipped>


Hi Bashing-om.

Thanks for your thoughts and comments.

Ran:
```

$ sudo update-initramfs -u
update-initramfs: Generating /boot/initrd.img-2.6.32-5-686
WARNING: could not open /var/tmp/mkinitramfs_OOAKgx/lib/modules/2.6.32-5-686/modules.builtin: No such file or directory

```

Now this looks like [this bug]("http://lists.debian.org/debian-kernel/2012/03/msg00224.html") which Ive been seeing for a while but did not take to seriously.

After that Im getting parsing errors ;) with your instructions.
[It seems you meant to say something but there was a slip of the editor]:P

---

### Post by Bashing-om on 2013-01-24
rpm13;
Did you replace the kernel number with the kernel number you are presently running?
(the example number I provided is an old one)
```
uname -r
``` will generate the current kernel number.

Rerun the update-initramfs command with the appropriate kernel number, see what haps.
In the mean time- I will look at the reference you provided.
[INDENT]puzzles have solutions

[/INDENT]

---

