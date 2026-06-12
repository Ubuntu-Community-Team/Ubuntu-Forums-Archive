---
title: "Creating a livecd"
date: 2012-10-30
forum: General Help
---

### Post by anon_private on 2012-10-30
It is best to download the file to a pc and then burn to a cd-r?

Does ubuntu have a burner?

Thanks

---

### Post by Bucky Ball on 2012-10-31
Yes; download the correct .iso file for your system (64bit or 32bit) then create a disk image.
Yes; Ubuntu has a burner. In fact, lots. I think the default in 12.04 LTS is still Brasero. 

1) Download the correct disk image while booted from the LiveCD (the install CD);
2) Launch Brasero and burn the .iso file to disk (using 'Create Disk Image');
3) Restart and go to the BIOS or boot device options to boot from the CD rather than the hard drive (it varies but you probably need F2 or F12 to change the boot device).

When you're done the install should boot from the optical drive.

---

### Post by anon_private on 2012-10-31
> **Bucky Ball said:**
> Yes; download the correct .iso file for your system (64bit or 32bit) then create a disk image.
Yes; Ubuntu has a burner. In fact, lots. I think the default in 12.04 LTS is still Brasero. 

1) Download the correct disk image while booted from the LiveCD (the install CD);
2) Launch Brasero and burn the .iso file to disk (using 'Create Disk Image');
3) Restart and go to the BIOS or boot device options to boot from the CD rather than the hard drive (it varies but you probably need F2 or F12 to change the boot device).

When you're done the install should boot from the optical drive.

I have CD/DVD Creator in 9.10. I assume that I can use this programme to burn the CD.

---

### Post by Bucky Ball on 2012-10-31
I would say so. Only ever used Brasero myself and never used 9.** anything (8.04 LTS straight to 10.04 LTS). You are looking to make a disk image, a bootable CD (as opposed to audio, video or data CD).

---

### Post by anon_private on 2012-10-31
> **Bucky Ball said:**
> I would say so. Only ever used Brasero myself and never used 9.** anything (8.04 LTS straight to 10.04 LTS). You are looking to make a disk image, a bootable CD (as opposed to audio, video or data CD).

I found Brasero.

I have downloaded lubuntu-12.04-alternative-i386,iso from cdimage.ubuntu.com.

I used a system called 'Bit Torrent'. I don't know how this works, but it did.

Initially, I tried to download using Firefox, but to my surprise I could not select a folder, only download (I believe to the livecd) or open. Surely, I should have been able to download to the hard-drive!

Now I have the file, I assume that I should check it for integrity and any viruses, malware etc., prior to burning. Can you tell me how I can do this?

Thanks

Ps. I only have Windows software installed on my machine, and cannot access the programmes due to insufficient memory.

---

### Post by zombifier25 on 2012-11-01
> **anon_private said:**
> I found Brasero.

I have downloaded lubuntu-12.04-alternative-i386,iso from cdimage.ubuntu.com.

I used a system called 'Bit Torrent'. I don't know how this works, but it did.

BitTorrent is a peer-2-peer file sharing network, and if you're downloading big files, you should use this protocol. Read on Wikipedia for more info.
> **anon_private said:**
> 
Initially, I tried to download using Firefox, but to my surprise I could not select a folder, only download (I believe to the livecd) or open. Surely, I should have been able to download to the hard-drive!


And about the Firefox issue, it's because Firefox's default configuration does not ask for location to download the file, but it wil instantly save the file to ~/Downloads.
> **anon_private said:**
> 
Now I have the file, I assume that I should check it for integrity and any viruses, malware etc., prior to burning. Can you tell me how I can do this?

Thanks

Ps. I only have Windows software installed on my machine, and cannot access the programmes due to insufficient memory.

The file's integrity should be checked during download using BitTorrent. You still should check it yourself though. [Instructions here](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Bucky Ball on 2012-11-01
Is there any reason you downloaded the i386 ISO? Have you an older machine? If you have a dual-core or newer machine you should be using the AMD64bit, regardless of whether you have and Intel or AMD processor.

Just download the torrent ISO using Transmission, which is already installed in Ubuntu under 'Network'. Let's not complicate things; you don't need to use Bit Torrent, just any torrent client.

---

### Post by anon_private on 2012-11-01
> **zombifier25 said:**
> BitTorrent is a peer-2-peer file sharing network, and if you're downloading big files, you should use this protocol. Read on Wikipedia for more info.


And about the Firefox issue, it's because Firefox's default configuration does not ask for location to download the file, but it wil instantly save the file to ~/Downloads.


The file's integrity should be checked during download using BitTorrent. You still should check it yourself though. [Instructions here]("https://help.ubuntu.com/community/HowToMD5SUM")

Thanks for the response.

You said that Firefox downloads to 'Downloads'. I got the impression that FF was trying to download to the liveCD!

---

### Post by anon_private on 2012-11-01
> **Bucky Ball said:**
> Is there any reason you downloaded the i386 ISO? Have you an older machine? If you have a dual-core or newer machine you should be using the AMD64bit, regardless of whether you have and Intel or AMD processor.

Just download the torrent ISO using Transmission, which is already installed in Ubuntu under 'Network'. Let's not complicate things; you don't need to use Bit Torrent, just any torrent client.


I have 32bit machine, hence I thought that the (Intelx86) would be the most appropriate file.

I think that I have downloaded the wrong file. I should have downloaded the Desktop Intelx86 version. I will try again this evening, and if I successfully download the file I will delete the alternative version. But I note that the alternative version installs on machines with less than 384 MB of RAM. I have 512 MB at present. I need advice on whether to burn the Desktop or Alternative version.

Ps. I was surprised at how quickly 'Bit Torrent' downloaded such a large file - about ten minutes.

I don't understand the reference to 'Transmission'. I had no problem with 'Bit Torrent". Why is 'Bit Torrent' listed as having a file size of 27k?

What is the difference between copying a file and burning a file?

---

### Post by MoebusNet on 2012-11-01
Ubuntu has changed a bit in the last year, which is why you've been questioned about your hardware. For example, in 12.04 Ubuntu, Kubuntu and Edubuntu now require you to have a CPU that supports a PAE kernel. If you have an older CPU (Pentium for example) that does not support PAE then you will need Lubuntu or Xubuntu because the others won't work for you. 12.10 no longer supports non-PAE CPUs.

The big advantage of a 64-bit kernel for most people is that it properly supports 3.5Gb and more of RAM. If your system uses less than about 3.5 Gb RAM, 32-bit will be fine.

I would use the desktop version rather than the alternative version; the alternative is really for those people who find they cannot use the desktop version to install.

BitTorrent is a protocol that underpins the practice of peer-to-peer file sharing and is used for distributing large amounts of data over the Internet. Transmission is an application that uses the BitTorrent protocol. The 27k BitTorrent file told Transmission or another BitTorrent apllication how to download the iso file for Ubuntu.

Copying a file places a copy of that file on your hard drive. Burning a file refers to placing a copy of that file on a CD or DVD.

---

### Post by anon_private on 2012-11-01
> **MoebusNet said:**
> Ubuntu has changed a bit in the last year, which is why you've been questioned about your hardware. For example, in 12.04 Ubuntu, Kubuntu and Edubuntu now require you to have a CPU that supports a PAE kernel. If you have an older CPU (Pentium for example) that does not support PAE then you will need Lubuntu or Xubuntu because the others won't work for you. 12.10 no longer supports non-PAE CPUs.

The big advantage of a 64-bit kernel for most people is that it properly supports 3.5Gb and more of RAM. If your system uses less than about 3.5 Gb RAM, 32-bit will be fine.

I would use the desktop version rather than the alternative version; the alternative is really for those people who find they cannot use the desktop version to install.

BitTorrent is a protocol that underpins the practice of peer-to-peer file sharing and is used for distributing large amounts of data over the Internet. Transmission is an application that uses the BitTorrent protocol. The 27k BitTorrent file told Transmission or another BitTorrent apllication how to download the iso file for Ubuntu.

Copying a file places a copy of that file on your hard drive. Burning a file refers to placing a copy of that file on a CD or DVD.

Thanks for responding.

My CPU is Pentium D 915 Processor Dual Core

I used to have 1GB of memory, but due to a problem I am running on 512GB at present. I believe that the machine can support up to 4GB of memory (not quite sure).

Would you expect me to have difficulty with versions of UBUNTU 9.10 and 10.04?

I will be downloading the desktop version of LUBUNTU 12.04. I believe that this should be suitable.

I believe that my machine is 32bit because the VIsta disk supplied - which contains the OS installed on the machine is 32bit. it is also about 6 years old.

I did not quite understand you point regarding the 27k Bit Torrent. It looks like a complete iso file

Best wishes.

A

PS. The md5 tests seem a bit of a chore

---

### Post by MoebusNet on 2012-11-01
Your CPU appears to be capable of running a 64-bit system, if you need more than about 3.5 Gb RAM: [http://en.wikipedia.org/wiki/List_of_Intel_Pentium_D_microprocessors](http://en.wikipedia.org/wiki/List_of_Intel_Pentium_D_microprocessors)

I wouldn't expect for you to have problems with 9.10 or 10.04, but 12.04 is to be preferred because of the 5 year support available.

Microsoft charged more for the 64-bit versions of Windows, so many computers were supplied with the 32-bit versions just for reasons of cost.

---

### Post by anon_private on 2012-11-01
> **MoebusNet said:**
> Your CPU appears to be capable of running a 64-bit system, if you need more than about 3.5 Gb RAM: [http://en.wikipedia.org/wiki/List_of_Intel_Pentium_D_microprocessors](http://en.wikipedia.org/wiki/List_of_Intel_Pentium_D_microprocessors)
 
I wouldn't expect for you to have problems with 9.10 or 10.04, but 12.04 is to be preferred because of the 5 year support available.
 
Microsoft charged more for the 64-bit versions of Windows, so many computers were supplied with the 32-bit versions just for reasons of cost.
 
 
Which LUBUNTU would you advise me to download?
Remember that at present I have only 512MB of RAM.
 
Thanks
 
Ps. I seem to have problems with UBUNTU 9.10 and 10.04 that relate to system resources - probably memory.

---

### Post by MoebusNet on 2012-11-01
I believe the consensus here is that if it is possible for your computer to run a 64-bit OS, then that is what you should do. Most applications are available as 64-bit. With few exceptions, applications that need to run on a 32-bit OS can be made to run on a 64-bit OS. That said, the link to 64-bit Lubuntu is:

[http://cdimage.ubuntu.com/lubuntu/releases/12.10/release/lubuntu-12.10-desktop-amd64.iso](http://cdimage.ubuntu.com/lubuntu/releases/12.10/release/lubuntu-12.10-desktop-amd64.iso)

Since you suspect your problems with 9.10 & 10.04 were due to memory, after downloading the Lubuntu 12.04 iso file I would: 1) confirm the md5sum of the file you just downloaded 2) Burn the Lubuntu iso file to CD 3)Boot the Live-CD and check the CD you just burned before running it as a Live-CD 4) Run a memory check from the Live-CD to confirm whether or not you are having hardware rather than software issues.

Steps 2 & 3 are available from the menu on the Live-CD. If I remember correctly, during the boot screen if you type any key it will bring you to the menu with the RAM check and CD check choices.

Once you know that you have an uncorrupted copy of Lubuntu and that you have no defective RAM, the rest should be fairly straightforward. I hope this helps.

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

---

### Post by Bucky Ball on 2012-11-01
You could try the desktop version but I have my doubts with 512kb RAM. Alternate is a better bet as it uses the text based installer rather than disco graphics. Exactly the same content in the install though. 

With that little RAM I would be forgetting about Ubuntu and going for Xubuntu or Lubuntu (neither of which uses Unity but xfce4 and lxde desktop environments respectively). Forget Kubuntu. That is a bloat and will not run, or will run sluggishly, on that amount of RAM, if it installs at all.

Yes, stick to the i386 for your 32bit machine. 64bit would not install anyhow, as you may have found out already. 

1) Download i386 .iso of OS of choice;
2) Burn that .iso to a CD using 'Create Disk Image';
3) Boot from CD. 

Easy. Good luck. ;)

---

### Post by anon_private on 2012-11-01
> **Bucky Ball said:**
> You could try the desktop version but I have my doubts with 512kb RAM. Alternate is a better bet as it uses the text based installer rather than disco graphics. Exactly the same content in the install though. 

With that little RAM I would be forgetting about Ubuntu and going for Xubuntu or Lubuntu (neither of which uses Unity but xfce4 and lxde desktop environments respectively). Forget Kubuntu. That is a bloat and will not run, or will run sluggishly, on that amount of RAM, if it installs at all.

Yes, stick to the i386 for your 32bit machine. 64bit would not install anyhow, as you may have found out already. 

1) Download i386 .iso of OS of choice;
2) Burn that .iso to a CD using 'Create Disk Image';
3) Boot from CD. 

Easy. Good luck. ;)

I have a problem.

The only working operating system on my pc is the LIveCD that I use from the CDdrive.

I have the iso image on the pc, but I can't remove the LiveCD while it is running. I only have one CDdrive.

---

### Post by Bucky Ball on 2012-11-02
Then make a LiveUSB:

[http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/](http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/)

That is one of a million howtos on this. ;)

---

### Post by black veils on 2012-11-02
it was my understanding (i am sure i read this a while ago) that you can remove the disc, and use the drive, because the linux distro is already loaded into ram. but i am not 100% on this, so if you do it, you may lose the file.

i am surprised 512mb ram would be stable with a file that size, the ram will max out and the system should crash, as it relies on the ram in live cd mode.

if i were you (and if you have lost the downloaded file) i would use the Ubuntu mini.iso:

- during the installation process, you can choose your desktop  environment (if you dont, you will have no graphical interface), so you  would pick Lubuntu desktop from the list.
- .iso is only about 30mb in size!
- downloads what you need during installation
- use an ethernet cable not wireless
- says about being a command-line installer, but you dont have to enter any commands, just follow a basic set of questions
[COLOR=Blue]**[here is a nice and easy guide, just in case you feel intimidated!]("http://www.webupd8.org/2012/05/how-to-install-ubuntu-1204-on-non-pae.html")**[/COLOR]

---

