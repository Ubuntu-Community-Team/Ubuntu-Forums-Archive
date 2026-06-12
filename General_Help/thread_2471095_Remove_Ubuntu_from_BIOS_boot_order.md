---
title: "Remove Ubuntu from BIOS boot order"
date: 2022-01-21
forum: General Help
---

### Post by tech291083 on 2022-01-21
Hi All,

I have been using Ubuntu for many years now and I must say that I just love it. But I am no Ubuntu expert by any means. Just a couple of weeks ago, I was just testing a new Seagate 1TB internal hard drive by installing Ubuntu on it. My was Ubuntu Desktop 21.10 64 bit.

I installed Ubuntu several times on this very hard drive over a period of many days and I realized that Ubuntu created an entry for itself each time it was installed in the boot order along with other physical devices such as hard drives and dvd-writers, which basically are displayed by their model numbers. 

I wanted to remove this Ubuntu entry from the boot order in motherboard settings and used a tool called rEFInd. It was very easy to use and I realized one thing that as long as there is a physical hard drive with Ubuntu on it, no matter how many times you delete the Ubuntu entry from the boot order using that rEFInd tool on a CD/DVD, it never really goes away.

What I want to highlight is the fact that (I while keeping Ubuntu installed on the hard drive and keeping the hard drive connected) deleted the Ubuntu entry from the boot order within the BIOS settings using that tool rEFInd and I found that the original entry called "Ubuntu" was gone, but a new entry called "UEFI: ST1000DM010-2EP102" was automatically created and I know this basically represented my hard drive on which Ubuntu still actually stayed installed. And when I booted into this new entry (UEFI: ST1000DM010-2EP102), I also found that Ubuntu booted well and upon reentering BIOS this very entry (UEFI: ST1000DM010-2EP102), had been automatically renamed Ubuntu just like earlier. 

So, finally I fired a shot in the dark by actually first installing Windows 7 on the same hard drive, thereby wiping Ubuntu entirely and then when the Ubuntu entry still remained in the boot order, I just used that rEFInd tool to delete Ubuntu entry and this time around the Ubuntu entry was gone forever from the boot order within BIOS settings. 

Have I done the right thing in order to removed the Ubuntu entry? Is there any other way of doing the same thing? Thanks.

[https://www.rodsbooks.com/refind/](https://www.rodsbooks.com/refind/)

Here is my entire process in photos with my personal comments in between. Sorry these photos were taken on my mobile a with poor quality camera.

[https://postimg.cc/gallery/5yGLJb2](https://postimg.cc/gallery/5yGLJb2)

As of now, it looks like the photos have been put in a random order by the website, rather the original order in which I had uploaded them. Please accept my apology.

Here is the final step.

Many thanks.

[URL="https://postimg.cc/gallery/9hWP1Jk"]https://postimg.cc/gallery/9hWP1Jk
[/URL]

---

### Post by dragonfly41 on 2022-01-21
You have gone into great detail to record your workflow.

 [rEFInd]("https://ubuntuforums.org/ROOT--rEFInd.html") can be a very useful alternative to boot manager.

I use rEFInd to navigate across different development systems, on multiple external drives.

It is installed within the usual efi filesystem. Not replacing /boot/efi/EFI/ubuntu
but adding /boot/efi/EFI/refind/

Now inside that refind folder we see ..
refind.conf-sample

If we wish to customise [rEFInd]("https://ubuntuforums.org/ROOT--rEFInd.html") usage and its UI, _save_ a copy of this sample file into refind.conf (dropping the "-sample" at end).

Now if this refind.conf file is opened in say Geany editor we see a whole bunch of config options.

I refer to the author's documentation.

[https://www.rodsbooks.com/refind/configfile.html](https://www.rodsbooks.com/refind/configfile.html)



Meanwhile, a route to achieve what you want is discussed here:

[https://askubuntu.com/questions/1168330/uefi-os-boot-manager-still-has-an-entry-for-ubuntu-after-its-removal](https://askubuntu.com/questions/1168330/uefi-os-boot-manager-still-has-an-entry-for-ubuntu-after-its-removal)

But note the warning to use commands with caution.

First run: efibootmgr
and you see the menu.

then follow advice here:    man efibootmgr

---

### Post by oldfred on 2022-01-21
If you run this, it shows details of UEFI boot entry including the GUID/partUUID of ESP partition it uses to find boot files.
sudo efibootmgr -v

And to see partUUID.
lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,uuid,partuuid

Any entries with partUUIDs that do not exist anymore from old install & be removed.
And if multiple or duplicate entries with same partUUID, you can remove all but one.

sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr

---

### Post by tech291083 on 2022-01-31
> **dragonfly41 said:**
> You have gone into great detail to record your workflow.

 [rEFInd]("https://ubuntuforums.org/ROOT--rEFInd.html") can be a very useful alternative to boot manager.

I use rEFInd to navigate across different development systems, on multiple external drives.

It is installed within the usual efi filesystem. Not replacing /boot/efi/EFI/ubuntu
but adding /boot/efi/EFI/refind/

Now inside that refind folder we see ..
refind.conf-sample

If we wish to customise [rEFInd]("https://ubuntuforums.org/ROOT--rEFInd.html") usage and its UI, _save_ a copy of this sample file into refind.conf (dropping the "-sample" at end).

Now if this refind.conf file is opened in say Geany editor we see a whole bunch of config options.

I refer to the author's documentation.

[https://www.rodsbooks.com/refind/configfile.html](https://www.rodsbooks.com/refind/configfile.html)



Meanwhile, a route to achieve what you want is discussed here:

[https://askubuntu.com/questions/1168330/uefi-os-boot-manager-still-has-an-entry-for-ubuntu-after-its-removal](https://askubuntu.com/questions/1168330/uefi-os-boot-manager-still-has-an-entry-for-ubuntu-after-its-removal)

But note the warning to use commands with caution.

First run: efibootmgr
and you see the menu.

then follow advice here:    man efibootmgr

Great, thanks a lot.

---

### Post by tech291083 on 2022-01-31
Mine situation..

> [james@localhost ~]$ efibootmgr -g
BootCurrent: 0001
Timeout: 1 seconds
BootOrder: 0001,0000,0008,0002,0007
Boot0000* Fedora
Boot0001* Fedora
Boot0002* ubuntu
Boot0007* CD/DVD Drive 
Boot0008* Hard Drive 
[james@localhost ~]$ 
[james@localhost ~]$ 
[james@localhost ~]$ efibootmgr -v
BootCurrent: 0001
Timeout: 1 seconds
BootOrder: 0001,0000,0008,0002,0007
Boot0000* Fedora    HD(1,GPT,6dc21198-1363-4e0b-84dc-9869c650de60,0x800,0x12c000)/File(\EFI\fedora\shimx64.efi)
Boot0001* Fedora    HD(1,GPT,9518731c-f4db-4aa3-b3ee-206e063cef61,0x800,0x12c000)/File(\EFI\FEDORA\shimx64.efi)
Boot0002* ubuntu    HD(1,GPT,1683a6c5-98b1-449e-9897-a9cb8be8260e,0x800,0x1e8000)/File(\EFI\ubuntu\shimx64.efi)
Boot0007* CD/DVD Drive     BBS(CDROM,,0x0)AMGOAMNO........m.D.R.W.-.2.4.D.5.M.T....................A.........................>..Gd-.;.A..MQ..L.M.K.J.J.7.5.2.K.2.0. .9. . . . . . . . ......AMBO
Boot0008* Hard Drive     BBS(HD,,0x0)AMGOAMNO........m.S.T.3.5.0.0.5.1.1.C.S....................A.........................>..Gd-.;.A..MQ..L. . . . . . . . . . . . .V.5.V.V.6.C.G.A......AMBO
[james@localhost ~]$ 


thanks a lot.

---

