---
title: "Lubuntu 12.04 doesn't want to turn off"
date: 2013-02-14
forum: General Help
---

### Post by Maui 74 on 2013-02-14
Hi,
I have installed Lubuntu 12.04 on a old laptop (Compaq Presario 2100 / CPU AMD Athlon XP-m 2000+ / RAM 1GB / VGA 64MB ATI integrated).
The problem I couldn't solve is that when I turn off the laptop it doesn't want to complete the procedure and I have to force it pushing the power button.
I have already tried to change something in the grub file adding "acpi=force", "acpi=off", "noacpi" but nothing has changed.
Can anybody help me?
Thank you! ! !

---

### Post by Joao Lacerda on 2013-02-14
Hi friend.

You can try shutting it down from terminal as sudo, and see what happens.
with one of these command.

sudo shutdown -h now

sudo halt

sudo poweroff

Good luck.

---

### Post by offgridguy on 2013-02-14
Someone else with the same problem in this thread, not sure if these fixes will work for you or not.

[http://ubuntuforums.org/showthread.php?t=2107235&highlight=force+shutdown](http://ubuntuforums.org/showthread.php?t=2107235&highlight=force+shutdown)

---

### Post by jhilp on 2013-02-15
I had a similar issue with one of my older computers, and this fix worked with Ubuntu 12.04. I'm not certain if it will work with the Lubuntu spin or not. Here's the link to the original question:

[http://askubuntu.com/questions/125844/shutdown-does-not-power-off-computer](http://askubuntu.com/questions/125844/shutdown-does-not-power-off-computer)

The answer at the top of the list is the one that worked for me. I quote it here:

Type in terminal:
1. sudo gedit /etc/default/grub
2. Find the line: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
3. Change this to: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force"
4. Save the file and close the file. 5. Finally, in terminal: sudo update-grub

---

### Post by Maui 74 on 2013-02-15
....sorry guys I have tried all the things you have suggested to me but nothing happened...
Also if I use sudo shutdown -h now or sudo halt or sudo poweroff from terminal it turn off properly.
I have tried also "acpi=force" but doesn't work... :-(

---

### Post by sudodus on 2013-02-15
> **Maui 74 said:**
> ...
The problem I couldn't solve is that when I turn off the laptop it doesn't want to complete the procedure and I have to force it pushing the power button.
...
Avoid that kind of hard reset. It is likely to damage your file system (for example creating corrupted files). Instead use the unique feature of linux to make a soft reset even when it seems non-responsive.

While pressing

***alt + SysRq***

all the time, press slowly (one key per second)

***r e i s u b***

to reboot.

Now that you have this situation, I think some program will not close properly because of some error in the file system. Try to repair it like this:

Find which partition it is with the following commands:
```
sudo fdisk -lu
```
```
sudo blkid
```
```
df
```
Boot you computer from the Ubuntu install CD or USB drive. Check that the partition (probably your root partition or home partition (if separate)) is ***not mounted***

Run the following command
```
sudo e2fsck -f /dev/sdxy
```
where x is the drive letter and y is the partition number (for example /dev/sda6)

> **Maui 74 said:**
> ...
Also if I use sudo shutdown -h now or sudo halt or sudo poweroff from terminal it turn off properly.
...

The shutdown task itself works, but some task in the GUI shutdown procedure fails. Some weeks ago I could repair a similar problem (or the same problem) in Lubuntu 12.04 by repairing the file system.

Another thing to do is to make sure your system is up to date

```
sudo apt-get update
```
```
sudo apt-get upgrade
```
and if some packages are held back
```
sudo apt-get dist-upgrade
```

---

### Post by Maui 74 on 2013-02-15
@sudodus
this is the result

[B]Code:
sudo fdisk -lu[/B]

Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 testine, 63 settori/tracce, 3648 cilindri, totale 58605120 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Identificativo disco: 0x000dc48c

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    56641535    28319744   83  Linux
/dev/sda2        56643582    58603519      979969    5  Esteso
/dev/sda5        56643584    58603519      979968   82  Linux swap / Solaris

[B]Code:
sudo blkid[/B]

/dev/sda1: UUID="da2e29ea-a9a1-4cc5-93d6-e526c395fbde" TYPE="ext4" 
/dev/sda5: UUID="e047410a-f44a-4e61-a05c-6d245ed46f8b" TYPE="swap"

[B]Code:
df[/B]

File system    1K-blocchi   Usati Disponib. Uso% Montato su
/dev/sda1        27875196 4124120  22335092  16% /
udev               472848       8    472840   1% /dev
tmpfs              192236     732    191504   1% /run
none                 5120       0      5120   0% /run/lock
none               480584     176    480408   1% /run/shm
none               102400       8    102392   1% /run/user

...now what I have to do?

---

### Post by sudodus on 2013-02-16
> **Maui 74 said:**
> ...
**df**

File system    1K-blocchi   Usati Disponib. Uso% Montato su
[COLOR="Red"]/dev/sda1        27875196 4124120  22335092  16% /[/COLOR]
udev               472848       8    472840   1% /dev
tmpfs              192236     732    191504   1% /run
none                 5120       0      5120   0% /run/lock
none               480584     176    480408   1% /run/shm
none               102400       8    102392   1% /run/user

...now what I have to do?

Boot you computer from the Ubuntu install CD or USB drive. Check that the root partition is not mounted (with ***df***). Unmount if necessary with
```
sudo umount /dev/sda1
```
 
Run the following command
```
sudo e2fsck -f /dev/sda1
```
Reboot and check if normal shutdown works.

---

### Post by Maui 74 on 2013-02-16
...I have followed your suggestion and I did both

Code:
sudo umount /dev/sda1

and 

Code:
sudo e2fsck -f /dev/sda1

then reboot...
...but...
...nothing new...
While is turning off it is blocked with black screen and "*Asking all remaining processes to terminate..." line :(:(

---

### Post by Maui 74 on 2013-02-20
...any suggestion?
:( 
:confused:

---

### Post by sudodus on 2013-02-20
> **Maui 74 said:**
> ...any suggestion?
:( 
:confused:

Try **[FONT="Courier New"][SIZE="3"]acpi=noirq[/SIZE][/FONT]** according to this link

[[COLOR="Red"]http://askubuntu.com/questions/132143/stuck-on-reboot-and-shutdown[/COLOR]]("http://askubuntu.com/questions/132143/stuck-on-reboot-and-shutdown")

Remember ```
sudo update-grub
``` after editing **[FONT="Courier New"][SIZE="3"]/etc/default/grub[/SIZE][/FONT]**

---

### Post by MoebusNet on 2013-02-20
One other thing; have you downloaded the updates for Lubuntu 12.04? We are on Ubuntu 12.04.2 now, but Lubuntu only offers 12.04 and 12.10. I don't believe they have updated the 12.04 image to include the 12.04.2 updates, of which there are quite a few.

If I remember correctly, I initially had this issue until I updated everything. I hope this is a helpful suggestion.

---

### Post by Maui 74 on 2013-02-20
...done but notthing changed...

---

### Post by sudodus on 2013-02-20
[http://www.zoringroup.com/forum/viewtopic.php?f=4&t=2662](http://www.zoringroup.com/forum/viewtopic.php?f=4&t=2662)

Just hit the Enter key at this message: 'Asking all remaining processes to terminate'
--
By the way, is your system updated?

---

### Post by Maui 74 on 2013-02-21
I have tried to push enter key but again notthing....
 
The system is updated, yes... I have followed your suggestion to do 
Another thing to do is to make sure your system is up to date


Code:
sudo apt-get update
Code:
sudo apt-get upgrade
and if some packages are held back

Code:
sudo apt-get dist-upgrade

Is there any tool to check if the HDD is ok?

---

### Post by sudodus on 2013-02-21
> **Maui 74 said:**
> Is there any tool to check if the HDD is ok?

If the HDD is not too old, there should be S.M.A.R.T. information, that you might see in a bios menu or with ***smartctl*** from the smartmontools package
```
sudo apt-get install smartmontools
``` There are several options for example
```
sudo smartctl /dev/sda -a
```

You have already checked the file system with

```
sudo e2fsck -f /dev/sda1
``` but you can do it again. See post #8

---

### Post by Maui 74 on 2013-02-23
...in the end I have found a creative mode to solve the problem: I have installed Xubuntu 12.10 and everything works...

---

