---
title: "VirtualBoxt: create a &quot;Ramdisk&quot; for better memory management between host and guest"
date: 2007-05-19
forum: General Help
---

### Post by kilou on 2007-05-19
Hi,

first I'm a newbie and maybe all this is ridiculous but please consider it and let me know what you think and if it is possible to achieve.

I'm using VirtualBox on a Ubuntu 7.04 host system and run XP as guest. It runs pretty well but I'd like to enhance the memory management of this system because for now I need to assign a fixed amount of RAM to the virtual machine, which means that when part of this assigned RAM is not used it is wasted because it is not given back to the host system. Moreover sometimes I need to run memory hungry applications such as Photohop in the guest system so I'd need to assign more RAM to the VM....but again when I'm not using Photoshop but run MSExcel I'd waste too much memory for the host system. My laptop has max 1Gb RAM support and I already have 1Gb RAM so I'm looking for a way to dynamically assign memory to the VM depending on the needs! 

My idea would be to assign a very small amount of RAM to the virtual machine so that XP is forced to use the pagefile (swap). You'll tell me that this is not good since swap is usually extremely slow but here comes the possible trick: create a sort of RAMDISK (portion of RAM used as a harddrive) in Ubuntu and store the XP pagefile on it through some sort of folder sharing or similar. The condition is that the size of this ramdisk must grow and shrink according to the pagefile size. If this can be achieved XP would be forced to use the pagefile but since the pagefile is stored in the RAM it wouldn't degrade swap performances. However the advantage over direct RAM assignment would be that the RAM used by the virtual machine would depend on its needs rather than being assigned a fixed size!! 

Usually ramdisk have a fixed size so this is not going to work. However it may be possible to achieve a similar thing with tmpfs which is a temporary file system that allow to store files in the swap space of linux. According to this article ([http://www.solarisinternals.com/si/reading/tmpfs.pdf](http://www.solarisinternals.com/si/reading/tmpfs.pdf)) this is supposed to be as fast as a ramdisk in the RAM but it provides additional benefits (mainly that the size can be adjusted!). Here is an example:

**mount -t tmpfs tmpfs /home/user/stuff**

That will create a variable sized ramdisk based upon the size of the files located in /home/user/stuff 

Now imagine that you mount something like **mount -t tmpfs tmpfs /ramdisk** and you make this folder available to XP guest (as a new partition) by some mean. Then you move the XP pagefile on this ramdisk folder and you set the XP virtual machine to use only 10Mb of RAM (assigned RAM in VirtualBox). This would force XP to use the pagefile whose size would vary according to the applications launched in XP, and thus the size of the tmpfs ramdisk would vary accordingly. This means that when you launch Photoshop in XP, the ramdisk would grow BUT when you close Photoshop the ramdisk would shrink and thus release memory back to the host system (something that is not yet possible in VirtualBox, even on the upcoming version 1.4 where ram usage will only be allowed to grow but memory cannot be given back to the host system).

OK now the questions:

- Is all this completely non sense ??

- What is the minimal RAM amount used to boot XP until the pagefile is used?? Is it possible to assign only 10Mb RAM to XP and boot it ?? Another way to ask this is: is it possible to boot XP using its pagefile as memory??

- Since the Linux ramdisk (tmpfs) must be shared with XP to allow the pagefile to be located on it, do you think that folder sharing would be sufficiently fast to allow this (probably not Samba but the built-in folder sharing of Virtualbox)???

- XP pagefile can be moved on any partition detected by Windows. Is there a way to share /ramdisk with XP but make it seen as a partition rather than a folder in XP?

- any other considerations or opinion ??

Thanks

---

### Post by kilou on 2007-05-19
It seems that ramfs is able to grow and shrink according to its content so this would be a preferable option since it creates a real ramdisk (in the physical RAM) while tmpfs uses the swap space.

---

### Post by kilou on 2007-05-19
Here is what I did for now:

# Create ramdisk of max 384Mb
sudo mkdir /mnt/ramdisk
sudo mount -t ramfs RAMDISK /mnt/ramdisk -o maxsize=384000
sudo chmod -R 777 /mnt/ramdisk

VBoxManage sharedfolder add "Windows XP" -name RAMDISK -hostpath /mnt/ramdisk

In XP:
net use J: \\vboxsvr\RAMDISK

Now the ramdisk is accessible to XP as a shared folder on J:\ I have then tried to move the XP pagefile on J:\ through registry editing:

run regedt32.exe
HLM/SYSTEM/ControlSet001/Control/Sesssion Manager/Memory Management/Paging Files = J:\pagefile.sys 4 384
HLM/SYSTEM/ControlSet002/Control/Sesssion Manager/Memory Management/Paging Files = J:\pagefile.sys 4 384

But XP doesn't want to put the pagefile on J: and leaves it on C: :( However if I set Paging Files = C:\folder\pagefile.sys 4 384 then XP moves the pagefile in "C:\folder".......

Is there another way to force XP to put pagefile.sys on the network drive J:\ ????

---

### Post by kilou on 2007-05-26
OK the problem seems to be that the pagefile initialisation occurs way before the initialisation of network drives in XP. Therefore even if we tell XP registry to place the pagefile on network drive J: when it tries to do so on reboot the network is not yet initialised so there is no J: yet and thus XP forces the pagefile on C: :(

So what we'd need is a way to delay the initialisation of the pagefile after the one of network drives or have a mean to start network drives BEFORE the pagefile is initialized...like starting the network and create the J drive in autoexec.bat or something???

If anybody knows if this can be done and how, plese post ;)

---

