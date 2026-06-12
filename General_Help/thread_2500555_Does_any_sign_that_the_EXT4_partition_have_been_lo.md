---
title: "Does any sign that the EXT4 partition have been loaded or accessed?"
date: 2024-09-05
forum: General Help
---

### Post by mangada on 2024-09-05
My Ubuntu and my friend's Windows are installed in the same disk, how can I know if my EXT4 partition have been loaded or/and accessed by him or others?

---

### Post by TheFu on 2024-09-05
Keep track of the timestamps for files and allow atime to work on the file system through mount options.

However, there's nothing to prevent him/her from booting off a flash drive and going crazy with the files in the linux side unless you setup full drive (including OS) encryption.  If it were me, I'd at least do that or get a USB3 flash (or SSD) drive and install linux to that, so you don't leave your OS with the system, but take it with you.

Most MS-Windows users don't know how to access ext4 file systems, so unless your friend is a nerd, they are unlikely to bother.  Only you know if they will.  It isn't automatic in the way that Linux desktops can basically point-n-click to access MS-Windows data file systems.

Have the appropriate amount of security for your needs.  It is pretty unlikely that anyone actually cares about your Linux install, but only you know if that is a risk or not.

---

### Post by mangada on 2024-09-06
What about Microsoft Windows itself and it's default softwares, are they allowed to read the files on EXT4 partition?

---

### Post by ajgreeny on 2024-09-06
I don't think Windows can read ext# formatted partitions without installation of some third party software but it's now 20 years since I dual booted Ubuntu and Windows XP so I may be out of date.

However, I agree largely with TheFu that only you know about the risks your second user might be to you, and how knowledgeable in Linux he is, possibly (probably?) not at all if my friends and family are anything to go by!

---

### Post by TheFu on 2024-09-06
> **mangada said:**
> What about Microsoft Windows itself and it's default softwares, are they allowed to read the files on EXT4 partition?

Google found this: [https://www.thewindowsclub.com/how-to-read-ext4-in-windows-10](https://www.thewindowsclub.com/how-to-read-ext4-in-windows-10)
and a few others that are similar.

Might be smart to ask the question on an MS-Windows forum.

---

### Post by yancek on 2024-09-06
A default windows install is unlikely to be able to read much less write to any Linux filesystem but there is third party software which can enable it such as the software referred to in the link below or the link in post 5.

  [https://www.diskgenius.com/resource/read-ext4-windows.html](https://www.diskgenius.com/resource/read-ext4-windows.html)

---

### Post by werewulf75 on 2024-09-06
> **TheFu said:**
> Google found this: [https://www.thewindowsclub.com/how-to-read-ext4-in-windows-10](https://www.thewindowsclub.com/how-to-read-ext4-in-windows-10)
and a few others that are similar.
It might be because I have WSL but Windows Disk Management recognises and mounts ext4 devices (to my horror! ;) ) and so does a standard Windows  file manager, although I have resisted actually looking at any ext4 device there. Better safe than sorry.

Of the utilities listed on that link, I have used Diskinternals LinuxReader - generally, excellent IME. 

One oddity about Linux files under Windows might be worth noting here, 7zip files created on Linux, especially encrypted ones, don't always open in 7zip Windows and actually the attempt seems to corrupt the file.

---

### Post by werewulf75 on 2024-09-06
> **yancek said:**
> A default windows install is unlikely to be able to read much less write to any Linux filesystem but there is third party software which can enable it such as the software referred to in the link below or the link in post 5.

  [https://www.diskgenius.com/resource/read-ext4-windows.html](https://www.diskgenius.com/resource/read-ext4-windows.html)
I'd be *very* weary of using  Diskgenius, or any tool that claimed to allow writing directly to ext4 from Windows. The risk of corrupting the file system is just too great. Better to exchange data between Windows and Linux from the Linux side. 

Other reasons for weariness include the 'free lifetime updates' and 'free lifetime support' for the Pro version. As a commercial software company, they are at very great risk of having their revenue stream dwindle more and more until eventually they won't be around at all any more.

---

### Post by TheFu on 2024-09-06
> **werewulf75 said:**
>  
One oddity about Linux files under Windows might be worth noting here, 7zip files created on Linux, especially encrypted ones, don't always open in 7zip Windows and actually the attempt seems to corrupt the file.

There are many different implementations of "ZIP" archives and compression.  Not all are compatible.  On Linux, if you want the ZIP to be compatible with the built-in ZIP in MS-Windows, use **PeaZIP**. Or, better, use a tgz or tar.gz archive type which is cross platform and F/LOSS (not proprietary).  Actually, there are lots and lots of different compressors. It happens that ZIP was early and used on MS-Windows.  Took about 15 yrs before MSFT added native support, but on Unix/Linux, we'd already moved onto others.

[LIST]
[*]cpio
[*]tar
[*]Compress - .Z
[*]PkZip - .zip (mainly MS-Windows and MS-DOS)
[*]InfoZIP - .zip (mainly Unix)
[*]Arj - .arg
[*]Lha - .lhz
[*]<lots of others, including 10 variants of ZIP)
[*]bz 
[/LIST]

In general, newer compression is faster and compresses to smaller files.  Sort like how mpeg1 --> mpeg2 --> Mpeg4/Divx/Xvid --> h.264 --> h.265 --> and all the new video codes have gotten better/smaller, but not necessarily faster.

Anyway, hope this is helpful. You can always use the 'file' utility to read the file signature to know what archiver/compressor was used on any specific file. A few examples:
```
$ file x.tgz
x.tgz: gzip compressed data, from Unix, original size modulo 2^32 10240

$ file y.tar.gz
y.tar.gz: gzip compressed data, was "y-2.038.tar", last modified: Mon Apr 15 20:14:19 2024, max compression, from Unix, original size modulo 2^32 174080

$ file z.zip
z.zip: Zip archive data, at least v2.0 to extract

```
The utility will look at file signatures for any file and make the best guess possible.
```
$ file BIOSRenamer.exe
BIOSRenamer.exe: PE32 executable (console) Intel 80386, for MS Windows

$ file command.com 
command.com: MS-DOS executable, MZ for MS-DOS
```

The Linux/Unix OS doesn't care about the extension. Some poorly written GUI programs on Linux do.  I don't know why.  File extensions are conveniences for humans.  They are really convenient, most definitely.

---

### Post by werewulf75 on 2024-09-06
> **TheFu said:**
> There are many different implementations of "ZIP" archives and compression.  Not all are compatible.  On Linux, if you want the ZIP to be compatible with the built-in ZIP in MS-Windows, use **PeaZIP**. Or, better, use a tgz or tar.gz archive type which is cross platform and F/LOSS (not proprietary).  Actually, there are lots and lots of different compressors. It happens that ZIP was early and used on MS-Windows.  Took about 15 yrs before MSFT added native support, but on Unix/Linux, we'd already moved onto others.
It's 7zip I was writing about, on both sides, meant to be cross-platform. Its default compression method is LZMA2, highest compression I've yet seen and fast, as well as offering AES256 encryption. Most times it works fine using Linux side file in Windows. Where it doesn't, I tend to re-compress as tgz.

> **TheFu said:**
>  
[LIST]
[*]cpio 
[*]tar 
[*]Compress - .Z 
[*]PkZip - .zip (mainly MS-Windows and MS-DOS) 
[*]InfoZIP - .zip (mainly Unix) 
[*]Arj - .arg 
[*]Lha - .lhz 
[*]<lots of others, including 10 variants of ZIP) 
[*]bz 
[/LIST]
It's sad that Lzx is missing from that list. It was, in its time, the fastest  archiver around with highest compression ratio. That was back in the early '90s on Amiga which I had as well as NeXT. Sadly, Lzx - just as it was becoming x-platform, was snapped up by Microsoft along with its developer and became cab.
> **TheFu said:**
> In general, newer compression is faster and compresses to smaller files.  Sort like how mpeg1 --> mpeg2 --> Mpeg4/Divx/Xvid --> h.264 --> h.265 --> and all the new video codes have gotten better/smaller, but not necessarily faster.

Anyway, hope this is helpful. You can always use the 'file' utility to read the file signature to know what archiver/compressor was used on any specific file. A few examples:
```
$ file x.tgz
x.tgz: gzip compressed data, from Unix, original size modulo 2^32 10240

$ file y.tar.gz
y.tar.gz: gzip compressed data, was "y-2.038.tar", last modified: Mon Apr 15 20:14:19 2024, max compression, from Unix, original size modulo 2^32 174080

$ file z.zip
z.zip: Zip archive data, at least v2.0 to extract

```
The utility will look at file signatures for any file and make the best guess possible.
```
$ file BIOSRenamer.exe
BIOSRenamer.exe: PE32 executable (console) Intel 80386, for MS Windows

$ file command.com 
command.com: MS-DOS executable, MZ for MS-DOS
```

The Linux/Unix OS doesn't care about the extension. Some poorly written GUI programs on Linux do.  I don't know why.  File extensions are conveniences for humans.  They are really convenient, most definitely.
All very useful information, thanks TheFu, let's hope it will prove so for lots of others too.

Yeah, sometimes the profusion of file extensions in places really irritates me but on the other hand, sometimes they can be convenient for us humans, as you point out. :)

---

### Post by mangada on 2024-09-07
reddit.com/r/windows/comments/1c7wflf/does_windows_1011_use_parts_of_or_based_on/
darwinsdata.com/does-windows-support-ext4-format/   

Are these links telling me EXT4 partitions can not be read and acccessed by windows without third parted software?

---

### Post by TheFu on 2024-09-07
> **mangada said:**
> reddit.com/r/windows/comments/1c7wflf/does_windows_1011_use_parts_of_or_based_on/
darwinsdata.com/does-windows-support-ext4-format/   

Are these links telling me EXT4 partitions can not be read and acccessed by windows without third parted software?

Depends on what you mean by "third parted software".  SysInternals is from MSFT, but not preinstalled.  WSL2 is from MSFT, but not preinstalled.
It won't happen accidentally. Someone needs to want to access the storage.  That's the only guarantee you'll get.

---

### Post by mangada on 2024-09-12
[https://reddit.com/r/windows/comments/1c7wflf/does_windows_1011_use_parts_of_or_based_on/](https://reddit.com/r/windows/comments/1c7wflf/does_windows_1011_use_parts_of_or_based_on/)
Is Linux kernel code including EXT4?

---

### Post by mangada on 2024-09-13
> **TheFu said:**
> Depends on what you mean by "third parted software".  SysInternals is from MSFT, but not preinstalled.  WSL2 is from MSFT, but not preinstalled.
It won't happen accidentally. Someone needs to want to access the storage.  That's the only guarantee you'll get.

[https://woshub.com/install-wsl-windows-subsystem-linux/](https://woshub.com/install-wsl-windows-subsystem-linux/)
```
wsl --install
```
This command will automatically enable all the necessary Windows features required for WSL, install the Linux kernel update for WSL2.

So it has been preinstalled, WSL is disabled by default on Windows.

---

