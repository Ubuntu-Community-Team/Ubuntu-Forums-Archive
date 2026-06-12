---
title: "Have exhausted my limited skillset - Need help getting media server to see second HD"
date: 2016-04-06
forum: General Help
---

### Post by javaikky on 2016-04-06
Hi all, I've spent hours upon hours trying to figure this out. I have a second mounted HD with all my media files stored (Formatted ext 4) No matter what I do, I can't get Emby(Or Plex)to see any files on the mounted drive.  

I've edited Fstab, and i've set the drive to auto mount, but I can't seem to get beyond that. 

Thanks in advance for any help/education guidance.  I've attached a few screens, and sorry if I've done something really dumb, or if this is in the wrong place. You guys and gals rock!

---

### Post by oldfred on 2016-04-06
Your fstab entry does not look correct.
Copy the example posted here, but use your UUID and mount point.

 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead. 

      
 ** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. Make sure you have partition unmounted if previously mounted:
sudo mount -a 

And did you give yourself ownership & permissions.
Not sure if Plex needs specific permissions or not.

If already mounted with fstab use that mount.
This is a manual mount and uses that mount to change ownership & permissions. Be sure to unmount if you use this and then edit fstab after. As it cannot be mounted to two places.


 #if not known to list partitions, change sda5 to your data partition or create multiples with different mount points
# is comment, do not type
sudo parted -l
sudo mkdir /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown -R $USER:$USER /mnt/data

---

### Post by ajgreeny on 2016-04-07
Your fstab file is certainly incorrect and will not mount the sdc1 partition as both lines are commented out with a # at the start; you should also use UUIDs not dev/sdx# nomenclature as the latter can change sometimes but UUIDs never do unless you reformat the partititon.

Who is the owner of the files and folders in that sdc1 partition? 
Ownership is the most likely cause of your probem, and may be helped if not totally solved by making sure you are a member of group plex  and that user plex is a member of your username group.

Then make sure that the mountpoint of that sdc1 partition is owned recursively by yourself, as noted by oldfred above.

---

### Post by javaikky on 2016-04-07
Thanks guys for your help going to try to edit the fstab file correctly now.  I'm the owner of the disk (It was originally root, I used chown to make myself owner.

---

### Post by javaikky on 2016-04-07
I think I discovered another issue.  The UUID in FSTAB listed as swap is actually the disk I'm trying to use. Any modifications I've made to that line, or adding a new line using the same UUID have caused it to crash. (I was able to restore by editing with vi in recovery mode). 

I know I'm missing something incredibly simple here.

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=7482b275-7946-4451-a804-d474276873fa /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=5ca39c3c-3288-4f1b-8eb3-53e7ad94a196i none          swap    sw                 0      0

---

### Post by ajgreeny on 2016-04-07
We are working slightly in the dark at the moment so let's see the output of command ```
sudo blkid -c /dev/null
``` which will give us the UUIDs of all partitions, and hopefully allow us to work out more effectively what your /etc/fstab file should contain.

As oldfred said, after editing fstab you should always run ```
sudo mount -a
``` to check syntax and errors and avoid potential crashes as you saw.

---

### Post by javaikky on 2016-04-07
Thanks ajgreeny for the quick reply. 

Also one correction to earlier. SDC1 is the drive I'm trying to work from. 

output of blkid: 
/dev/sda1: UUID="7482b275-7946-4451-a804-d474276873fa" TYPE="ext4" PARTUUID="bda6888d-01"
/dev/sda5: UUID="5ca39c3c-3288-4f1b-8eb3-53e7ad94a196" TYPE="swap" PARTUUID="bda6888d-05"
/dev/sdb1: PARTUUID="8538e9d2-01"
/dev/sdc1: LABEL="md" UUID="f43b8401-c992-4a35-baf0-ab5f231fd28e" TYPE="ext4" PARTUUID="7d7058a0-01"

---

### Post by javaikky on 2016-04-07
Also really quick just so we have fully transparency - I did edit Fstab again(see below), and I added emby to the user group I gave access to the folder. 

[I]Fstab: # /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=7482b275-7946-4451-a804-d474276873fa /               ext4    errors=remount-ro 0       1
/swapfile   none    swap    sw    0   0
UUID=f43b8401-c992-4a35-baf0-ab5f231fd28e /media/rocky/md1 ext4 defaults,noatime 0 2[/I]

**Permissions for folder:  I added user emby to group rocky **

[I]rocky@rocky-Aurora:~$ stat /media/rocky/md1
  File: &#8216;/media/rocky/md1&#8217;
  Size: 4096      	Blocks: 8          IO Block: 4096   directory
Device: 821h/2081d	Inode: 2           Links: 5
Access: (0755/drwxr-xr-x)  Uid: ( 1000/   rocky)   Gid: ( 1000/   rocky)
Access: 2016-04-07 08:35:54.634817693 -0500
Modify: 2016-04-07 11:33:03.142778740 -0500
Change: 2016-04-07 11:33:03.142778740 -0500
 Birth: -
[/I]

---

### Post by oldfred on 2016-04-07
The default mount uses label (md) and is in /media/$USER.
You can create a mount point that is the same or different than the label.
I have used Data as label, and /mnt/data as mount and gotten confused as case in Linux is important.
I label all partitions, but only mount a few like my /mnt/data.

If you want to have your mount seen in the left panel of Nautilus automatically, you need to mount in /media.
If you do not want the mount shown, then use /mnt. I use /mnt as I also use linking to add all the folders into /home. Only occasionally do I have to use Nautilus and drill down from Computer or / to /mnt to /mnt/data.

I think you still have to create mount /mnt/md, /media/md or /media/$USER/md if using fstab. And then set ownership & permissions.

# Manual entry for sdc1
       UUID=f43b8401-c992-4a35-baf0-ab5f231fd28e /media/md ext4 defaults,noatime 0 2 

Change mount point to one you have created, and possible change parameters.
I sometimes use defaults, relatime which is defaults plus relatime or defaults,noatime.
I think the noatime is more for SSD to reduce writes, but can be used anywhere.

See this for more details on parameters
man mount
      
 Since Hardy (or Intrepid), Ubuntu adds the relatime option by default.
relatime = relatime + defaults = relatime, rw, suid, dev, exec, auto, nouser and async

---

### Post by javaikky on 2016-04-07
Holy crap man! You did it!!!!!!!!  Thanks so much, to you and ajgreeny! Not only did we get this thing working, I learned a ton in the process.   Thanks for helping out, and being good people.  I'll pay this forward with things I'm awesome at to someone else. 

Thanks!!!

---

