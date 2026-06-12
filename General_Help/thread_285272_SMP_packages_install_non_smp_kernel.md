---
title: "SMP packages install non smp kernel?"
date: 2006-10-26
forum: General Help
---

### Post by st00ner on 2006-10-26
i noticed in 6.10 now both linux-k7-smp and linux-686-smp both just install linux generic. what gives? my computer cannot even boot the generic kernel(even freebsd generic can boot on my computer lol). Was there a reason for this? i am completely lost and about to build my own kernel, im just curious as to why the smp packages point to the generic kernel....

---

### Post by lime4x4 on 2006-10-26
same here

---

### Post by st00ner on 2006-10-26
well since it seems that more than one person has this issue, and being such a majour issue, im sure it will be solved quickly... i hope at least

---

### Post by hotani on 2006-10-26
yep - Just upgraded to 6.10, using the "generic" kernel and am using only ONE core of my 3800+ X2.

---

### Post by dcarpenter on 2006-10-26
Same problem here... I installed edgy just a while ago via the regular desktop install cd and after reboot, grub greeted me with only 1 kernel option, generic.  I've never had this problem with a previous release of ubuntu.

---

### Post by Ghost Freeman on 2006-10-26
From what's been said on IRC, there's no longer a need for the various kernels, and that 'generic' is meant to supersede it. Maybe someone else can clarify this.

Makes no sense to me either, but i'm running generic right now and it has picked up support for my 686-smp processor.

---

### Post by hotani on 2006-10-26
All I know is that in the system monitor it used to show 2 CPUs, now it shows 1. My CPU monitor used to never go to 100%, now it is maxxed out on a regular basis. 

Not claiming to be the sharpest tool in the shed or anything, but it looks like I'm down to one CPU.

---

### Post by madmetal on 2006-10-26
another thread about generic kernel..
[http://www.ubuntuforums.org/showthread.php?t=283056](http://www.ubuntuforums.org/showthread.php?t=283056)

generic includes both smp and k7 support and optimization (as far as i know..)

---

### Post by hotani on 2006-10-26
generic kernel will NOT BOOT MY MACHINE. Neither will the K7. Both just hang without even showing the progress bar. 

Right now, I'm using the only thing that will boot which is 2.6.17-10-386. If there is another one that would work, and say... you know, utilize both cores of my chip that would be AWESOME!

Edgy has done a bang up job of wrecking what was a perfectly good system up until a couple of hours ago. Upgrades are supposed to *UP*grade - RIGHT?

---

### Post by sillygit on 2006-10-26
I'm having exactly the same issue as hotani.  My machine will only boot if I use 2.6.17-10-386... :( 

As a side note, I can't seem to start the terminal in Gnome.  A minimized window appears with "Starting Terminal" but it just disappears after a few seconds...

---

### Post by Pinoy915 on 2006-10-26
I've just recently installed Ubuntu 6.10 and smp is working. I'm using AMD64 X2 4200+ with the 32 bit Ubuntu. Man, it seems a bit more responsive than when I was using Dapper64.

---

### Post by st00ner on 2006-10-26
yeah... if it would boot im sure it would work. here is my hardware
Gigabyte Mobo nForce4 SLI
Athlon X2 3800+
GeForce 7800 GT
1 GB DDR Ram
Lynksis EG1032 Gigabit Adapter
Sound Blaster Audigy SE

Ubuntu 6.10 x86

If yours wont boot, please post your hardware

---

### Post by hotani on 2006-10-26
sounds like a similar setup to mine:

Gigabyte GA-M55 AM2 mb
AMD 3800+ X2 CPU
GeForce 7600GT
2GB Corsair RAM

Ubuntu 6.10 386

I saw in [another thread](http://ubuntuforums.org/showthread.php?t=276358) that it could be related to the nvidia driver. However, in that thread it sounded like those problems had been resolved. Obviously not for us, if it is the same issue at all.

Plus - and I'm not sure if all this is related or not - when I run glxgears, it works but takes 100% CPU - I know it didn't do that before; it should all be offloaded to the GPU right?

---

### Post by st00ner on 2006-10-26
yeah mine does to :o(100% cpu glxgears). could this be the nVIdia proprietary driver? im going to switch to vesa but i dont think that will do any good :[

hmm we both have gigabyte mobos and GeForce 7 series

last time i tried to boot generic, my sound card and nic stoped working, and i had to manaully remove them, flash the bios, and put them back in. wish me luck :[

---

### Post by sillygit on 2006-10-26
I'm running:

MSI RS482M4/RX480M4 Series (with the onboard ATI video disabled)
nVidia GeForce 6600 GT

---

### Post by st00ner on 2006-10-26
Ok here is a temporary solution if you still have an old SMP kernel:

apt get the xorg vesa driver.
then edit your /etc/X11/xorg.conf

Section "Device"
	Identifier	"Keep the same"
	Driver		"vesa"
	BusID		"Keep the same"
EndSection

you wont have 3d acceleration, but you will have dual core. i dont play many games, so i can live with it for now. Ubuntu team please helpe get a more compatible SMP kernel like in 6.06 :[

When i boot linux-generic, the message i get stuck at is
waiting for root....

---

### Post by dcarpenter on 2006-10-27
Ah, I did not realize they changed this.  That would explain why in Synaptic linux-686-smp says "Made Obsolete by Generic" or something to that nature.  It appears that hyper threading is functioning normal as well.  I have 2 cpu's in system monitor.

---

### Post by Ronbo on 2006-10-27
After the original install according to the system monitor I show CPU1 and CPU2.  After I install the NVIDIA drivers I only show CPU1 in the system monitor.  I am running an Asus MB and an Athlon X2 3800.  Just reinstalled and waiting to hear about a fix for the problem.  For some reason installing the Nvidia drivers seems to install linux-image-2.16.17-10-386.

---

### Post by autocrosser on 2006-10-27
One more step for Hyperthreading--(from my /boot/grub/menu.lst)

title        Edgy, kernel 2.6.17-10-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ht=on ro splash  (note the "ht=on")
initrd        /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

For you guys with the K7 stuff--you might take a look at your /etc/fstab---I had a BIG problem about two months ago when they changed to UUID in fstab--I had hangs at /root---if you have this prob--revert (if it was changed) fstab back to /dev/whatever & recheck--It took me several days to find that one--also remember that you are now using upstart which changes boot by not loading un-needed items--could cause problems in some cases (I do not know a roll-back for this one)


> **dcarpenter said:**
> Ah, I did not realize they changed this.  That would explain why in Synaptic linux-686-smp says "Made Obsolete by Generic" or something to that nature.  It appears that hyper threading is functioning normal as well.  I have 2 cpu's in system monitor.

as for the -386---use Synaptic & install the-generic kernel to get your dual back---
> After the original install according to the system monitor I show CPU1 and CPU2. After I install the NVIDIA drivers I only show CPU1 in the system monitor. I am running an Asus MB and an Athlon X2 3800. Just reinstalled and waiting to hear about a fix for the problem. For some reason installing the Nvidia drivers seems to install linux-image-2.16.17-10-386.


---

### Post by hotani on 2006-10-27
Mine does seem to be hanging on a drive when I attempt to do generic in recovery mode, but fstab does not seem to have been changed. 

This is what happens when I try to boot with generic kernel, it hangs here:
[img]http://hotani.net/images/20061026_edgy1.jpg[/img]

---

### Post by autocrosser on 2006-10-27
OK--try this---instead of /dev/hda---use /dev/sda (or whatever your numbers are) AND Have a bootable Ubuntu CD close at hand-- There was a bit of trouble with the hda/sda in fstab & you might be caught by that---Of course, if it works for the generic kernel--it won't work for the -386 one--and the third option is it won't work at all & you'll need to boot with a CD & re-edit your /etc/fstab (by creating a /dev/whatever & then a /mkdir /mnt/whatever, then mounting it)

---

### Post by hotani on 2006-10-27
holy hell. Ok, I'm taking my single CPU and bowing out for the evening. I'll try the fstab shuffle tomorrow night.

I have a RAID 1 setup as well as an LVM so this could get ugly.

---

### Post by sillygit on 2006-10-27
so is this only a problem for those that have done a `apt-get dist-upgrade`?

---

### Post by hotani on 2006-10-27
Apparently not, did mine with [gksu "update-manager -c"].

---

### Post by sillygit on 2006-10-27
my question was a little to specific... :)

is the problem only affecting machines that have undergone a distribution upgrade?

---

### Post by hotani on 2006-10-27
Yes, this is a new "feature" of Edgy.

---

### Post by mega on 2006-10-27
I also cannot boot off the generic kernel

system is a dell 9100 dual core p4

nvidia 7300GS

I cant get dual core to work, and I cant get the nvidia card to work in direct mode

[IMG]http://freddy.geekopolis.com/gallery2/d/4818-2/DSC_1164.JPG[/IMG]

---

### Post by hotani on 2006-10-27
I must be blind, but [this thread](http://ubuntuforums.org/showthread.php?t=282956) appears to have a fix - wish I had found it yesterday. 

Can anyone confirm? I can do the CLI stuff from here but I won't be able to really test and reboot till I get home tonight. Yeah, I can reboot from here but I like to within reach of that button in case it doesn't work!

---

### Post by mega on 2006-10-27
thanks that fixed it

now the only thing left is the nvidia driver

mega@mainpc:~$ glxinfo | more
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4

---

### Post by ~LoKe on 2006-10-27
I've been using both cores along with the generic kernel for the past week.

---

### Post by hotani on 2006-10-27
FIXED! That thread did the trick - I have 2 CPUs again. :D

glxgears still seems to be using a ton of CPU, but one thing at a time...

---

