---
title: "Need help attempting recover of failed Windows 7 Drive"
date: 2014-02-11
forum: General Help
---

### Post by v-ben on 2014-02-11
Hello - I am trying to recover some files on a failed Windows 7 Drive (attempts to boot - wants to run system restore... then says that I need to locate the drivers for the hard-drive.. all the while, the HDD is chirping like a cricket) The interesting thing is that when I click browse to locate the driver - I can browse to all of the folders on the HDD that I am needing to get the information off of.. It doesn't show anything for it since it will only list driver files.

I have Ubuntu on a live usb drive, but I can get my disk to mount... When I run:
mount -t ntfs-3g /dev/sdb1 /media/disk -o force

It returns
"Mount is denied because the NTFS volume is already exclusively opened. The volume may be already mounted, or another software may use it which could be identified for example by the help of the 'fuser' command."

I tried the following fuser command:
fuser -k /dev/sda1

and it doesn't return anything.. and I receive the same error when I attempt to mount the drive.

When trying to mount from the "Home" folder - I can see my volume - Right Click and select Mount - The HDD makes its chirping sound and sits for like 5 mins - Then the system returns the error:
"Unable to mount Acer

Error mounting: mount exited with exit code 13:ntfs_attr_pread_i:ntfs_pread
failed: Input/output error
Failed to read NTFS $Bitmap: input/output error
NTFS is either inconsistant, or there is a hardware fault, or it's a
SoftRAID/FakeRaid hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very 
important! If the devise is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahabcc1). Please see the 'dmraid' documentation 
for more details.

To my knowledge this was not a RAID setup at all.. It was a HDD in an Acer ASPIRE ONE, and was the only HDD.

Thanks in advance for any help!
-Ben

---

### Post by Mark Phelps on 2014-02-11
In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions. Your best bet at recovering data in a useful form from the Windows filesystem is to do as indicated below ...

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of RecoverMyFiles from [http://getdata.com](http://getdata.com).
5) Right-click the RecoverMyFiles shortcut and select "Run as Administrator"
6) Select the option to Recover a Drive
7) You will get a list of drive, scroll down to find the one for your USB stick or memory card
8) Select Automatic Driver recovery, press Start button
9) It will run for a while but when done, will show a directory tree in the left pane. Do NOT interrupt it.
10) When done, browse the folders in the directory tree -- and be SURE to check the filesizes of the files you want to recover.  If the filesize is zero, the file is trashed and you will NOT be able to recover it.

If the files look OK, you will need to contact Runtime Software to purchase a license for the recovery. You won't have to reinstall the app; instead, they will email you an activation code which you can use to turn on the recovery feature.

According to their website, the "standard" version of the app is $70 USD.  They also have a Pro version for $99 dollars, but if you go to their website, you can compare versions and features.

Your data ... your money ... your choice.

---

