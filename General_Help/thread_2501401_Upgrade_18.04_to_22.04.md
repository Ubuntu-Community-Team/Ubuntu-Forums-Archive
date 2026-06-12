---
title: "Upgrade 18.04 to 22.04"
date: 2024-10-05
forum: General Help
---

### Post by sks24 on 2024-10-05
Hi,
I have a 6th Gen X-1 Carbon (i7, 16GB) dual booting Win 11 and 18.04. The Ubuntu partition hasn't booted in about a year, and the error message has to do with not enough available space. So I think what I would like to do is increase the size of the Linux partition and install 22.04 LTS. (I would install 24.04, but I'm afraid that it won't run ThinkorSwim desktop as well as 22.04). I don't have any data in the Ubuntu partition that I care about, so we can delete whole partitions if that's the easiest thing to do. But the thing is, I'm not sure which partition is which in the Windows disk management interface. 
I'm really not sure about the best way to go about this, but what I'm used to doing is managing the partitions from within Windows, then coming back and installing Ubuntu from a USB drive. I did boot 22.04 from a thumbdrive, and I'll link to some screen shots from both that boot and the Windows partition manager here: [https://photos.app.goo.gl/KDtqBR2qsF2Pq2Ej6]("https://photos.app.goo.gl/KDtqBR2qsF2Pq2Ej6")

Edit: Maybe the best way to go is somehow repair the boot on the 18.04 installation and upgrade from there? I'm indifferent; whatever you guys think is easiest and safest in terms of the Windows installation, which I need. 

Thanks in advance for your help,
Scott

---

### Post by 1fallen on 2024-10-05
I have a 7th Gen X1 Carbon running 24.04 nicely, just to ease your mind.
A clean install will always be the best outcome, as soon as you get your sizes sorted out. ;)

---

### Post by oldfred on 2024-10-05
Looks like p5 is / (root), p6 is swap & p7 is /home.
You probably have to turn Windows bitlocker off & resize NTFS partitions with Windows tools. And reboot Windows so it can run chksk which it needs after any resize. Your p4 is probably a Windows recovery partition & if shrinking p3, will also have to move p4 left. Only use Windows tools for NTFS partition changes. And make sure Windows boots after all Windows changes.

You then can use gparted to resize Linux partitions. If unallocated to the left, you move partition left & resize right. Only do one change at a time.
You should also shrink swap, it only needs to be 4GB and default installs use swap file of about 2GB. But swap partition is still often recommended & just over 4GB is suggested as all you need. You can add swap space converted to unallocated to /home. Again move left & expand right. Move left can take a long time depending on amount of data.

Looks like you had Kubuntu? 
With 24.04 it has a new installer (I think its better), or Calmares. Ubuntu now uses subiquity, and used to use ubiquity installers.
Whichever use use, best to use manual install, and choose p5 (after resized) as / (root), and p7 as /home. It should find & use swap (after you have made it smaller) You may want to increase size of /home also, but that depends on how much data you save. Some like a separate NTFS partition for shared data, but if bitlocker on, that will not work.

---

### Post by grahammechanical on 2024-10-05
> Edit: Maybe the best way to go is somehow repair the boot on the 18.04 installation and upgrade from there?

That will mean an online upgrade from 18.04 to 20.04 to 22.04 and perhaps onto 24.04. Everything may turn out fine. But then again. May be not. Be prepared to do a fresh install.

Regards

---

### Post by sks24 on 2024-10-05
Thanks oldfred,
I've seen Kubuntu in some of the BIOS output when booting, but I could have sworn I was running the standard LTS Ubuntu. In any case, I'll try 24.04 desktop. What I would like to do is delete partitions 5, 6, and 7 (by right-clicking and selecting "delete volume") and reboot windows. (See: [https://photos.app.goo.gl/XAsmXuzRVbuMfCRo8]("https://photos.app.goo.gl/XAsmXuzRVbuMfCRo8") Then boot to the installer, and let the installer install Ubuntu for me. Will that work? (I've never learned how to do manual installs, although I'm not opposed to it.) I turned Bitlocker off, and it no longer indicates "Bitlocker" in the C drive.  Those partitions have about 124GB of space. I'll probably expand that another 100 GB for the 24.04 installation (although it seems to me like 124 GB should be plenty for an Ubuntu installation in which I only run one program and don't use it to store files locally.) 

Thanks again, Scott

---

### Post by sks24 on 2024-10-05
Thanks 1fallen2,
I'll try the clean install of 24.04.
Best,
Scott

---

### Post by sks24 on 2024-10-05
Thanks grahammechanical,
Will do the fresh install. 
Best,
Scott

---

### Post by 1fallen on 2024-10-05
> **sks24 said:**
> Thanks 1fallen2,
I'll try the clean install of 24.04.
124 GB should be plenty for an Ubuntu installation. 
Best,
Scott
That 124Gigs should be plenty for a non storage set-up, with a little wiggle room.

Good Luck I have faith in your skills. ;)

---

### Post by sks24 on 2024-10-05
Thanks 1fallen2,
Could you please help me with checksums? 
I'm trying to navigate to my Home/Downloads/ISO folder so I can run a checksum on the 24.04 ISO. I've forgotten how to do this! "cd /Home/Downloads/ISO" yields "No such file or directory." What am I missing? There used to be an easier way to run the checksums, but I can't find it. See: [https://photos.app.goo.gl/E3VRnafox2ACpUzW9](https://photos.app.goo.gl/E3VRnafox2ACpUzW9).
Thanks, 
Scott

---

### Post by 1fallen on 2024-10-05
> **sks24 said:**
> Thanks 1fallen2,
Could you please help me with checksums?
I'm trying to navigate to my Home/Downloads/ISO folder so I can run a checksum on the 24.04 ISO. I've forgotten how to do this! "cd /Home/Downloads/ISO" yields "No such file or directory." What am I missing? There used to be an easier way to run the checksums, but I can't find it. See: [https://photos.app.goo.gl/E3VRnafox2ACpUzW9](https://photos.app.goo.gl/E3VRnafox2ACpUzW9).
Thanks,
Scott

Sorry I've been off messing around but, Alongside the actual ISO files containing the Ubuntu image you downloaded, all Ubuntu mirrors publish some extra files. The ones we are interested in are called:

SHA256SUMS                                    
SHA256SUMS.gpg  

It is usually convenient to download these at the same time as downloading the distro. However, if you didn&#8217;t, not to worry - the checksums and the signature are consistent for the image, so even if you downloaded your ISO file from a different source, as long as it is fresh and hasn&#8217;t been updated in the interim, you can fetch these files from the: [http://releases.ubuntu.com](http://releases.ubuntu.com) page for the relevant release. You will usually find the relevant files on the top of the directory listing.

I took the liberty to include the right page in my link above.

The easiest way to find out if you need the key is to run the authentication command: ```


gpg --keyid-format long --verify SHA256SUMS.gpg SHA256SUMS


```

---

### Post by davetheoldcoder on 2024-10-05
If the files were downloaded from a trusted site, and you only want to verify the checksum, without checking the GPG signature:

Check all of the files listed (with their SHA-256 hashes) in the specified file: 
```
sha256sum -c SHA256SUMS
```

 Compute the SHA-256 hash of the specified file:
```
sha256sum ubuntu-24.04-desktop-amd64.iso
```

---

### Post by sks24 on 2024-10-06
> **1fallen2 said:**
> Sorry I've been off messing around but, Alongside the actual ISO files containing the Ubuntu image you downloaded, all Ubuntu mirrors publish some extra files. The ones we are interested in are called:

SHA256SUMS                                    
SHA256SUMS.gpg  

It is usually convenient to download these at the same time as downloading the distro. However, if you didn’t, not to worry - the checksums and the signature are consistent for the image, so even if you downloaded your ISO file from a different source, as long as it is fresh and hasn’t been updated in the interim, you can fetch these files from the: [http://releases.ubuntu.com](http://releases.ubuntu.com) page for the relevant release. You will usually find the relevant files on the top of the directory listing.

I took the liberty to include the right page in my link above.

The easiest way to find out if you need the key is to run the authentication command: ```


gpg --keyid-format long --verify SHA256SUMS.gpg SHA256SUMS


```

Thanks 1fallen2,

Here's the result:  

```
scott@scott-ThinkCentre-M910q:~$ gpg --keyid-format long --verify SHA256SUMS.gpg SHA256SUMS
gpg: directory '/home/scott/.gnupg' created
gpg: keybox '/home/scott/.gnupg/pubring.kbx' created
gpg: can't open 'SHA256SUMS.gpg': No such file or directory
gpg: verify signatures failed: No such file or directory
scott@scott-ThinkCentre-M910q:~$ ^C
scott@scott-ThinkCentre-M910q:~$ 


```

I found the "How to verify your Ubuntu download" tutorial on Canonical's site. My issue is that it specifies operations I don't know how to do. For example, how does one download the ISO and the SUMS files at the same time? I did it sequentially. Apparently, that doesn't work. They are in the same directory: [https://photos.app.goo.gl/yijXuwu2UjNrzpTa7]("https://photos.app.goo.gl/yijXuwu2UjNrzpTa7")

---

### Post by 1fallen on 2024-10-06
OK then:
```
cd Downloads
```
next:
```
[FONT=monospace][COLOR=#000000]md5sum --version[/COLOR]

```
[/FONT]this will create a trust database for the current user.
```
[FONT=monospace][COLOR=#000000]sha256sum --version[/COLOR]

```
Now run it:
```
[/FONT][FONT=monospace][COLOR=#54FFFF]**~/Downloads**[/COLOR][COLOR=#000000]  [/COLOR]
[COLOR=#54FF54]**&#9492;&#9472;>**[/COLOR][COLOR=#000000]  gpg --keyid-format long --verify SHA256SUMS.gpg SHA256SUMS [/COLOR]
gpg: WARNING: unsafe permissions on homedir '/home/me/.gnupg' 
gpg: Signature made Thu 29 Aug 2024 10:08:15 AM MDT 
gpg:                using RSA key 843938DF228D22F7B3742BC0D94AA3F0EFE21092 
gpg: key D94AA3F0EFE21092: public key "Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>" imported 
gpg: Total number processed: 1 
gpg:               imported: 1 
gpg: Good signature from "Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>" [unknown] 
gpg: WARNING: This key is not certified with a trusted signature! 
gpg:          There is no indication that the signature belongs to the owner. 
Primary key fingerprint: 8439 38DF 228D 22F7 B374  2BC0 D94A A3F0 EFE2 1092

```

[/FONT]
[FONT=monospace]
[/FONT]
[FONT=monospace]


[/FONT]

---

### Post by sks24 on 2024-10-06
Got it! Thanks, davetheoldcoder. O:)

---

### Post by sks24 on 2024-10-06
Got it! Thanks, 1fallen2

---

