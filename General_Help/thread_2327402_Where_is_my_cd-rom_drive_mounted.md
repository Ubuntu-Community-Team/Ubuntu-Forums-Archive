---
title: "Where is my cd-rom drive mounted?"
date: 2016-06-10
forum: General Help
---

### Post by schnuckenack2 on 2016-06-10
Hello,

I want to make an image of an audio cd with dd but I'm having trouble finding out the mountpoint.

$ mount

output is:

```
/dev/sda7 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
/dev/sda6 on /home type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=brian)
```

---

vlc would show /run/user/1000/gvfs/cdda:host=sr0/Track 1.wav in the "Last opened" list
--

Thank you!

---

### Post by X-RED_Tech on 2016-06-10
/dev/sr0 perhaps?

---

### Post by schnuckenack2 on 2016-06-10
Thanks but nope, not working :(

dd: error reading from »/dev/sr0": Input-/Outputerror

---

### Post by sudodus on 2016-06-10
Check with ***sudo lsblk***

```
[COLOR="#0000FF"]sudo lsblk[/COLOR]
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 298,1G  0 disk 
&#9500;&#9472;sda1   8:1    0    80G  0 part 
&#9500;&#9472;sda2   8:2    0    64G  0 part 
&#9500;&#9472;sda4   8:4    0     1K  0 part 
&#9500;&#9472;sda5   8:5    0     8G  0 part [SWAP]
&#9500;&#9472;sda6   8:6    0    32G  0 part 
&#9500;&#9472;sda7   8:7    0    14G  0 part 
&#9492;&#9472;sda8   8:8    0 100,1G  0 part /
sdb      8:16   0  55,9G  0 disk 
&#9500;&#9472;sdb1   8:17   0   3,7G  0 part 
&#9500;&#9472;sdb2   8:18   0   320M  0 part 
&#9500;&#9472;sdb4   8:20   0     1K  0 part 
&#9492;&#9472;sdb5   8:21   0  51,9G  0 part 
[COLOR="#FF0000"]sr0     11:0    1  1024M  0 rom[/COLOR]
```

My CD/DVD drive is recognized as **/dev/sr0** and if you mount it you will see a mountpoint too. Example: a Clonezilla CDROM:

```
[COLOR="#0000FF"]sudo lsblk[/COLOR]
...
[COLOR="#FF0000"]sr0     11:0    1   112M  0 rom  /media/olle/2.0.1-15-i686-pae[/COLOR]
```

***df*** shows only mounted drives:

```
[COLOR="#0000FF"]df -h[/COLOR]
Filesystem      Size  Used Avail Use% Mounted on
udev            2,0G     0  2,0G   0% /dev
tmpfs           405M  6,6M  398M   2% /run
/dev/sda8        99G   32G   63G  34% /
tmpfs           2,0G  1,1M  2,0G   1% /dev/shm
tmpfs           5,0M  4,0K  5,0M   1% /run/lock
tmpfs           2,0G     0  2,0G   0% /sys/fs/cgroup
cgmfs           100K     0  100K   0% /run/cgmanager/fs
tmpfs           405M   36K  405M   1% /run/user/1002
tmpfs           405M   12K  405M   1% /run/user/108
[COLOR="#FF0000"]/dev/sr0        112M  112M     0 100% /media/olle/2.0.1-15-i686-pae[/COLOR]
```

---

### Post by schnuckenack2 on 2016-06-10
Hello sudodus,

> ***sudo lsblk ***shows
NAME   MAJ:MIN  RM   SIZE RO TYPE MOUNTPOINT
sda          8:0            0 465,8G   0 disk 
&#9500;&#9472;sda1   8:1            0 252,6G   0 part 
&#9500;&#9472;sda2   8:2            0        1K   0 part 
&#9500;&#9472;sda5   8:5            0     3,9G   0 part    [SWAP]
&#9500;&#9472;sda6   8:6            0 179,5G   0 part    /home
&#9492;&#9472;sda7   8:7            0   29,7G   0 part    /
sr0         11:0            1 405,6M  0 rom  


How do I mount it?

---

### Post by X-RED_Tech on 2016-06-11
If you open it in the file manager it will be automagically mounted.

---

### Post by yancek on 2016-06-11
> How do I mount it? 		

Create a mount point.  Below is an example, you can change it to whatever you want.

```
sudo mkdir /mnt/cdrom
```

Then mount it.

```
sudo mount /dev/sr0 /mnt/cdrom
```

---

### Post by sudodus on 2016-06-11
> **schnuckenack2 said:**
> Hello sudodus,

How do I mount it?

If it is a CDROM (with a file system), you mount it as described in the previous posts. But in your original post you wanted to make an image of the disk, an audio CD. Then you need not and should not mount it. Just make an image of it.

There are tools with a graphical user interface for that task, for example ***k3b***. Maybe what you want is 'Copy medium', or 'Rip audio CD'.

If it is not installed in your flavour of Ubuntu, you can install it with

```
sudo apt-get install k3b
```

---

### Post by schnuckenack2 on 2016-06-11
Expected a "RTFM" answer but thanks for being nice too boons.

Thanks [**[COLOR=#000000]yancek[/COLOR]**]("http://ubuntuforums.org/member.php?u=1928724&")

Yet this still produces some error "Superblock couldn't be read"

[**[COLOR=#000000]X-RED_Tech[/COLOR]**]("http://ubuntuforums.org/member.php?u=2022583")

Nah, Ctrl+L produces cdda://sr0/
I wonder if this solution works for anyone?

[**[COLOR=#DD4814][B]sudodus**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1499021")

I will try this

---

### Post by schnuckenack2 on 2016-06-12
Question for [**[COLOR=#DD4814][B]sudodus**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1499021")

I installed k3b but under [Settings] -> [Configure K3b] I can't find an option to create an .iso image. It will only create .wav files or an ".img" file

Thanks

---

### Post by yancek on 2016-06-12
You can't mount a blank CD/DVD.  It needs to have some type of filesystem on it which is what is actually mounted.

With k3b, you can go to whichever iso file you want to burn and right click on it and then select the option to "open with k3b".  Or you can open k3b and click on the Tools Tab and then select Burn Image and at the top click on the folder icon to navigate to the iso.  Make sure you have a blank CD/DVD in the tray before doing this.  After selecting the iso, click the Start tab at the bottom.

---

### Post by schnuckenack2 on 2016-06-12
As I stated, I want to create an .iso of an audio-cd that I own. Not burn a new cd from an existing .iso file.

---

### Post by X-RED_Tech on 2016-06-12
With K3b: Select copy medium then press burn. In this dialog tick "only create image"; in the tab "image" you can choose a different folder.

---

### Post by mc4man on 2016-06-12
> **schnuckenack2 said:**
> Hello,

I want to make an image of an audio cd _with dd_ but I'm having trouble finding out the mountpoint.

Not going to happen. Find yorself an app that can do that, maybe brasero,  AcetoneISO, cdrdao or the likes

---

### Post by schnuckenack2 on 2016-06-12
> **X-RED_Tech said:**
> With K3b: Select copy medium then press burn. In this dialog tick "only create image"; in the tab "image" you can choose a different folder.
Thanks, but under the tab I may only select a folder :confused: 

Same goes for Brasero. *It doesn't show an option for .iso*, only for tools: ["cdrdao-image", "CUE-Image", "Readcd/Readom-image"]

---

### Post by sudodus on 2016-06-12
Please select "only create image* if that is what you want.

An ISO file as an image of a CDROM with an ISO9660 file system, and an audio CD is something different. Either "only create image* or copy the disk to another disk.

In ***k3b:***

***Tools -- Copy medium... -- Only create image***

An alternative is

***Tools -- Rip Audio CD ...***

"Rip" the sound-tracks, if you want music files, that you want to play in your computer, a mobile phone, an mp3-player ...

---

### Post by mc4man on 2016-06-12
What do you think you're going to do with an .iso file of an audio cd?
(- which I doubt is possible anyway.. without some conversions

You could do something [like this ]("http://ubuntuforums.org/showthread.php?t=771986&p=12317664&viewfull=1#post12317664")- (bin & toc to iso & cue

---

### Post by bapoumba on 2016-06-12
Which audio CD ? Trying to get around restrictions ?

---

### Post by X-RED_Tech on 2016-06-12
> **bapoumba said:**
> Which audio CD ? Trying to get around restrictions ?

That would explain dd which theoretically should result in a bit by bit copy. But it will also copy the "copy protection".

---

### Post by mc4man on 2016-06-12
Has nothing to do with restrictions, dd can only work when there is a file structure & an .iso can only represent a file structure. (neither of which is an audio cd
I would ?assume? the hope here would be to have a 'file' that can be played as if it's the audio cd without ripping or actually playing the audio cd itself.

In that case a bin & cue  is best bet. There are linux tools that will do that though as I remember sometimes they seem to work but produce static. So to quickly reacquaint myself with a known working method- 

Had wine installed so downloaded & installed Imgburn
Added the cdemu ppa & installed gcdemu cdemu-client
Put an audio cd in drive, opened Imgburn & choose the Disk to Image option, that produced 2 files, by default generically named Image.bin & Image.cue,  scr. 1 & 2

Then mounted the .cue file with - 
 cdemu load 0  /home/doug/.wine/drive_c/Image.cue

At this point it's seen just like any 'real' audio cd & can be played as such, scr. 3 

lshw on that mounted image - 
 ```
*-cdrom
       description: DVD-RAM writer
       product: Virt. CD/DVD-ROM
       vendor: CDEmu
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sr1
       version: 1.10
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: status=ready
     *-medium
          physical id: 0
          logical name: /dev/sr1

```

---

### Post by bapoumba on 2016-06-12
Jefferson Airplane !

---

### Post by schnuckenack2 on 2016-06-13
Thank you for your numerous answers. What I thought I could have was some bit-to-bit-copy-file which I could then mount eventually. But it seems to be not a trivial task with an audio cd. I guess I will just rip it to mp3 then. :(

Thanks

---

### Post by sudodus on 2016-06-13
I think ripping is a good way to get access to the sound tracks in a flexible way :-)

-o-

You can also try to "Only create image" in ***k3b***. I don't think it works with dd from an audio CD.

---

### Post by mc4man on 2016-06-13
> **schnuckenack2 said:**
> Thank you for your numerous answers. What I thought I could have was some bit-to-bit-copy-file which I could then mount eventually. But it seems to be not a trivial task with an audio cd. I guess I will just rip it to mp3 then. :(

Thanks
Then rip to flac which maintains quality & offers some space saving. 
Here I've got hundreds of cd's that I'll likely need to part company with soon so am ripping all to flac. Flac can be restored easily back to optical media as an audio cd or converted to more portable formats when desired.

---

