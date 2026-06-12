---
title: "VMware difficulties"
date: 2007-06-04
forum: General Help
---

### Post by RealEmotionX on 2007-06-04
I am trying to get a fresh Windows XP  installation to run under VMware. The install is from a partition on the harddrive. I used these: [http://ubuntuforums.org/showthread.php?t=380699](http://ubuntuforums.org/showthread.php?t=380699) to do the thing. >< but I keep getting this error message

VMware Player cannot find the virtual disk "/root/Desktop/VMware data folder/windows.vmdk". Please verify the path is valid and try again.
Cannot open the disk '/root/Desktop/VMware data folder/windows.vmdk' or one of the snapshot disks it depends on.
Reason: The system cannot find the file specified.

yes I am doing the process logged into root. It was convenient at the time. Once VMware is working properly I am going to seal Root back up and log in under my user.


I can go through what I did Step by step with all the data I was given if you need it (being lazy right now)

---

### Post by steveneddy on 2007-06-04
If you are on feisty it doesn't work with this kernel yet.

---

### Post by ryanVickers on 2007-06-04
I'm on feisty with the new kernel and it works fine*!

*it's kind of slow, even with VM tools, but from a functionallity point of view, it's been great!  I love it!  you can see my posts on this [here]("http://ubuntuforums.org/showthread.php?t=459651").

For help on VM tools, go [here]("http://www.brandonhutchinson.com/Installing_VMware_Tools_with_VMware_Player.html")!  Real easy!

---

### Post by RealEmotionX on 2007-06-05
Well this is strange. I installed VMware tools through Synaptic but I am not seeing any kind of functionality anywhere. Any ideas?

---

### Post by cliffd7 on 2007-06-05
I had been using VMware with Edgy and it worked well but when I updated to Fiesty it was dead.
Reinstalled from synaptic and nothing worked so went back to basics, downloaded the VMware-Server-Distrib, went through the process and it works.
My virtual Machine is Windows XP prof.
But::: I cannot start it from the Applications menu, it will only start from terminal and then only sudo.
So my question is; how can I start VMware without sudo??

---

### Post by ryanVickers on 2007-06-05
Try changing permissions of the files where your virtual machine is to be accessible by you (read/write/execute/etc.)

---

### Post by RealEmotionX on 2007-06-05
still reciveing the error

VMware Player cannot find the virtual disk "/root/Desktop/VMware data folder/windows.vmdk". Please verify the path is valid and try again.
Cannot open the disk '/root/Desktop/VMware data folder/windows.vmdk' or one of the snapshot disks it depends on.
Reason: The system cannot find the file specified.

and I shouldent have to change permissions, I am logged in under ROOT. part of the reason why I was operating under root to get this working

---

### Post by scxtt on 2007-06-06
do the following and post it here:

**slocate -u**
**slocate windows.vmdk**
**vmware-cmd -l** (that's a lowercase L)

---

### Post by tylerjames on 2007-06-06
I'm having a strange problem as well.

On Monday I was able to run VMware server and boot Windows XP just fine. Then this morning I tried to do the same and VMware loaded fine but when I tried to fire up my Windows XP VM it just gave me a black screen and wouldn't load up XP.

Any ideas?

---

### Post by veloce on 2007-06-06
> **RealEmotionX said:**
> I am trying to get a fresh Windows XP  installation to run under VMware. The install is from a partition on the harddrive. I used these: [http://ubuntuforums.org/showthread.php?t=380699](http://ubuntuforums.org/showthread.php?t=380699) to do the thing. >< but I keep getting this error message

VMware Player cannot find the virtual disk "/root/Desktop/VMware data folder/windows.vmdk". Please verify the path is valid and try again.
Cannot open the disk '/root/Desktop/VMware data folder/windows.vmdk' or one of the snapshot disks it depends on.
Reason: The system cannot find the file specified.

yes I am doing the process logged into root. It was convenient at the time. Once VMware is working properly I am going to seal Root back up and log in under my user.


I can go through what I did Step by step with all the data I was given if you need it (being lazy right now)

You do seem to be doing this the hard way - if you were really lazy, you'd be using vmware-server + vmware converter.

Anyway, your issue sounds like the reference to the physical disk isn't working correctly.  I'd investigate that area of the vmx file.  

You should also check that the executable flag is on for the vmx file - root access won't turn that on - though I think you'd get a different error if that was off.

---

### Post by veloce on 2007-06-06
> **tylerjames said:**
> I'm having a strange problem as well.

On Monday I was able to run VMware server and boot Windows XP just fine. Then this morning I tried to do the same and VMware loaded fine but when I tried to fire up my Windows XP VM it just gave me a black screen and wouldn't load up XP.

Any ideas?

I've had that behaviour when some hardware or connection (network or usb) was not present.  Windows will sit for ages trying to contact the missing item. Usually it eventually gets there (worst was about 10 minutes) and is fine until the next time.  This may or may not be the cause.

---

### Post by RealEmotionX on 2007-06-06
> slocate -u
slocate windows.vmdk
vmware-cmd -l (that's a lowercase L)

bash: vmware-cmd: command not found


> 
You do seem to be doing this the hard way - if you were really lazy, you'd be using vmware-server + vmware converter.

Anyway, your issue sounds like the reference to the physical disk isn't working correctly. I'd investigate that area of the vmx file.

You should also check that the executable flag is on for the vmx file - root access won't turn that on - though I think you'd get a different error if that was off.

I get the same error with those on or off. And I am doing this the hard way so I could boot the partition and not a copy ><

---

### Post by veloce on 2007-06-06
> **RealEmotionX said:**
> 
I get the same error with those on or off. And I am doing this the hard way so I could boot the partition and not a copy ><

I can't get into that howto at the moment, but it does show using a physical disk with vmware **player**? I've not seen that done.  I didn't think there was a vmdk file for a physical disk? 

This is more straightforward with vmware server because server allows you to create new vms - or adjust the hardware of existing ones, including attaching physical disks.  I'm sure there's a howto for that around if you can't get this to work.

---

### Post by cliffd7 on 2007-06-06
Thanks ryanVickers,
I tried changing the permissions by chmod 777 vmware, which certainly changes them as shown by ls -l
but it doesn't fix the problem.
I still have to start vmware from the terminal with sudo .....:?

---

### Post by RealEmotionX on 2007-06-06
VMware can communicate with a physical disk. Its a bit more difficult but all it requires is parted information

---

### Post by vapore0n on 2007-06-06
> **cliffd7 said:**
> Thanks ryanVickers,
I tried changing the permissions by chmod 777 vmware, which certainly changes them as shown by ls -l
but it doesn't fix the problem.
I still have to start vmware from the terminal with sudo .....:?

I just got XP working using vmplayer.

All of the files are owned by root and disk. While im in the disk user group I still have to use sudo to start vmplayer.

Just use gksudo in an icon

gksudo vmplayer windows.vmx

---

### Post by RealEmotionX on 2007-06-06
I shouldent have to Sudo anything though

I was running everything while logged into ROOT

---

### Post by RealEmotionX on 2007-06-06
HERE IS MY EVERY MOVE!

STEP ONE: I use parted to examine my harddrive I am now not using ROOT but my profile KYLE


> kyle@kyle-desktop:~$ sudo parted
Password:
GNU Parted 1.7.1
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) unit s                                                           
(parted) print                                                            

Disk /dev/sda: [488281249s] [this is the number I need according to the walk through]
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start      End         Size        Type     File system  Flags
 1      63s        68485094s   68485032s   primary  ntfs         boot 
 2      68485095s  88486019s   20000925s   primary  linux-swap        
 3      88486020s  488279609s  399793590s  primary  ext3              

(parted) unit cyl                                                         
(parted) print                                                            

Disk /dev/sda: 30394cyl
Sector size (logical/physical): 512B/512B
BIOS cylinder,head,sector geometry: [30394,255,63] [the second group of numbers I need].  Each cylinder is 8225kB.
Partition Table: msdos

Number  Start    End       Size      Type     File system  Flags
 1      0cyl     4262cyl   4262cyl   primary  ntfs         boot 
 2      4263cyl  5507cyl   1245cyl   primary  linux-swap        
 3      5508cyl  30393cyl  24886cyl  primary  ext3      


NEXT! I take the first number and subtract 63 from it
488281249 - 63 = 488281186

Then I open Windows.VMDK and add the number at line 8: RW 488281186 FLAT "/dev/hda" 63 

then I add the cylender numbers at the bottom!

> # Disk DescriptorFile

version=1

CID=9428f535

parentCID=ffffffff

createType="fullDevice"



# Extent description

RW 63 FLAT "windowsxp.mbr" 0

RW 488281186 FLAT "/dev/sda" 63 



# The Disk Data Base 

#DDB 



ddb.toolsVersion = "6530"

ddb.adapterType = "ide"

ddb.virtualHWVersion = "4"

ddb.geometry.sectors = "63"

ddb.geometry.heads = "255"

ddb.geometry.cylinders = "30394"

I run this command: dd if=/dev/sda of=windowsxp.mbr bs=512 count=63
> kyle@kyle-desktop:~$ dd if=/dev/sda of=windowsxp.mbr bs=512 count=63
63+0 records in
63+0 records out
32256 bytes (32 kB) copied, 0.000803838 seconds, 40.1 MB/s


I then create the profile in WINDOWS and boot back into Ubuntu.

> Same error message here as in ROOT
VMware Player cannot find the virtual disk "/home/kyle/Desktop/VMware data 2/windows.vmdk". Please verify the path is valid and try again.
Cannot open the disk '/home/kyle/Desktop/VMware data 2/windows.vmdk' or one of the snapshot disks it depends on.
Reason: The system cannot find the file specified.


for reference here is my VMX
> #!/usr/bin/vmware
config.version = "8"
virtualHW.version = "4" 

uuid.location = "56 4d d7 78 be c8 5c e4-09 af 3d 04 d5 b0 cb ac"
uuid.bios = "56 4d d7 78 be c8 5c e4-09 af 3d 04 d5 b0 cb ac"

uuid.action = "create" 
checkpoint.vmState = "" 

displayName = "Windows XP" 
annotation = "" 
guestinfo.vmware.product.long = "" 
guestinfo.vmware.product.url = "" 

guestOS = "winxppro" 
numvcpus = "1" 
memsize = "128" 
paevm = "TRUE" 
sched.mem.pshare.enable = "TRUE" 
MemAllowAutoScaleDown = "FALSE" 

MemTrimRate = "-1" 
nvram = "WindowsXP.nvram" 
mks.enable3d = "FALSE" 
vmmouse.present = "FALSE" 
vmmouse.fileName = "auto detect" 

tools.syncTime = "TRUE" 
tools.remindinstall = "FALSE" 
isolation.tools.hgfs.disable = "FALSE" 
isolation.tools.dnd.disable = "FALSE" 
isolation.tools.copy.enable = "TRUE" 
isolation.tools.paste.enabled = "TRUE" 
gui.restricted = "FALSE" 

ethernet0.present = "TRUE" 
ethernet0.connectionType = "nat" 
ethernet0.addressType = "generated" 
ethernet0.generatedAddress = "00:0c:29:59:aa:eb" 
ethernet0.generatedAddressOffset = "0" 

usb.present = "FALSE" 
usb.generic.autoconnect = "FALSE" 

sound.present = "TRUE" 
sound.virtualdev = "sb16" 

ide0:0.present = "TRUE" 
ide0:0.fileName = "windows.vmdk" 
ide0:0.mode = "independent-persistent" 
ide0:0.deviceType = "rawDisk" 
ide0:0.redo = "" 
ide0:0.writeThrough = "FALSE" 
ide0:0.startConnected = "TRUE" 

ide1:0.present = "TRUE" 
ide1:0.fileName = "/dev/cdrom" 
ide1:0.deviceType = "atapi-cdrom" 
ide1:0.writeThrough = "FALSE" 
ide1:0.startConnected = "TRUE" 

floppy0.present = "TRUE" 
floppy0.fileName = "/dev/fd0" 
floppy0.startConnected = "TRUE" 

serial0.present = "FALSE" 
serial1.present = "FALSE" 
parallel0.present = "FALSE"


---

### Post by scxtt on 2007-06-06
you never did supply the output for these:

[B]slocate -u
slocate windows.vmdk[/B]

---

### Post by cliffd7 on 2007-06-07
Hi scxtt,
i was not sure whether the question was for me but assuming it was here is the answer:
~$ slocate -u
slocate: fatal error: You are not authorized to create a default slocate database!

slocate windows.vmdk does not do anything.

Cliffd7

---

### Post by RealEmotionX on 2007-06-07
I supplied the output above

---

### Post by scxtt on 2007-06-07
**@ cliffd7**: you need to use sudo (as far as i can remember REX was the root user)

**@RealEmotionX**: there are 3 commands there, you just supplied the output for **vmware-cmd -l** - which just showed that the vmware-cmd perl scripts aren't working (or it's some $PATH problem, which would be odd) ... the **slocate -u** & **slocate windows.vdmk** are the important ones ...

---

### Post by RealEmotionX on 2007-06-07
kyle@kyle-desktop:~$ sudo slocate -u
kyle@kyle-desktop:~$ slocate windows.vmdk
/home/kyle/Desktop/VMware data 2/windows.vmdk~
/home/kyle/Desktop/VMware data 2/windows.vmdk
/root/Desktop/windows.vmdk~
/root/Desktop/VMware data folder/windows.vmdk~
/root/Desktop/VMware data folder/windows.vmdk
kyle@kyle-desktop:~$ sudo vmware-cmd -l
sudo: vmware-cmd: command not found

---

### Post by scxtt on 2007-06-08
can you do an **ls -l /home/kyle/Desktop/VMware\ data\ 2/** and post it?
and **ls -l /root/Desktop/VMware\ data\ folder/** while you're at it?

---

### Post by RealEmotionX on 2007-06-08
> kyle@kyle-desktop:~$ ls -l /home/kyle/Desktop/VMware\ data\ 2/
total 84
-rw-r--r-- 1 kyle kyle  4415 2007-06-06 17:54 LOG
-rw-r--r-- 1 kyle kyle  4113 2007-06-06 17:53 LOG~
-rw-r--r-- 1 kyle kyle 16336 2007-06-06 17:53 vmware-0.log
-rw-r--r-- 1 kyle kyle 16712 2007-06-06 17:48 vmware-1.log
-rw-r--r-- 1 kyle kyle 16336 2007-06-06 18:04 vmware.log
-rw-r--r-- 1 kyle kyle   385 2007-06-06 18:06 windows.vmdk
-rw-r--r-- 1 kyle kyle   383 2007-06-06 18:04 windows.vmdk~
-rw------- 1 kyle kyle     0 2007-06-06 17:48 windows.vmsd
-rwxr-xr-x 1 kyle kyle  1715 2007-06-06 17:53 **windows.vmx**
-rw-r--r-- 1 kyle kyle  1715 2007-06-06 17:48 windows.vmx~


exactly as it appears in my console

> -rw-r--r-- 1 root root 16209 2007-06-05 21:57 vmware-0.log
-rw-r--r-- 1 root root 16209 2007-06-05 21:56 vmware-1.log
-rw-r--r-- 1 root root 16209 2007-06-05 21:55 vmware-2.log
-rw-r--r-- 1 root root 16209 2007-06-06 00:02 vmware.log
-rw-rw-rw- 1 root root   388 2007-06-04 20:31 windows.vmdk
-rw-r--r-- 1 root root   386 2007-06-04 20:23 windows.vmdk~
-rw------- 1 root root     0 2007-06-04 20:09 windows.vmsd
-rw-rw-rw- 1 root root  1715 2007-06-04 20:23 windows.vmx
-rw-r--r-- 1 root root  1715 2007-06-04 20:07 windows.vmx~


nothing bold this time

---

### Post by scxtt on 2007-06-08
well, your root "windows.vmx" isn't executable (or bold as it is for kyle) ...

not that i really think it should matter, but i'd move all the files is "VMware data 2" / "VMware data folder" somewhere else, preferrably directories w/ NO spaces ... or just change "VMware data 2" to **VMware_data_2** [ VMware_data_folder ] ... then make windows.vmx executable (**chmod +x windows.vmx**) ...

i forget if you're able to launch vmware (server or player?) ... ?

---

### Post by RealEmotionX on 2007-06-08
VMware Player cannot find the virtual disk "/home/kyle/Desktop/VMWAREdata2/windows.vmdk". Please verify the path is valid and try again.
Cannot open the disk '/home/kyle/Desktop/VMWAREdata2/windows.vmdk' or one of the snapshot disks it depends on.
Reason: The system cannot find the file specified.

Same situation. I even chmoded the file, but it was already Executable, according the ubuntu's file properties that you get from right clicking.

I am using PLAYER

---

### Post by scxtt on 2007-06-08
the chmodding was for the windows.vmx for root, since it didn't have +x permissions ... i'd download a pre-made "appliance" and see if that boots fine, so you can rule out problems w/ vmware on the whole ...

---

### Post by RealEmotionX on 2007-06-09
after trying to install VMware server through synaptic I couldent find the programs, and things got a little messy in my computer so I reinstalled ubuntu. I am going to attempt to install from a .tar.gz package instead of synaptic

---

### Post by scxtt on 2007-06-09
just make sure you've also got the kernel headers / source installed too, since it'll be needed to build the kernel module for vmware ... i installed it from source when i used ubuntu, and it was a pretty easy operation ...

---

### Post by longlegs on 2007-06-09
Hi ,

VMware Player cannot find the virtual disk "/root/Desktop/VMware data folder/windows.vmdk". Please verify the path is valid and try again.
Cannot open the disk '/root/Desktop/VMware data folder/windows.vmdk' or one of the snapshot disks it depends on.
Reason: The system cannot find the file specified.

I just transferred a VMf rom Win2k to ubuntu as follows.
1.removed VMPlayer 1.xx from ubuntu
2.downloaded and installed VMPlayer 2.0 from VMware site
3. made a dir I named Projects/VMware/MyWinVM
4. Copied the 8 files from the VM in win2k to the /MyWinVM dir
5. started VMPlayer
6 browsed to the MyWinVM and selecte the .vmx file

VMPlayer ran my win vm just fine.
It may be that your windows.vmdk file is not in the same dir as the .vmx
BTW there may only be 7 files because the 'suspend' file is not always there
Good luck
Longlegs

---

### Post by veloce on 2007-06-09
> **RealEmotionX said:**
> after trying to install VMware server through synaptic I couldent find the programs, and things got a little messy in my computer so I reinstalled ubuntu. I am going to attempt to install from a .tar.gz package instead of synaptic

Vmware server is in the commercial repository.  From my notes:

> VMWare Server is now in the commercial repository for Feisty.  Had to add the commercial repo. to the file /etc/apt/sources.list:
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

Full howto:
[http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html](http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html)


If you haven't started installing from the tar.gz file, I'd suggest using the one in the repositories because the upgrades are much easier and it doesn't have to compile anything.

The tar.gz will probably need you to get the "any to any" patch for configuration to work.  I had a link to the howto on this installation but have deleted it because I'm using the repo version.

---

### Post by tylerjames on 2007-06-09
argh..

for some reason vmware server still won't boot xp for me anymore. it was working fine last week, now whenever I click "Power on this Virtual Machine" is see the vmware boot screen, then nothing... just a black screen forever 

has anyone else had this problem and fixed it? i was really hoping that vmware would liberate me from hassles of dual-booting (unforunately i need to use windows to run some stupid blackberry JDE)

any help would be appreciated. i could try reinstalling windows xp on vmware... but if it's just going to do the same thing again i don't want to waste the time

thanks!

---

### Post by scxtt on 2007-06-10
could be that XP itself is having problems booting, in a VM-independent way ... do you have any "WRITELOCK" files in the directory for the VM when it's off?  do the logs shed any light?

---

### Post by longlegs on 2007-06-11
Just a thought,
If your XP vm was working under vmplayer version 1xxx and you downloaded the tar.gz from VMWare site the you may hve gotten the version 2.xxx which may not run the XP files correctly. 
BTW the repository does not have version 2.0xx yet. The VM2.0xx I downloaded from VMWare site works easier and quicker than the 1.xx (but you may have to revise your xp files)
Good Luck
longlegs

---

