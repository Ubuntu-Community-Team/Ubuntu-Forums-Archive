---
title: "How do I move Grub2 to a different partition"
date: 2014-01-12
forum: General Help
---

### Post by PopsTheSailor on 2014-01-12
I have a setup that has 4 partitions. They are Win 7, Ubuntu 13.10, Xubuntu 13.10 and Mint 16. Right now, Grub is on Xubuntu. I want it on Mint. That's the partition / install that I primarily use and want GRUB2 on it. Here is the output from sudo blkid

/dev/sda1: LABEL="System" UUID="CCD6490ED648F9EA" TYPE="ntfs" 
/dev/sda2: LABEL="TI106033W0C" UUID="A47677F27677C418" TYPE="ntfs" 
/dev/sda3: LABEL="Shared" UUID="BC168CE2168C9ED0" TYPE="ntfs" 
/dev/sda5: LABEL="Ubuntu" UUID="91baa88c-7f57-4014-9fae-d788bd00f499" TYPE="ext4" 
/dev/sda6: LABEL="Mint" UUID="663d6c75-af4d-4f5d-8b09-21f0bf1ecbda" TYPE="ext4" 
/dev/sda7: LABEL="FreeOldSwap" UUID="17c06f57-50ce-4e85-b6e3-d779a5a89a99" TYPE="ext4" 
/dev/sda8: LABEL="Xubuntu" UUID="f03ea7f4-bd09-4bf2-abf8-44843a6caec5" TYPE="ext4" 

I have tried the command

sudo grub-install -f /dev/sda6
sudo update-grub2

But that didn't do it. How do I set sda6 to be where Grub2 is installed?

---

### Post by carl4926 on 2014-01-12
If you don't want to use the MBR you can install grub with
grub-install /dev/sda6
but you also need to set that partition with the boot flag

---

### Post by deadflowr on 2014-01-13
The easiest thing to do would be to boot into mint and run
```
sudo grub-install /dev/sda
```
This will install grub to the mbr rather than a partition. Installing to a partition isn't really recommeneded but is possible, so...
Another method I think works is to mount the mint partition and use the --boot-directory=  option
I would look something like this
```
sudo mount /dev/sda6 /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sda
```
You can find where grub is loading from with
```
grub-probe -t device /boot/grub

```
But I will still say that simply booting into mint and running the grub-install /dev/sda command is by far the easiest way to go.
And possibly the safest.

---

### Post by carl4926 on 2014-01-13
I agree with the above

---

### Post by deadflowr on 2014-01-13
I would add, if all falls apart [boot repair]("https://help.ubuntu.com/community/Boot-Repair") is your friend.
It's saved many a sunken ship.

---

### Post by carl4926 on 2014-01-13
> **deadflowr said:**
> I would add, if all falls apart [boot repair]("https://help.ubuntu.com/community/Boot-Repair") is your friend.
It's saved many a sunken ship.
I always use the MBR and never yet had to rescue myself

---

### Post by mikodo on 2014-01-13
I am no expert, so use this with your judgment.

Boot into the Mint partition. Then:

                        sudo fdisk -l
#if it's "/dev/sda" then just run:
sudo grub-install /dev/sda
#If that returns any errors run:
sudo grub-install --recheck /dev/sda
 
Then: 
                        
sudo update-grub

                        That should refresh the Grub 2 menu files (/boot/grub and /etc/grub.d folders and the /etc/default/grub file) in the mint install and give it control of the boot process. I think that is what you want.

As stated earlier, Grub 2 should not be installed to a partition, but to devices. ie. a drive. (dev/sda).


  Hope that helps.

---

### Post by PopsTheSailor on 2014-01-13
Well, I'm always up for taking the easy way to do things. I ussued the sudo grub-install /dev/sda and it worked perfectly!

I'm marking this as SOLVED.

---

