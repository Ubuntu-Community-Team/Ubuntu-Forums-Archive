---
title: "Transfer all data from hard disk"
date: 2021-11-13
forum: General Help
---

### Post by satimis on 2021-11-13
Hi all,

Please advise what will be the easy way transferring all data from a 4TB HD, ext 4 format, to a brand new 4TB HD, NTFS format.  There is no OS on the HD.

The new 4TB HD will be used for data storage only in another dual boot PC, sharing data between Ubuntu and Win 10.  No OS will be installed on the new 4TB HD

Thanks

Regards

---

### Post by Tadaen_Sylvermane on 2021-11-13
Cp or rsync. With no special permissions on ntfs its pretty basic. Will take a long time though.

If over network just scp instead of cp. Start it in a tmux session and let it run.

---

### Post by guiverc on 2021-11-13
Also asked at [https://askubuntu.com/questions/1375391/dumping-all-data-from-old-hd-to-new-hd](https://askubuntu.com/questions/1375391/dumping-all-data-from-old-hd-to-new-hd)

---

### Post by satimis on 2021-11-14
> **Tadaen_Sylvermane said:**
> Cp or rsync. With no special permissions on ntfs its pretty basic. Will take a long time though.

If over network just scp instead of cp. Start it in a tmux session and let it run.

Hi Tadaen_Sylvermane,

Thanks for your advice.

I have been running cp command on Ubuntu Terminal for long time.  As you mentioned that it will take long time to dump the data on an old 4TB SATA HD to a new 4TB SATA HD, even though they are connected in the same PC, say PC-1.

I have performed following test;

1) Start Ubuntu 20.04 Terminal on PC-1, which runs Oracle VirtualBox.
2) $ cp /path/to/old_HD/directory_1/ /path/to/new_HD/
3) Remove the new_HD from PC-1 and insert it in an USB Hard Drive Docking
4) On PC-2, a Dual boot PC, Ubuntu 20.04 on SSD_1 and Windows10_SSD-2, start Ubuntu and plugin the USB Hard Drive Docking to it.
5) Ubuntu detects the new_HD, reading directory_1 and its files without problem.  Files can be edited.  Even Window 10 VM and Linux OS VMs can read director_1 and its files
6) On PC-2 again, start Windows 10 and plugin the USB Hard Drive Docking to it.  Windows 10 can read directory_1 and its files on the new_HD

The above test proves that data of old_HD, of ext 4 format, can be copied to the new_HD, of NTFS format, without problem.

Now my problem is how to dump the data on the 4TB old_HD to the 4TB new_HD at the least time? 

Regards

---

### Post by dragonfly41 on 2021-11-14
One option you might consider (depending on your priority Windows/Ubuntu) is to install RLinux in Windows to read ext4 files.
Then you could use an external dual docking bay to clone ext4 to ext4, in background.
[https://www.youtube.com/watch?v=3f-W3WYpRCg&ab_channel=CrosstalkSolutions](https://www.youtube.com/watch?v=3f-W3WYpRCg&ab_channel=CrosstalkSolutions)

I use the Startech dual docking bay which can carry two SSD's. In fact I am using Ubuntu 20.04 now from external SSD.
So I have three drives: 1 internal HDD plus 2 external SSD's.

---

### Post by HermanAB on 2021-11-14
I would use rsync, since it does proper error detection and correction.  In a large set of data, you may get one or two errors with ordinary cp and rsync will prevent that.

---

### Post by satimis on 2021-11-14
> **dragonfly41 said:**
> One option you might consider (depending on your priority Windows/Ubuntu) is to install RLinux in Windows to read ext4 files.
Then you could use an external dual docking bay to clone ext4 to ext4, in background.
[https://www.youtube.com/watch?v=3f-W3WYpRCg&ab_channel=CrosstalkSolutions](https://www.youtube.com/watch?v=3f-W3WYpRCg&ab_channel=CrosstalkSolutions)

I use the Startech dual docking bay which can carry two SSD's. In fact I am using Ubuntu 20.04 now from external SSD.
So I have three drives: 1 internal HDD plus 2 external SSD's.
Hi dragonfly41,

Thanks for your advice

What is RLinux?  To install Linux on Windows?

I has considered Diskinternals, Linux Reader, before

If You Need to Access Ext4 from Windows
[https://www.diskinternals.com/linux-reader/access-ext4-from-windows/](https://www.diskinternals.com/linux-reader/access-ext4-from-windows/)

Then I need to install Diskinternals on all Win 10 VMs.  I think data sharing on HD is my direction.

This spare PC, PC-2, is a triple-boot PC, controlled by BIOS;
1st boot - Ubuntu 20.04 on SSD-1, running Oracle VirtualBox
2nd boot - Windows 10 on SSD-2 (bare-metal OS)
3rd boot - Ubuntu 20.04 SSD-3 (bare-metal OS)

All data are stored on a Storage HD, ext 4 format and without OS installed.

I need those bare-metal OS for testing, in case VirtualBox unable to forward some hardware to VMs.

I only have a single-bay docking device.

Now I'm reading some documents regarding "xcopy" of Command Prompt (Windows 10 application).  It seems having more options able to compress data in transferring.  If I can sort out my problem here I prefer to go Linux way.

Regards

---

### Post by satimis on 2021-11-14
> **HermanAB said:**
> I would use rsync, since it does proper error detection and correction.  In a large set of data, you may get one or two errors with ordinary cp and rsync will prevent that.
Hi HermanAB

Thanks for your advice

Just found;
How do I transfer a large number of files using rsync?
[https://support.cpanel.net/hc/en-us/articles/1500000822902-How-do-I-transfer-a-large-number-of-files-using-rsync-](https://support.cpanel.net/hc/en-us/articles/1500000822902-How-do-I-transfer-a-large-number-of-files-using-rsync-)

I suppose I should follow;
When you want to "push files" to a server from the current server you are logged into, the following command can be used........

One question I have to consider;
In case of failure, the data on the old HDD won't be damaged? That is my top priority consideration

Thanks

Regards

---

### Post by Tadaen_Sylvermane on 2021-11-14
I think one thing to consider is you can only push that data so fast. Even with a very powerful cpu and stuff it will max at the i/o speeds of the drives themselves. You could throw a quad socket with 12 cores on each at it and it will still cap at 100MBs or so depending on the drives (spinning drives). Also if it's a bunch of smaller files instead of a few big ones that alone will slow it down. There really is no high speed method that I'm aware of. 4tb is a lot of data so it will take time no matter how you slice it.

> [COLOR=#000000]In case of failure, the data on the old HDD won't be damaged? That is my top priority consideration[/COLOR][COLOR=#000000]

The copy process doesn't do any writing to the source generally so unless the source drive itself crashes and burns as far as it's concerned it's just data being read. Nothing more.

Doesn't help with the ext4 > ntfs transition but this is why raid exists. Keep redundant copies so you aren't waiting on a major downtime. I know in my case with snapraid for media it's all fine and good but when I lose a drive whatever is on that drive is MIA until the snapraid recovers it to the new drive. Proper raid eliminates this problem and the downtime associated with it.

*EDIT* A further option if you have a server running is just keep it on the server. Then you can keep a "single" copy so to speak and any machine can access it. You can run a samba share and nfs export at the same time with zero problems. At that point format is irrelevant.[/COLOR]

---

### Post by satimis on 2021-11-14
> **Tadaen_Sylvermane said:**
> I think one thing to consider is you can only push that data so fast. Even with a very powerful cpu and stuff it will max at the i/o speeds of the drives themselves. You could throw a quad socket with 12 cores on each at it and it will still cap at 100MBs or so depending on the drives (spinning drives). Also if it's a bunch of smaller files instead of a few big ones that alone will slow it down. There really is no high speed method that I'm aware of. 4tb is a lot of data so it will take time no matter how you slice it.
Hi Tadaen_Sylvermane,

That is a very good advice.

I'm considering creating 4 folders and dividing the data into 4 parts.  Each folder will contain 1 parts of the data.  Then transfer 4 folder one after one.

Any comment?  Thanks

> 
The copy process doesn't do any writing to the source generally so unless the source drive itself crashes and burns as far as it's concerned it's just data being read. Nothing more.
Noted and thanks.

> 
Doesn't help with the ext4 > ntfs transition but this is why raid exists. Keep redundant copies so you aren't waiting on a major downtime. I know in my case with snapraid for media it's all fine and good but when I lose a drive whatever is on that drive is MIA until the snapraid recovers it to the new drive. Proper raid eliminates this problem and the downtime associated with it.

*EDIT* A further option if you have a server running is just keep it on the server. Then you can keep a "single" copy so to speak and any machine can access it. You can run a samba share and nfs export at the same time with zero problems. At that point format is irrelevant.[/COLOR]
No I don't run server here.

Regards

---

### Post by dragonfly41 on 2021-11-14
> What is RLinux?

[https://www.r-studio.com/free-linux-recovery/](https://www.r-studio.com/free-linux-recovery/)

---

### Post by satimis on 2021-11-14
> **dragonfly41 said:**
> [https://www.r-studio.com/free-linux-recovery/](https://www.r-studio.com/free-linux-recovery/)
Thanks

Regards

---

### Post by satimis on 2021-11-14
Hi all,

Tadaen_Sylvermane on posting #9 above suggests me keeping one HD copy on a server so that any machine can access it.  At present I don't run server but it is not difficult for to build one.  I have old spare PCs.  Speed is not important in file sharing.

I just read following article online;
**[COLOR="#FF0000"]How to share files through the local network?[/COLOR]**
[https://askubuntu.com/questions/310180/how-to-share-files-through-the-local-network](https://askubuntu.com/questions/310180/how-to-share-files-through-the-local-network)

Which solution will be more suitable to me?  Please share me your experience.  Thanks

[B][COLOR="#FF0000"]Edit
==[/COLOR][/B]
Just found following document online

**[COLOR="#FF0000"]Share Large Files by Setting Up a Home File Server[/COLOR]**
[https://www.online-tech-tips.com/free-software-downloads/how-to-create-your-own-windows-file-sharing-server-to-share-large-files/](https://www.online-tech-tips.com/free-software-downloads/how-to-create-your-own-windows-file-sharing-server-to-share-large-files/)

Regards

---

### Post by TheFu on 2021-11-14
Just use rsync.  If it fails, you can restart and the previously completed copies won't happen again.
4TB will take about 26 hrs, IME.

```
rsync  -av --stats --progress /path/to/source[COLOR="#FF0000"]/[/COLOR]  /path/to/target[COLOR="#FF0000"]/[/COLOR]
```

This will provide information as the copy proceeds.  I assume you will mount the NTFS with the correct mount options to allow write ... or use sudo.
Beware, ext4 filenames can be different from what NTFS supports.  I don't know how this gets handled. The NTFS mount options can have a "windows_names" option to intelligently handle that.

---

### Post by satimis on 2021-11-14
> **TheFu said:**
> Just use rsync.  If it fails, you can restart and the previously completed copies won't happen again.
4TB will take about 26 hrs, IME.

```
rsync  -av --stats --progress /path/to/source[COLOR="#FF0000"]/[/COLOR]  /path/to/target[COLOR="#FF0000"]/[/COLOR]
``` 

This will provide information as the copy proceeds.  I assume you will mount the NTFS with the correct mount options to allow write ... or use sudo.
Beware, ext4 filenames can be different from what NTFS supports.  I don't know how this gets handled. The NTFS mount options can have a "windows_names" option to intelligently handle that.
Hi TheFu,

Thanks for your advice.

I'll mount the new 4TB SATA HDD, NTFS, inside the PC, not connecting it via USB.

I have tested on Terminal running cp a complete folder from the old 4TB HDD, ext4, to the new 4TB HDD, NTFS.  Then I connected the new 4TH HDD to PC via Hard Drive Docking device.  The said folder can be read in Ubuntu 20.04 and Windows 10, including Linux VMs and Windows VMs.  Its files can be edited.

I'll split the files on the Old 4TH HDD into 4 folders and transfer folder by folder, not all files at one time.  Besides I'll test each folder after each transfer completion.

What I'm planning to do is as follow;

I have 3 PCs, not run at the same time:
PC-1  
Daily working PC - Ubuntu 20.04, Oracle VirtualBox, LinuxVMs and WindowsVMs

PC-2
Stand-by PC, Multi-boot
SSD-1 - Ubuntu 20.04, Oracle VirtualBox, LinuxVMs and WindowsVMs
SSD-2 - Windows 10
SSD-3 - Ubuntu 20.04

PC-3
Stand-by PC - Ubuntu 20.04, Oracle VirtualBox, LinuxVMs and WindowsVMs

After completion I'll plugin the new 4TB HDD in my Hard Drive Docking device for file sharing amongst my PCs

The ONLY reason for me going back to Windows is to enhence the old video of my VHS and V8 tapes.  I can't get in done on Linux.  There are many articles and threads online explaining how to do it on Windows applications.

I'll start another posting later on file sharing server.

[B][COLOR="#FF0000"]Edit
===[/COLOR][/B]
On my PC, running AMD Ryzen 5 5600G 3.9GHz, 19MB and 32G RAM onboard, I hope the transfer time will be shorter

Regards

---

### Post by dragonfly41 on 2021-11-15
> [COLOR=#000000]The ONLY reason for me going back to Windows is to enhence the old video of my VHS and V8 tapes. I can't get in done on Linux. There are many articles and threads online explaining how to do it on Windows applications.[/COLOR]

If that is the case and you are not dependent on vendors such as Adobe have you explored Blender in Ubuntu for rendering?

[This is an interesting benchmark.]("https://www.youtube.com/watch?v=cpE2B2QSsa0&ab_channel=CGGeek")

---

### Post by satimis on 2021-11-15
> **dragonfly41 said:**
> If that is the case and you are not dependent on vendors such as Adobe have you explored Blender in Ubuntu for rendering?
[This is an interesting benchmark]("http://The ONLY reason for me going back to Windows is to enhence the old video of my VHS and V8 tapes. I can't get in done on Linux. There are many articles and threads online explaining how to do it on Windows applications.").
Sorry your link doesn't work.

I have tried Blender, OpenShot, etc. before on Ubuntu 20.04 without result.  Also I have made intensive online search.  The suggested solutions found by me all work on Windows.  Besides I have subscribed online photo/movie/video forums.  All the folks there only work on Windows environment.

Not one software can do the job.  6 software work together to get the job done,

Please visit following interesting YouTube video
How to use VirtualDub AviSynth AvsP and WinFF to restore videotapes and VHS
[https://www.youtube.com/watch?v=WXhLmH_ul94](https://www.youtube.com/watch?v=WXhLmH_ul94)

Regards

---

### Post by dragonfly41 on 2021-11-15
[Sorry, I should have checked the URL.]("https://www.youtube.com/watch?v=cpE2B2QSsa0&ab_channel=CGGeek")

---

### Post by dragonfly41 on 2021-11-15
Here is a bunch of further links to explore .. in Ubuntu.


[https://wiki.ubuntu.com/UbuntuStudio/Tutorials/EditingVideoInBlender](https://wiki.ubuntu.com/UbuntuStudio/Tutorials/EditingVideoInBlender)


 VirtualDub AviSynth AvsP and WinFF


FFMPEG, AviSynth, VirtualDub - Which tool for which purpose?

[http://www.digitalfaq.com/forum/video-restore/8814-ffmpeg-avisynth-virtualdub.html](http://www.digitalfaq.com/forum/video-restore/8814-ffmpeg-avisynth-virtualdub.html)

Blender vs VirtualDub

[https://comparisons.financesonline.com/virtualdub-vs-blender](https://comparisons.financesonline.com/virtualdub-vs-blender)

[https://blenderartists.org/t/video-color-restoration/666898](https://blenderartists.org/t/video-color-restoration/666898)

[https://community.wolfram.com/groups/-/m/t/2253071](https://community.wolfram.com/groups/-/m/t/2253071)

Now this last one is way off the beaten path and illustrates how mathematical kernels can be applied to videos.

I have installed wolframscript (CLI) into Ubuntu 20.04 and I registered for the free developer licence for playing around.

Wolfram can pass objects into Blender using Python API.

In fact if you go so far as installing Jupyter Lab in Ubuntu you can write scripts, clip by clip, as a notebook

Well worth playing with even if it does not meet your video restoration requirements.

---

### Post by TheFu on 2021-11-15
> **satimis said:**
>  
On my PC, running AMD Ryzen 5 5600G 3.9GHz, 19MB and 32G RAM onboard, I hope the transfer time will be shorter


It isn't the CPU.  **It is the HDD I/O that limits.**

BTW, I have a relatively new 5600G w/ 16G RAM as well. About a month old now.  It replaced a Pentium G3258 "server" that has a window manager, but isn't really used with a display. It is a server, so network access is the main way it gets used. Think it has about 30+TB of storage connected. I need to load a fresh 20.04 onto the empty NVMe drive and migrate all the server processes over to that and probably migrate a few VMs from a 3 yr old Ryzen too.

---

### Post by satimis on 2021-11-16
Hi all,

Following solution works for me seamlessly

1.  Format the new 4TB SATA HDD on Windows 10 Command Prompt running "diskpart" NTFS format
2.  Connect the new 4TB SATA HDD and the Old 4TB SATA HDD in the same PC
3.  Use Copy&Paste copying data from old HDD to new HDD
4.  Mount the new 4TB SATA HDD on a Hard Drive Docking

The data on the new 4TB SATA HDD can be read and edited on Ubuntu 20.04, Windows 10 and all Linux VMs and Win VMs

Regards

---

