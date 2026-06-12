---
title: "Ubuntu 20.04 &quot;cuda_11.1.1_455.32.00_linux.run.xx&quot; occupying all hard drive space"
date: 2021-06-22
forum: General Help
---

### Post by Dedalo on 2021-06-22
Hi. I have recently updated my ubuntu, from 18 to 20.04. It fixed some problems I used to have related to my graphics card, which is an nvidia gtx 1060. 

However, now I'm seeing in the home directory lots of files called "cuda_11.1.1_455.32.00_linux.run.xx" ranging from cuda_11.1.1_455.32.00_linux.run, cuda_11.1.1_455.32.00_linux.run.1, cuda_11.1.1_455.32.00_linux.run.2,..., cuda_11.1.1_455.32.00_linux.run.24. 

I have never noticed these files before, and they occupy a lot of space in my hard drive. 

So, I don't know why this files are appearing, I think that the system is somehow creating them, because I've noticed this when the system alerted me that there were only 800mb or so of free disk space. 

The first thing I would like to know is if it is safe to just remove all this files. 

And the second, how do I fix this? I'm not sure about this, but I think the system is just creating this files. I have tried to install cuda a long time ago, I'm not actually using it, so I could just remove cuda from my system, but I would also like to know how to do that safely. 

Another detail is that when I double click an icon on the desktop, trying to open a file or something, it just won't do it, I have to go to the terminal or do something else.

Thanks in advance.

---

### Post by monkeybrain20122 on 2021-06-22
cuda_11.1.1_455.32.00_linux.run is the cuda installer from Nvidia. If you make it executable and run it in the terminal, it will prompt you to install cuda. I don't know what the rest are, probably copies and I don't know how they end up in your system. When you do distro upgrade strange things happens especially if your configuration is not standard (say you installed the nvidia driver from some repository) so I usually just backup my data and do a clean install, also clear up a lot of clutters in the system.

I think they are safe to delete.

---

### Post by Dedalo on 2021-06-24
I've deleted all of them after I posted here. I didn't have any problem, and today it appeared again. I don't know why do they appear. But it is strange, all the files together made around 80gb. I know what you mean, it looks like the cuda installer, but not all the files have the same size, for example the one I have just deleted was only 300mb, but the ones that I've deleted the other day, some of them were around 3gb. I have installed cuda it like a year ago, but never used it. I have also noted that the anaconda2 folder occupies 8.5 gigabytes, I'm not sure if that is ok. Also, I have realized that most of the space in my storage drive isn't occupied in my home folder, but in systems folders, and it is a lot, like 100gb. I use gfortran, mpi, matlab, mathematica and some other stuff, but I don't think it should take so much space.

I am wondering if this cuda problem has something to do with a problem I've reported before updating the distro here: [https://ubuntuforums.org/showthread.php?t=2461102](https://ubuntuforums.org/showthread.php?t=2461102)

I had some problems with the nvidia drivers, but I think it was fixed after the guidance I've obtained here: [https://ubuntuforums.org/showthread.php?t=2435273](https://ubuntuforums.org/showthread.php?t=2435273)

I don't understand where this files comes from, are they being downloaded by the system? or just created by the system? it is very strange.

 I also have an nvme ssd installed that I'm not using, I think that I have to do something in the bios to start it, but a possibility would be just to made a fresh installation on that drive, and start all over again from there.

Thanks.

---

### Post by dddman on 2021-06-24
Not so long ago I needed to clean my file system and
```
df -h
```
showed me what to remove.

Will it help you any?

---

### Post by sudodus on 2021-06-24
I don't know about cuda and anaconda, but I have some experience of **nvme** drives.

- In newish computers it is straightforward to boot from nvme. I have a laptop that works that way.

- In older desktop or tower computers it is often possible to plug in a PCI card, where you can connect an nvme stick. I have such a computer and it is straightforward to use the nvme drive to store data and it is faster than an SSD connected via SATA. I have not been able to boot from it, but when I put the bootloader and /boot on another drive (which is bootable) the main system (the root file system, /) can be on the nvme drive and I can run the system.

If the nvme stick came with Windows, there may be RST, and you should erase it and replace it with AHCI to make file systems for Linux (and I think this is done in the UEFI/BIOS menu system).

---

### Post by Dedalo on 2021-06-24
Same here, don't know how to use the information. This is what I get with df -h:

Filesystem      Size  Used Avail Use% Mounted on
udev            7.8G     0  7.8G   0% /dev
tmpfs           1.6G  2.2M  1.6G   1% /run
/dev/sda1       220G  131G   78G  63% /
tmpfs           7.8G  152M  7.7G   2% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           7.8G     0  7.8G   0% /sys/fs/cgroup
/dev/loop1      100M  100M     0 100% /snap/core/11187
/dev/loop0      100M  100M     0 100% /snap/core/11167
/dev/loop2       56M   56M     0 100% /snap/core18/2074
/dev/loop3       56M   56M     0 100% /snap/core18/2066
/dev/loop4      162M  162M     0 100% /snap/gnome-3-28-1804/128
/dev/loop5      163M  163M     0 100% /snap/gnome-3-28-1804/145
/dev/loop6      219M  219M     0 100% /snap/gnome-3-34-1804/66
/dev/loop7      219M  219M     0 100% /snap/gnome-3-34-1804/72
/dev/loop8       66M   66M     0 100% /snap/gtk-common-themes/1515
/dev/loop9       65M   65M     0 100% /snap/gtk-common-themes/1514
/dev/loop10     2.3M  2.3M     0 100% /snap/gnome-system-monitor/157
/dev/loop11     2.3M  2.3M     0 100% /snap/gnome-system-monitor/148
/dev/loop13      18M   18M     0 100% /snap/pdftk/9
/dev/loop12      68M   68M     0 100% /snap/jupyter/6
/dev/loop14      51M   51M     0 100% /snap/snap-store/547
/dev/loop16     135M  135M     0 100% /snap/skype/173
/dev/loop15     9.2M  9.2M     0 100% /snap/python38/22
/dev/loop17     409M  409M     0 100% /snap/pycharm-community/238
/dev/loop18     296M  296M     0 100% /snap/vlc/2288
/dev/loop19     136M  136M     0 100% /snap/skype/176
/dev/loop20      51M   51M     0 100% /snap/snap-store/542
/dev/loop21     409M  409M     0 100% /snap/pycharm-community/240
/dev/loop22     296M  296M     0 100% /snap/vlc/2103
tmpfs           1.6G   20K  1.6G   1% /run/user/121
tmpfs           1.6G  4.4M  1.6G   1% /run/user/1000

---

### Post by monkeybrain20122 on 2021-06-24
There seems to be a lot of snap stuffs. I am just wondering maybe one of those is malfunctioning ... There are talks of packaging cuda in snap-core, so I don't know.. [https://forum.snapcraft.io/t/nvidia-cuda-on-ubuntu-core/292](https://forum.snapcraft.io/t/nvidia-cuda-on-ubuntu-core/292)

---

### Post by dddman on 2021-06-24
That is a large snap collection you have there.  I also had a large snap collection and decided to clean it up.  What started out as a few things ended up being total snap removal.  I wanted my space back mainly.  I also read that too many snaps can cause performance problems, which it did not in my case.
[https://ubuntuforums.org/showthread.php?t=2463316&highlight=](https://ubuntuforums.org/showthread.php?t=2463316&highlight=)
If one day I decide I need snap, then I will reinstall.  I see nothing wrong with snaps except for the space required.

Clean yours up, remove snap packages your not using.
```
sudo snap remove [COLOR=#006400]*PackageName*[/COLOR]
```[COLOR=#008000][/COLOR][COLOR=#006400][/COLOR]
Snap will not allow you to remove any snap system packages or packages in the wrong order.

May not be cuda related, but should help overall.

I did a search on "removing cuda from ubuntu" and received several hits.  I have no experience with cuda so I can only point to a possible solution.

---

### Post by monkeybrain20122 on 2021-06-24
> **dddman said:**
> 


I did a search on "removing cuda from ubuntu" and received several hits.  I have no experience with cuda so I can only point to a possible solution.

Well not sure if OP has cuda installed. It just looks like somehow the cuda installer was downloaded (many times?) and dumped into his $HOME. In order to talk about how to remove cuda OP needs to find out whether cuda is installed in the first place. Depending on how it is installed (if installed) the way to remove is different. If use Nvidia's deb repository or Ubuntu's then it is just apt remove, if it is from run file then just delete the /usr/local/cuda, but snap might have installed some cuda components in that case you need to uninstall accordingly. This is very strange.

---

### Post by Dedalo on 2021-06-25
I don't know what functionality could I lose by removing the snaps (I actually don't know what a snap is, but I see it is related to some programs I use, like skype). Anyway, I guess I could just reinstall what I need. But yes, I don't know what the problem is, or why this cuda installer appears (I have just deleted another file of that type, with 3.5gb). I think that it not only has been downloaded many times, it looks like it also keeps doing it, quiet randomly. I would like not to have problems with the drivers by uninstalling something inappropriately (I have work to do, and I wouldn't like to lose time on this kind of stuff, I should also make a backup before trying anything), but I think I have to do something about this.

BTW, I do have cuda installed: 
:~$ nvcc --version
nvcc: NVIDIA (R) Cuda compiler driver
Copyright (c) 2005-2019 NVIDIA Corporation
Built on Wed_Oct_23_19:24:38_PDT_2019
Cuda compilation tools, release 10.2, V10.2.89

How should I proceed to remove the snaps? and which of the listed should be safe to remove? I don't care much about anaconda and pycharm, I might reinstall them if I need'em. I'm afraid if I touch cuda related things, I'll have problems with my gpu drivers.

PD: It just did it again, two files appeared on my home folder. This is driving me crazy.

I have found this in google: [https://stackoverflow.com/questions/56431461/how-to-remove-cuda-completely-from-ubuntu](https://stackoverflow.com/questions/56431461/how-to-remove-cuda-completely-from-ubuntu)

If I have to uninstall my nvidia drivers, how should I do after it to install them properly? I have asked this before, and I have done it wrong in the past, which brought me problems, so I would like to know in case I need it.

---

### Post by Dedalo on 2021-06-25
I think that at some point I have installed this by using:

wget [https://developer.download.nvidia.com/compute/cuda/11.1.1/local_installers/cuda_11.1.1_455.32.00_linux.run](https://developer.download.nvidia.com/compute/cuda/11.1.1/local_installers/cuda_11.1.1_455.32.00_linux.run)

sudo sh cuda_11.1.1_455.32.00_linux.run

Is there some reason why the system could be doing a loop in this wget? I've installed it like last year, and the problem started when upgraded ubuntu 18 to 20.04. Is there a way to avoid the system doing this? like blocking the nvidia webpage or something?

---

### Post by Dedalo on 2021-06-25
Ok. Sorry for the consecutive posting. Howver, I have just uninstalled cuda successfully without any problems by doing:

sudo apt-get --purge remove "*cublas*" "cuda*" "nsight*"

sudo rm -rf /usr/local/cuda* 

I will let you know if the problem persists (if this file appears again, I think it should be anaconda or something I have installed to use cuda on python in that case).

---

### Post by Dedalo on 2021-06-25
Ok. It just did it again, and I realized what is happening. I had this file, a .txt file on my desktop, that I usually open with gedit (it is what it used to do before I upgraded my ubuntu version), because I have commands I use frequently, so I don't have to remember them, or do the search, whatever. One of this commands, which I have just saw a few posts before this one was the wget related one. The thing is that when I double click this .txt file, it doesn't jump to the gedit anymore (that is what it used to do in ubuntu 18), it doesn't do anything. Or that is what I thought, because a second ago I did it while having my home directory folder open, and just when I double clicked on it, the file appeared! so what it seems to be happening is that, my .txt file on desktop doesn't start with gedit when I double click on it, instead it looks like it was like reading it from bash or something. Crazy sh*t.

Now, I don't know why this happen with the files on the desktop, it doesn't happen when I double click a file on the home directory for example. And now I actually see an error message that says something about "execution" when I double clic de .txt file.

And it actually was that specific .txt file, I just copied the stuff in it to other file and deleted, end of the problem.

Thank you all.

---

### Post by CatKiller on 2021-06-25
> **Dedalo said:**
> Now, I don't know why this happen with the files on the desktop, it doesn't happen when I double click a file on the home directory for example.
At some point you've marked that file as being executable, or some extension that you're using to get around Gnome's aversion to files on the desktop has.

---

