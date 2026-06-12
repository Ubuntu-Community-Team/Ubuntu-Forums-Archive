---
title: "Grub issues. booting into linux partition"
date: 2012-10-15
forum: General Help
---

### Post by Hachi-Roku on 2012-10-15
Grub bootloader doesn't see ubuntu partition.
See's windows.

Ok... So 2 weeks ago I did the run-of-the-mill update via the icon on the taskbar and BOOM. Next time i booted i was into the land of Grub rescue. No boot loader, no nothing. Panic :). 

Been 2 weeks of researching and trying workarounds but its not happening.

I run a tripple boot with 2 windows and 1 ubuntu OS's.

I've booted into the live disc and got back the grub bootloader with my windows partitions... and here's where it gets odd..

It's my UBUNTU partiton that is not being recognised!!

Now, running the triple boot I've of course ran into the problems previously where windows is not recognised and I've had to do manual entries...but I've never had it before with a linux one. Linux is normally a solid performer.

So far:
I've grub installed/updated like a boss (countless times). Mounting, chroot-ing etc.I've read many threads on here and elsewhere. There is a lot for windows but again... not a linux partition.

I've ran the boot info script, wasn't too enlightening.
And just now I've gone into the grub.d area and have been messing with etc/grub.d/40_custom to make a manual entry for linux.

I don't like this because it's a bit of a manual contrived way. But I need it working. I added this into 40_custom, but still no luck.

```
menuentry "Ubuntu lucid" {
    insmod part_gpt
    insmod ext4
    set root=(hd0,7)
        linux /vmlinuz root=/dev/sda7 ro quiet splash
        initrd /initrd.img
}
```

Then ubuntu shows in the menu!!! but executing the option I get output:
error: file not found
error: file not found
error: you must load kernel first.


When Im updating grub I have /dev/sda7 (ubuntu) mounted. If i dont i get grub error 21.

I know grub is updating as im toggling the grub beep on and off everytime i mess with it... as a sense check.

On the bootmenu there are no memtest entries (removed them about a year ago) and i remember *possibly* something going wrong with os_prober.

What diagnostics can I run and post up? Any advise appreciated as I'm now lost.

---

### Post by oldfred on 2012-10-15
Post link to BootInfo report.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by Hachi-Roku on 2012-10-15
Thanks for the help

Ive attached a text file with the boot info report. I copied and pasted out of terminal so if it's misaligned... that's why :).

Does anything unusual jump out at you?

I notice that in this case os prober finds the linux partition... hmm.

It's in 2 parts because it exceeded the max attachment limit for a .txt.

Thanks

---

### Post by oldfred on 2012-10-15
The link is a bit easier. 

I am not seeing any bootable files in the script. Neither Windows nor Ubuntu.

Windows has these files to boot. And if you have two Windows installs the second moves its boot files to the active partition or the boot flagged partition. So all your Windows boot files should be in sda2. Check and see is script missed these files somewhere on your Windows system. Script only looks in standard location.
Windows Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

Do you have a Windows repairCD or USB?  Xp does have boot files in backup locations or on installCD. Vista normally needs repairCD.

Same with Linux. Script normally shows grub files which you have but then none of  the kernels and init files. And the links in / (root) to the most recent kernel to boot like you are trying to do. None are shown. And when you last ran the grub update, it managed to run, but did not find any kernels so you have nothing in boot menu.

You may be able to chroot into Ubuntu with Boot-Repair and run these commands. Anything after # is comment, do not type.

#Then run whatever other commands needed - no sudo needed if chroot (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
#Commands once in chroot:
#if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

---

### Post by Hachi-Roku on 2012-10-20
Yeah, I would have used the link but the dialogue didn't provide one like it did in the example screen shots :(. 
I'm using windows right now and both my windows boot so there is boot files somewhere, also I know I have some initrd etc. files in my /, so I think the script may have missed them but I don't know how that's possible. I remember some years ago getting the triple boot to work took a lot of fiddling so maybe the windows boot files are in a super weird location. not sure.

Trying your suggested commands now. Fingers crossed. I'll report back soon. I'll likely miss out the dist-upgrade as I don't want the latest distro, I can't stand the unity gui :).

cheers

---

### Post by Hachi-Roku on 2012-10-20
No luck :(. Got several errors on the update/grade commands. Can't resolve hosts etc which seem to be networking errors, but of course im on a LAN cable and other internet operations are working fine. Some packages seemed to update but didnt help my situation.

Where is the kernel normally located?

I've made an entry for ubuntu in my 40_custom. but when I choose the entry in grub bootloader i get 3 errors and the last one says "you must load kernel first".

What command can i use in 40_custom to load the kernel. (after I've sussed if I actually have one) ??

This is my ubuntu entry atm;

```
menuentry "Ubuntu 10 Lucid" {
insmod ext2
insmod ext4
   	
set root='(hd0,7)'
        
linux /vmlinuz root=/dev/sda7/ ro quiet splash
        
initrd /initrd.img

}



```

thanks!!

---

### Post by oldfred on 2012-10-20
There is only one insmod for the ext family of formats - ext2, so perhaps your entry of ext4 causes an issue? Also not sure if trailing slash makes a difference or not, it normally is root= /dev/sda7 with not slash at end. See link below for more examples.

Your entry otherwise looks ok. We are seeing were if often shows an error of partition not existing, but wait a minute & it boots with your style entry and grub 1.99.

You entry is based on the links to the correct kernel in /boot being correct. Sometimes links are broken even if kernels are there. If kernels are not there you can chroot into an otherwise good system and reinstall them or backup your data and reinstall.

How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)

---

