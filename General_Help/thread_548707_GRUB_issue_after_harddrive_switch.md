---
title: "GRUB issue after harddrive switch"
date: 2007-09-11
forum: General Help
---

### Post by Krank on 2007-09-11
On my server, Grub is behaving rather oddly. It began when I moved my Linux partitions onto a new harddrive and removed the old, then replaced the olf with thr new, I think.

It seems it tries to use the hd(0,0) for root in the root line, and the hdc1 as root in the kernel line of the menu.lst.

This, I must admit, confounds the heck out of me. It's supposed to use (I figured out after some furious testing) hd(0,1) and sda2, respectively. Now, I need to manually edit the options at boot time (which, fortunately, isn't all that often - it's my server, you see).

These erroneous stanzas have remained through at least five kernel upgrades, and persist even if I do a update-grub. For some reason, it seems to believe, rather persistantly, that it has autodetected the correct options. Which it has not, I assure you.

This has been botherwing me for a while now, and any assistance would be much appreciated.

---

### Post by mcduck on 2007-09-11
> **Krank said:**
> On my server, Grub is behaving rather oddly. It began when I moved my Linux partitions onto a new harddrive and removed the old, then replaced the olf with thr new, I think.

It seems it tries to use the hd(0,0) for root in the root line, and the hdc1 as root in the kernel line of the menu.lst.

This, I must admit, confounds the heck out of me. It's supposed to use (I figured out after some furious testing) hd(0,1) and sda2, respectively. Now, I need to manually edit the options at boot time (which, fortunately, isn't all that often - it's my server, you see).

These erroneous stanzas have remained through at least five kernel upgrades, and persist even if I do a update-grub. For some reason, it seems to believe, rather persistantly, that it has autodetected the correct options. Which it has not, I assure you.

This has been botherwing me for a while now, and any assistance would be much appreciated.
You just need to edit the menu.lst to use correct partitions yourself. Updating kernel or running update-grub is not even supposed to autodetect the correct partitons for you. Actually even installing Grub doesn't autodetect them, you need to point Grub to the correct partiton yourself.

---

### Post by flatwombat on 2007-09-11
Try "sudo gedit /boot/grub/menu.lst" to get to the file.  It will open a new window with your existing grub menu and you can simply change the partition and drive information there.  Save, exit and reboot.

---

### Post by Krank on 2007-09-11
> **mcduck said:**
> You just need to edit the menu.lst to use correct partitions yourself. Updating kernel or running update-grub is not even supposed to autodetect the correct partitons for you. Actually even installing Grub doesn't autodetect them, you need to point Grub to the correct partiton yourself.

Will those changes be carried over the next time the kernel is updated? Or will I have to edit these lines every time the kernel is updated? Is grub-update intelligent enough to just modify the kernel-specific parts of each stanza?

EDIT: Apparently not. If I do an update-grub, my changes vanish. So, either update-grub uses some failed way to autodetect these things, or it uses some bizarre defaults, which are apparently hidden somewhere.


WHAT I WANT: I want Grub to work as it should. I shouldn't have to manually edit these lines at every kernel update. It *SHOULD* be done automagically. It claims that it is. It's not. THAT's my problem, not any inability to do a sudo nano /boot/grub/menu.lst .

---

### Post by flatwombat on 2007-09-11
So, then you've got to look at where grub's pulling it's info from. Another file needs to be updated.  [http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)  If nobody comes up with the correct one here, you can probably send a message and get some info from the grub team.

---

### Post by mcduck on 2007-09-11
> **Krank said:**
> Will those changes be carried over the next time the kernel is updated? Or will I have to edit these lines every time the kernel is updated? Is grub-update intelligent enough to just modify the kernel-specific parts of each stanza?

EDIT: Apparently not. If I do an update-grub, my changes vanish. So, either update-grub uses some failed way to autodetect these things, or it uses some bizarre defaults, which are apparently hidden somewhere.


WHAT I WANT: I want Grub to work as it should. I shouldn't have to manually edit these lines at every kernel update. It *SHOULD* be done automagically. It claims that it is. It's not. THAT's my problem, not any inability to do a sudo nano /boot/grub/menu.lst .

Yes it is, you just need to also make the changes under the default options in the menu.lst file. Like I said, update-grub doesn't autodetect anything. Running update-grub (or installing new kernel) reads the default options  from the very same file,  and then creates new kernel boot lines based on those options.

```
## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=365d417b-a50b-4df9-8249-f17f37a542aa ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=splash vga=792 quiet

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##
```

---

### Post by emperor on 2007-09-11
> **Krank said:**
> 
It seems it tries to use the hd(0,0) for root in the root line, and the hdc1 as root in the kernel line of the menu.lst.

This, I must admit, confounds the heck out of me. It's supposed to use (I figured out after some furious testing) hd(0,1) and sda2, ...


If you changed your IDE (hdc) drive to an SATA (sda) then you will need to edit /etc/grub/device.map My first drive is an SATA drive and device.map has the following entry:

emperor@iceland:/boot/grub$ cat device.map
(hd0)   /dev/sda

Note: This entry is used when a new kernel is installed.

---

### Post by Krank on 2007-09-11
In case anyone's interested:

[http://www.fifi.org/cgi-bin/man2html/usr/share/man/man8/update-grub.8.gz](http://www.fifi.org/cgi-bin/man2html/usr/share/man/man8/update-grub.8.gz)

I found the solution to my little conundrum. It was simply a matter of me having been unable to understand that

# groot=(hd0,0) 

Really *meant* just that. I had thought that the "commenting #" had to be removed - but it most certainly shouldn't.

So, changing the line to read

# groot=(hd0,1)

and a fresh update-grub solved my entire problem.

Thanks for trying, anyways.

> 
Like I said, update-grub doesn't autodetect anything. Running update-grub (or installing new kernel) reads the default options from the very same file, and then creates new kernel boot lines based on those options.


Yeah, I found the same info =)

---

