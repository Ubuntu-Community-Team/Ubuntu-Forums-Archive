---
title: "No disk decryption password prompt on boot"
date: 2022-11-22
forum: General Help
---

### Post by richterbg on 2022-11-22
I am running Ubuntu 20.04.5 LTS with full disk encryption. After the last update, the password prompt for disk decryption disappeared. The screen just goes blank after I choose Ubuntu in Grub. Basically, I need to go to recovery and choose to scan for missing packages. The interface there prompts me to enter the password for disk decryption, and then I can proceed to normal boot.


I will be grateful to any suggestions on how to return the prompt back.

---

### Post by MAFoElffen on 2022-11-22
I have to pick my wife up... Will be back in a few hours.

Basically, at the grub menu, press <E> to go into edit mode > <Arrow down> until you get to the line that begins with "linux" > <Arrow-Right> and remove the word "quiet". Press <Cntrl><X> to boot.

That should let you see the boot messages until it gets to the encryption pass-phrase...

Once you get booted, edit /etc/default/grub with sudo permissions. Remove "quiet" from the Grub boot line. Save. Then 
```

sudo update-grub

```

If none of that works, post back with a photo of where it hangs... Be back in a few hours.

---

### Post by richterbg on 2022-11-23
I managed to enable the debugging output. 

At first, it was stalling while dealing with my Logitech keyboard. After I changed to a different USB port, it started stalling at some VGA-related lines. 

I've attached the screenshots. 

Thank you!

---

### Post by MAFoElffen on 2022-11-23
Describe your encrption... Did you install with LUKS or an encrypted lvm home?

---

### Post by richterbg on 2022-11-23
I guess it is LUKS, because it is a full disk encryption, applied during the initial installation.

---

### Post by MAFoElffen on 2022-11-23
Here is how I open LUKS encrypted volumes from a LiveCD before running the 'boot-info' script on an ecrytpted system:
```

sudo -i

apt-get update
apt-get install lvm2 cryptsetup
modprobe dm-crypt

DISK=$(lsblk -o NAME | grep -v 'loop\|NAME' | head -n 1 )

# Or modify next line to the encrypted disk:
export DEV="/dev/$DISK"

export DM="${DEV##*/}"

export DEVP="${DEV}$( if [[ "$DEV" =~ "nvme" ]]; then echo "p"; fi )"

export DM="${DM}$( if [[ "$DM" =~ "nvme" ]]; then echo "p"; fi )"

sgdisk --print $DEV
## Sample Output:
#Disk /dev/vda: 52428800 sectors, 25.0 GiB
#Sector size (logical/physical): 512/512 bytes
#Disk identifier (GUID): F55FCB42-F356-4C7B-A747-5D046D7B8907
#Partition table holds up to 128 entries
#Main partition table begins at sector 2 and ends at sector 33
#First usable sector is 34, last usable sector is 52428766
#Partitions will be aligned on 2048-sector boundaries
#Total free space is 2014 sectors (1007.0 KiB)
#
#Number  Start (sector)    End (sector)  Size       Code  Name
#   1            2048            6143   2.0 MiB     EF02  GRUB
#   2            6144          268287   128.0 MiB   EF00  EFI-SP
#   3          268288         1841151   768.0 MiB   8301  /boot
#   5         1841152        52428766   24.1 GiB    8301  rootfs

ls /dev/mapper/
##Sample Output:
#control  LUKS_BOOT  ubuntu--vg-root  ubuntu--vg-swap_1  vda5_crypt

cryptsetup open ${DEVP}3 LUKS_BOOT
#Enter passphrase for /dev/vda3: 


cryptsetup open ${DEVP}5 ${DM}5_crypt
#Enter passphrase for /dev/vda5:

```

More to follow in next post...

---

### Post by richterbg on 2022-11-23
Actually, I can access my computer via the recovery mode. It allows me to decrypt the disk and then to proceed to normal boot. Of course, it is cumbersome and not what the normal login process should be, and what it used to be... So, what I would like to achieve is to restore the standard boot process where I get a prompt to decrypt the disk and then log in to my desktop.

---

### Post by MAFoElffen on 2022-11-23
Using recovery mode > network > drop to root prompt...

What happens after you do a
```

update-grub
update-initramfs

```
???

---

### Post by richterbg on 2022-11-23
Well, update-grub did output the same information as when I do update and there is a kernel update. 

update-initramfs requires some options, and I really don't know which one to choose. 

However, I noticed something else. When the screen appears to hang at boot, I tried to enter the decryption password, although I don't have a prompt. Then the boot proceeded. It loaded the ubuntu login screen. After I entered the password for my user, the screen went black for a while (which didn't happen before), and then loaded my desktop. Something is definitely misconfigured, but I do lack the knowledge to fix it. Anyway, it kinda works...

---

### Post by MAFoElffen on 2022-11-23
Sorry...
```

update-initramfs -u

```

---

### Post by MAFoElffen on 2022-11-23
i just replicated your problem spinning up a VM with LUKS2... What I posted in post #2 worked.

---

### Post by MAFoElffen on 2022-11-24
I can confirm it is a problem with an unknown, unidentified update.

If I spin up a fresh instance of Ubuntu Desktop with encryption, of 20.04 or 22.04 from an install, it works fine. If I apply "any updates", the startup panel remains dark, with no prompt for the passphrase. If I wait a minute and enter the passphrase (as if the passphrase prompt was there), it continues the the Graphical Logon Panel. So it is affecting both 20.004 and 22.04.

If I delete "quiet" from the Linux Kernel boot parameters, as described in post #2, then it displays the boot messages, and does display the encryption passphrase prompt.It is a Bug that should be reported at Launchpad. The title should be something like: "Encryption Passphrase Prompt does not display." Since you are someone who is having this problem on real hardware, please report it.

Link this thread to it. Link Post #2 as a work-around. Please edit post #1 and add "LUKS2" as a tag. File the bug against luks2. Ensure you add the wording "This problem affects multiple Users."

Post a link to the Launchpad Bug Report back here, and I will join it and add details to the Bug Report.

---

