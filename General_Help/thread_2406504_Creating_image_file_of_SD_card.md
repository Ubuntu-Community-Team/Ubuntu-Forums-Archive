---
title: "Creating image file of SD card"
date: 2018-11-21
forum: General Help
---

### Post by nonetheless on 2018-11-21
I want to create an image of SD card for backup. Gnome Disk Utility is not detecting any SD card. Also checked with ***sudo fdisk -l ***with no SD card detection.

Any idea how can I create the image file of that SD card in my PC running Ubuntu 16.04.

---

### Post by ajgreeny on 2018-11-21
Where has that sd card come from; what filesystem is on it?

We can not really help with the minimal info you've given us.
Plug it in and then run command ```
dmesg | tail -n 20
``` and show us the output back here.

Please use **Code-Tags** for terminal output to show that text in a more readable format, the same as it is in the terminal, not as plain text. See my signature below for a **How-to**

---

### Post by nonetheless on 2018-11-22
I use this sd card in my android phone. I don't know its filesystem. I didn't check earlier and now it's not detected, is there any other way to know the filesystem ?

SD adapter is also not working, so I've put the card on another phone and connected to the pc via USB.

Here's the result of the code :

```
dmesg | tail -n 20

[13466.287583] pcieport 0000:00:1c.0:   device [8086:9d14] error status/mask=00001000/00002000
[13466.287594] pcieport 0000:00:1c.0:    [12] Replay Timer Timeout  
[13784.255749] pcieport 0000:00:1c.0: AER: Corrected error received: id=00e0
[13784.255777] pcieport 0000:00:1c.0: PCIe Bus Error: severity=Corrected, type=Data Link Layer, id=00e0(Transmitter ID)
[13784.255791] pcieport 0000:00:1c.0:   device [8086:9d14] error status/mask=00001000/00002000
[13784.255803] pcieport 0000:00:1c.0:    [12] Replay Timer Timeout  
[16375.081217] mmc0: error -110 whilst initialising SD card
[16562.695425] usb 1-3: new high-speed USB device number 5 using xhci_hcd
[16562.880991] usb 1-3: New USB device found, idVendor=22b8, idProduct=2e82
[16562.881006] usb 1-3: New USB device strings: Mfr=2, Product=3, SerialNumber=4
[16562.881016] usb 1-3: Product: XT1706
[16562.881025] usb 1-3: Manufacturer: MediaTek
[16562.881034] usb 1-3: SerialNumber: HKE6FPEP
[16584.138920] usb 1-3: USB disconnect, device number 5
[16584.561587] usb 1-3: new high-speed USB device number 6 using xhci_hcd
[16584.746993] usb 1-3: New USB device found, idVendor=22b8, idProduct=2e82
[16584.747012] usb 1-3: New USB device strings: Mfr=2, Product=3, SerialNumber=4
[16584.747025] usb 1-3: Product: XT1706
[16584.747036] usb 1-3: Manufacturer: MediaTek
[16584.747047] usb 1-3: SerialNumber: HKE6FPEP


```

---

### Post by ajgreeny on 2018-11-22
I assume this SD card is a MediaTek card and that it is detected by the system, even though apparently not mounted successfully.

I am no expert in this but it might be useful to see the output of ```
sudo blkid -c /dev/null
``` in terminal to see if that sees it in any way.
Please use **Code-Tags** as you did last time for terminal output to show that text in a more readable format, the same as it is in the terminal, not as plain text. See my signature below for a **How-to**

---

### Post by nonetheless on 2018-11-22
My card is a SanDisk one. I guess MediaTek is related to the phone as this product no 
```
[16562.881016] usb 1-3: Product: XT1706
``` 
relates to my phone model. And I searched, the phone has SoC by MediaTek.

Code output :
```
sudo blkid -c /dev/null

/dev/sda1: UUID="917b4de3-c935-4909-a72e-1c594f60d9e7" TYPE="ext4" PARTUUID="d39f7b15-01"
/dev/sda2: UUID="af89d536-745d-4899-971b-27cba56930be" TYPE="ext4" PARTUUID="d39f7b15-02"
/dev/sda3: UUID="d28ad152-fb8b-456d-986e-c3776154daf0" TYPE="swap" PARTUUID="d39f7b15-03"

```

---

### Post by angisky on 2018-11-22
Looks like it's not mounted. If you have a GUI on your setup you can try viewing the files and it should automatically mount when you go in. Then you can go back to fdisk and it should be listed on fdisk -l.

Edit: I found this to do it from terminal 
[https://askubuntu.com/questions/37767/how-to-access-a-usb-flash-drive-from-the-terminal](https://askubuntu.com/questions/37767/how-to-access-a-usb-flash-drive-from-the-terminal)

---

### Post by nonetheless on 2018-11-23
Oh that link has a LOT to go through :confused:
And ...I gotta run now !! 
I will be back later with some results from those instructions:cool:

---

### Post by nonetheless on 2018-12-07
I didn't get enough time to do this earlier and i'm sorry for that..but here I am now with some results from the link.

1. ```
lsblk
```

```
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 931.5G  0 disk 
&#9500;&#9472;sda1   8:1    0  95.4G  0 part /
&#9500;&#9472;sda2   8:2    0 826.6G  0 part /home
&#9492;&#9472;sda3   8:3    0   9.5G  0 part [SWAP]
sr0     11:0    1  1024M  0 rom  

```

so, the SD card is not showing in here.

2. ```
sudo blkid
``` 
```
/dev/sda1: UUID="917b4de3-c935-4909-a72e-1c594f60d9e7" TYPE="ext4" PARTUUID="d39f7b15-01"
/dev/sda2: UUID="af89d536-745d-4899-971b-27cba56930be" TYPE="ext4" PARTUUID="d39f7b15-02"
/dev/sda3: UUID="d28ad152-fb8b-456d-986e-c3776154daf0" TYPE="swap" PARTUUID="d39f7b15-03"

```

3. Also, ```
sudo fdisk -l
```

```
Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xd39f7b15

Device     Boot      Start        End    Sectors   Size Id Type
/dev/sda1  *          2048  199999487  199997440  95.4G 83 Linux
/dev/sda2        199999488 1933524991 1733525504 826.6G 83 Linux
/dev/sda3       1933524992 1953523711   19998720   9.5G 82 Linux swap / Solaris


```

So, none of them reads the card.

Here I want to say one thing. Though it is not 'mounted',ie, not showing in the terminal , somehow I can share files between the pc and sd card directly. Is that weird ?

---

