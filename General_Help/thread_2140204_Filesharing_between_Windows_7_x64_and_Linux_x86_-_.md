---
title: "Filesharing between Windows 7 x64 and Linux x86 - very low speeds"
date: 2013-04-29
forum: General Help
---

### Post by Tralce on 2013-04-29
Now, I realize that technically this isn't an Ubuntu issue but I'm not sure it really matters, where the distros are so similar. I'm using a Debian machine to run bittorrent and other large downloads. I generally copy or move the downloaded files to the Windows machine over Samba. Until upgrading my network to gigabit (with a new gigabit switch and cat6) I hadn't really paid attention to the fact that the speeds were actually quite low -- usually peaking out at 4MB/s. I had previously thought that this was a result of the old 100mbit switch but as it turns out it's not. Both the windows machine and Debian machine have gigabit Ethernet cards, and /are/ running at 1000Mbps full duplex. I have verified the network throughput with iperf to be ~950Mbps both ways. 

Here's where it gets weird. Samba, FTP, SFTP, NFS and HTTP transfers are all extremely slow. 
Maximums:
Samba - ~4300KB/s (Tested with a simple file copy and Windows 7)
SFTP - ~5000KB/s (Tested with WinSCP and openssh-server)
NFS - 2520KB/s (Tested with the standard NFS client on another Linux box)
HTTP - 3250KB/s (Tested with wget/google-chrome and apache2)

Interestingly they all begin this slowly /except/ for Samba, which with a standard windows drag and drop file copy starts up at around 70MB/s and the speed tapers off at a rate of about 2MB/s/s until it reaces a plateau of around 4MB/s. 

Steps I've taken:

Items 1 and 2 on this list: [http://www.sysprobs.com/windows-7-network-slow](http://www.sysprobs.com/windows-7-network-slow)
The smb.conf mods made by the third poster in this thread: [http://ubuntuforums.org/showthread.php?t=1908714](http://ubuntuforums.org/showthread.php?t=1908714)

The only thing that seemed to help was disabling Remote Differential Compression which I think was the cause for the initial speed burst of 70MB/s. 

I've been hours googling this and I'm exhausted so I may have overlooked something... please help...

Update: I've replaced all cables concerned twice. If I try a similar file transfer between the debian server and an ubuntu laptop, over the gigabit ethernet, the speed hovers around 29MB/s, which is definitely not a gigabit speed either, but it's a lot better than 4MB/s.

---

### Post by QIII on 2013-04-29
As a control, have you tested a Linux to Linux transfer of a large file over your network?

---

### Post by Tralce on 2013-04-29
This is weird...

The computers concerned are as follows: 
Debian machine - "server"
Windows 7 machine - "desktop"
xubuntu machine - "laptop" 

samba from server to desktop - slow as all gang busters
samba from server to laptop - slow but not /as/ slow
samba from laptop to desktop - more reasonable ~29MB/s
NFS on the server, mounted on desktop with NekoDrive - ~8MB/s
NFS on the server, mounted on laptop with standard mount.nfs ~50MB/s
NFS on the server, mounted on desktop running Ubuntu livecd and standard nfs client -lightning fast ~110 MB/s

Obviously, now, it seems Windows is probably the main culprit. Strange since I've never had any filesharing problems with Windows before. This is an almost clean install of Home Premium x64 that's probably less than two weeks old. 

I'm going to do some research on Windows forums now, but if I find a solution I'll post it here so that maybe others can get help with this.

---

