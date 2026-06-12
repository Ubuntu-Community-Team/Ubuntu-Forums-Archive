---
title: "Unable to write new files to my aufs storage pool"
date: 2014-02-27
forum: General Help
---

### Post by Dana_Pagliarulo on 2014-02-27
I am on Ubuntu 13.10. I have 8 HDDs. 5 of which I am pooling together with aufs. All of the drives are full except 2. I have highlighted the pooled drives below.

Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       455G   87G  346G  20% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           389M  5.5M  384M   2% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.9G  4.0K  1.9G   1% /run/shm
none            100M     0  100M   0% /run/user
**/dev/sdb1       917G  870G  689M 100% /media/JP2940HD2V7XYC**
**/dev/sde1       1.8T  688G  1.1T  40% /media/S240WFJG**
**/dev/sdf1       688G  649G  4.6G 100% /media/5VPB955M**
**/dev/sdd1       917G  849G   22G  98% /media/JP2940HD2VD72C**
**/dev/sdg1       917G  865G  5.5G 100% /media/WD-WCC1S4134840**
/dev/sdc1       2.7T  928G  1.7T  36% /media/WD-WCC4N0655997
aufs#none       5.2T  3.9T  1.1T  79% /storage
/dev/sdh1       2.7T  928G  1.7T  36% /media/W1F2YG0M

As you can see, my aufs pool at /storage is showing 79% capacity with 1.1T of free space remaining. However, I am not able to write new files to my storage pool.

Here is my fstab entry...
aufs#none /storage aufs br:/media/JP2940HD2V7XYC=rw:/media/JP2940HD2VD72C=rw:/media/5VPB955M=rw:/media/WD-WCC1S4134840=rw:/media/S240WFJG=rw,sum,create=pmfs 0 0

I have tried create=mfs and create=pmfs thinking this has something to do with it.

I have also replaced aufs with mhddfs and it still works, but I prefer to use aufs due to it's kernel support.

Anyone have an idea what could be going on here. I am no expert on aufs, nor do I want to be. It seems to me that this should just continue to work until all of my drives are full in the pool.

---

### Post by andymurn on 2014-09-10
I initially was using create=pmfs mode as well until it started saying I was out of free space. The problem with pmfs mode is that it will only write to disks that contain the parent folder.
My directory structure looks something like this:

/storage/TV/Show Name/Season 1/video.mkv

In pmfs mode the disk containing season 1 of the show was at 100% and when I tried to write the episodes from season 2 to the disk it told me that the disk was full even though I had TBs of free space on available in /storage/TV.
I incorrectly assumed that in pmfs mode it would create the 2 necessary directories, /storage/TV/**Show Name/Season 2**, on another disk once the disk containing the show was full.

In the newer versions of aufs 3.9 and up (I believe) there is a new create mode called pmfsrr which seems more like what you were looking for. It enables aufs to write to other disks when the drive/s containing the parent folders get full in a round robin fashion. A snippet from the aufs man page:
> **create=pmfsrr:low[:second] **[COLOR=#000000][FONT=Times New Roman]Firstly selects a writable branch as the ’pmfs mode.’ If there are less than ’low’ bytes available on all branches where the parent dir exists, aufs selects the one which has the most free space regardless the parent dir.[/FONT][/COLOR] 
I am unsure why mfs mode would not have worked as it would just write everything to **/media/S240WFJ** since it has the most free space unless you didn't unmount and remount the drive pool after making the changes in the configuration or had permissions configured incorrectly.

---

