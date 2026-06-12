---
title: "Why Doesn’t A Clone Of My Bootable ubuntu Boot?"
date: 2021-01-15
forum: General Help
---

### Post by box02-0 on 2021-01-15
Ubuntu 20.04 on a DELL 7791 Laptop
1tb Internal SATA SSD bootable ubuntu
1tb External SATA SSD plugged into laptop via USBC to Esata Cable

Hi.

I am trying to make a clone of a 1tb Internal SATA SSD bootable ubuntu (sda) onto a 1tb External SATA SSD  (sdc).

I boot with Gparted Live, and go into terminal.

     sudo dd if=/dev/sda of=/dev/sdc bs=1024  (Took 44 minutes)

F12 on the DELL displays the internal ubuntu as one of the bootable options, but the destination clone does not appear at all.

The destination SSD looks identical to the source, however, it is  not bootable. (Both the ubuntu partitions have identical uuid's, as expected.)

How come?

Thanks,
M...

---

### Post by TheFu on 2021-01-15
Cloned disks cannot be connected at the same time after the cloning ends.  All the unique UUIDs are cloned too, so they are not unique any more. That's not good.

That's my first guess. There are other possible issues too, but more details would be needed like did you force new uuids and change the fstab to be consistent?

---

### Post by box02-0 on 2021-01-15
> **TheFu said:**
> Cloned disks cannot be connected at the same time after the cloning ends.  All he unique UUIDs are cloned too, so they are not unique any more.

That's my first guess. There are other possible issues too, but more details would be needed like dd you force new uuids and change the fstab to be consistent?

Hi.
No I did not  touch UUIDs or fstab. I just did the "dd" as above.
M...

---

### Post by QIII on 2021-01-15
The next question was implicit in TheFu's response:  did you disconnect the original drive before attempting to boot?  Did you alter your BIOS/EFI to attempt to boot first to the cloned drive?

---

### Post by TheFu on 2021-01-15
> **box02-0 said:**
> Hi.
No I did not  touch UUIDs or fstab. I just did the "dd" as above.
M...

Well, that's great if you put the drive into a different system. Won't work if both drives are connected to a single system or more correctly, won't work with consistent results.

---

### Post by HermanAB on 2021-01-15
The problem is that if you clone a disk, then the UUIDs of the old disks are also copied in the /etc/fstab and /etc/mtab files, while the UUIDs of the new disks are different.  The resulting clone cannot boot, since the system goes looking for the old disk.

Making a clone of a Linux disk is generally a waste of time and disks.  It is usually better to only backup your data and when your system fails, install a fresh version of Linux and restore your data.

There is no point in backing up the whole Linux distribution.  There are thousands of copies at universities around the world already.

---

### Post by box02-0 on 2021-01-17
Hi.

Thanks for all the responses.

Yes I thought duplicate UUID's might be an issue. But I would think that a cloned disk would at least show up as a bootable option when I hit F12 on my DELL. The Internal shows up, but the external does not show at all.

I would never run a system live with 2 identical drives as I know there would be issues with duplicate UUIDs.

When I boot with the GParted USB, I can clearly see both drives which look identical. 

Is there a difference because I'm trying to boot via USBC vs the internal drive? I just want to be able to determine that the clone is bootable - not actually boot it.

I have lots of custom software on my ubuntu. Not easy to rebuild from an iso off the internet. As a result, I typically clone drives as a backup. If an internal drive fails, it makes a recovery easy - just plug in the cloned backup and minutes later it's business as usual.

To review - I booted with Gparted, went into terminal, did the "DD clone", booted the DELL with an F12, and did **not** see the cloned drive as a possible bootable drive.

Thanks,
M....

---

### Post by rbmorse on 2021-01-17
Does the ESP partition on the clone have the boot and ESP flags set?  You can check with gparted.

---

### Post by oldfred on 2021-01-17
Just like live installer, external drives boot from /EFI/Boot/bootx64.efi which is an UEFI:USB entry in UEFI boot menu.
Not from an 'ubuntu' entry.
You can create an ubuntu entry, but when drives are disconnected UEFI normally forgets specific entries.
You do have to have ESP - efi system partition as FAT32 with esp/boot flag.

---

### Post by tea for one on 2021-01-17
Have you tried this?

Remove, isolate, de-activate your source SSD
Only leave the cloned disk accessible

Does it boot?

---

### Post by box02-0 on 2021-01-17
Hi.

Here is what gparted shows for the cloned SSD when I plug it into my Desktop Esata:

                                label       flag
/dev/sda      FAT32       esp        boot,esp

it all looks good.

In the DELL BIOS, I did try to disable the Internal SSD so that I could try to boot the External cloned SSD with no other drive in the system. The problem is that there is this silly NVME Optane 32gb drive which requires there to be some kind of a "fake" software RAID setup.

In order to disable the internal SATA drive, I had to turn off this software RAID flag, which I did. I then plugged in the cloned SSD (USBC to SATA), booted with an F12, and **NO** bootable drive showed up at all! This with ONLY the cloned SSD  plugged in.

Then, when I turned the software RAID flag back on and booted with an F12, the internal SSD did **NOT** show up. YIKES!! Scared the daylights out of me. 

I then ran DELL DIAGS from the BIOS, and it fixed the problem - the Internal SSD was once again, bootable.

In my desktop, the BIOS allows me to enable/disable any drive. The DELL BIOS does not seem to allow me to do that without possibly wiping out the boot flag on the Internal SSD. 

Bottom line is that I still can't boot the cloned SSD.

What to try next ??

Thanks,
M...

---

### Post by TheFu on 2021-01-17
Perhaps the planned disk-swap recovery method isn't going to work?

---

### Post by tea for one on 2021-01-18
> **box02-0 said:**
> The problem is that there is this silly NVME Optane 32gb drive which requires there to be some kind of a "fake" software RAID setup.

Is that a separate physical drive?
Are you dual booting with Windows 10?

Does this web site provide any help? [https://help.ubuntu.com/rst/](https://help.ubuntu.com/rst/)

I'm not at all familiar with RAID but there are some forum posts about turning off RAID and installing Ubuntu with AHCI.

---

### Post by box02-0 on 2021-01-18
Hi.

DELL 7791 UEFI laptop setup:

-512gb NVME that came with Windows 10 installed.

-32gb NVME drive that is the DELL Optane drive cache/accelerator that is entirely controlled by DELL. In order to take advantage of the Optane feature (speed), the system comes from DELL with a Software RAID setup. It is not a conventional multiple drive RAID setup &#8211; that is all I know about it. Disabling this Software Raid flag in the BIOS wipes out the Windows Boot Manager for the 512gb NVME (ask me how I know this.&#8230;).

- I added a  1tb SATA SSD where I installed ubuntu 20.04.

- Each of the drives has multiple partitions where data files are stored.

- To backup either of the drives, I plug in a 1tb or 512gb SSD via a SATA to USBC cable. For Windows backup (512gb NVME), we use Macrium which allows you to clone partitions. For ubuntu backup (1tb SSD), I use Gparted to clone partitions (cut/paste), or it&#8217;s Terminal to &#8220;dd&#8221; clone the entire 1tb SSD.

The DELL laptop is actually my wife&#8217;s machine. I added ubuntu in order to wean her off of Windows. She boots with F12 and selects Windows or ubuntu. 

So it does appear that for whatever reason, the Cloned 1tb External SSD cannot be booted via F12 as the DELL Bios does not see it as a bootable drive (even though it is **identical** to the 1tb Internal SSD). 

I guess that's pretty much it.

Thanks for all your help. Stay Safe,
M....

---

### Post by dragonfly41 on 2021-01-18
I too am on  Dell (3268) with Windows 10 on internal drive and Ubuntu on external USB3 SSD.
I can only suggest trying to install ReFIND to give an alternative loader option in EFI folder. Works fine for me.

---

### Post by box02-0 on 2021-01-18
Hi dragonfly41.

I have downloaded "refind_0.12.0-1_amd64.deb".

I'm a little chicken to just install it.
 
Where does it install? How do I invoke it? 

Thanks for the tip.
M...

---

### Post by dragonfly41 on 2021-01-18
Basically refind can be safely installed either in your internal drive or in the external SSD (which I prefer).
Looking at my setup I have /boot/efi/EFI in external SSD and inside there I have
> Boot
> Dell
> Microsoft
> refind
> tools
> ubuntu

Now that partition I created before installing Ubuntu and it has boot flags set through Gparted.

When you boot up choose the loader (in boot menu) at ..
/boot/efi/EFI/refind/refind_x64.efi

Later you can hack refind.conf to customise the GUI.

[Google search for papers on refind written by Rob Smith]("https://askubuntu.com/questions/760875/any-downside-to-using-refind-instead-of-grub").

Refind does not overwrite grub installations - it adds to them.
When you install refind you point to your external bootable SSD.

---

### Post by tea for one on 2021-01-18
It wasn't clear from your original post that you had 3 separate drives. 

As Ubuntu is installed on a separate disk, which was added after purchase, it seems odd that you cannot then replace this disk and still boot an OS.
Possibly the cloning operation was not perfect as it cannot be tested.
A back up is never trustworthy until it is restored (similar to an insurance company until you want to make a claim ;))

Here's another suggestion:-

Make a bootable USB stick with [COLOR="#0000FF"]Clonezilla[/COLOR] [https://clonezilla.org/](https://clonezilla.org/)
Clone your Ubuntu SSD with the Device to Device option
Remove the source Ubuntu drive
Insert the cloned drive
Leave the Windows 512GB nvme and 32GB nvme Optane drives in situ so as not to interfere with the additional problem of losing the Windows boot manager.

To boot or not to boot, that is the question........

---

### Post by box02-0 on 2021-01-19
Thanks for the info.

I would really not remove the 2nd Internal SSD - very fragile connectors that were not designed to be plugged in/out very often. Ideally I could disable the drive through the BIOS, but DELL does not appear to allow that. 

I do have faith that "dd" made a proper clone. In my desktop (2 internal drives, one a clone of the other) after I clone the drive, I turn it off via the BIOS and boot with the backup and check it out. Then I turn the backup drive off and the active drive back on via the BIOS. Easy, peasy.

I will try refind. Sounds like a plan.

You've all been a big help. 

Stay Safe,
M...

---

### Post by dragonfly41 on 2021-01-19
Just for extra information I now keep my two external SSD's in an external docking bay which is connected to Dell only through a USB3 connection (USB3 is necessary for performance). This allows me to unplug SSD's or switch power off at docking bay.
If that setup is of interest I can post more details.

---

### Post by tea for one on 2021-01-19
> **box02-0 said:**
> I do have faith that "dd" made a proper clone. In my desktop (2 internal drives, one a clone of the other) after I clone the drive, I turn it off via the BIOS and boot with the backup and check it out. Then I turn the backup drive off and the active drive back on via the BIOS.

Is there anything preventing you from de-activating both your drives in your Desktop PC to discover if your laptop clone boots?

---

### Post by box02-0 on 2021-01-19
Hey dragonfly41.

I have pondered the same setup - external docking bay with  thunderbolt drives - fortunately the laptop has onboard thunderbolt. Prices of these tbolt drives are coming down.

Thanks again,
M...

---

