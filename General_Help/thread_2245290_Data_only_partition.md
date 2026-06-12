---
title: "Data only partition"
date: 2014-09-22
forum: General Help
---

### Post by giannhs905 on 2014-09-22
Hello,
I would like to create a partition that will hold my data.
What I need is this partition to be separate from my ubuntu installation so in case that something goes wrong it would be possible to get my files back.
Scenario: bad use leads ubuntu to break down.Then I format the ubuntu partition again either installing ubuntu or windows.And I get my files back from that separate partition.
Is that possible..?
So far I have my Ubuntu partition,swap and another partition which lives in /media/username/E.
That location concerns me, since I think that it is strongly attached to my Ubuntu partition and in any case that Ubuntu breaks down I will lose my files..:(

---

### Post by yancek on 2014-09-22
Yes it is possible.  The reference you make to /media/username/E would lead me to believe this is a windows partition, is that the case?  Is this the partition you are referring to or do you want to create another.  Generally, you would create a mount point from which you would access the partition.  This is usually created under the /mnt directory but can be elsewhere.  You would then need an entry for the partition in the /etc/fstab file so that it would mount on boot.  If you want  to create another partition, you would need additional free space or would have to shrink another partiiton.

---

### Post by ajgreeny on 2014-09-22
It is very easy to setup at installation time, but a bit more complicated afterwards, though still very possible as long as you have sufficient space and the ability to edit any partitions if needed with gparted or similar. It is actually one commonly recommended way to share data files when using both Windows and Linux; ie by having a partition formatted to ntfs, which both OSs can read and write without problem.  Do you have both Windows and Ubuntu installed or just Ubuntu?

Let's see a screenshot of your current partition layout from a gparted window as that will allow us to make much more detailed recommendations of how to proceed.

---

### Post by grahammechanical on 2014-09-22
I have my data on a partition that I have called Data. I have several installations of Ubuntu and I can access my Data partition from any install of Ubuntu. And I often install Ubuntu. I make sure that during the installation I never allow my Data partition to be formatted. I only format the partition that Ubuntu is being installed into.

Right now File Manager tells me that my Data partition is mounted at /media/graham. What you are seeing is the mount point that the partition has. Everyone of my Ubuntu installs will mount that Data partition at /media/graham. Do not read more into it than it actually is.

Regards.

---

### Post by KalleHeiman on 2014-09-22
I've splitted my hard disk three partitions: One 50GB mounted / (root) and it have OS and applications, one little for Swap and about 440GB mounted /home.
When I needs to do new clean installation of Ubuntu it needs only format / partition. /home -partition keeps all my data and settings when I use same username and password than earlier.
You must select 'Other' installation method and select manually mountings to do this.

---

### Post by nerdtron on 2014-09-22
> **KalleHeiman said:**
> I've splitted my hard disk three partitions: One 50GB mounted / (root) and it have OS and applications, one little for Swap and about 440GB mounted /home.
When I needs to do new clean installation of Ubuntu it needs only format / partition. /home -partition keeps all my data and settings when I use same username and password than earlier.
You must select 'Other' installation method and select manually mountings to do this.

This is good but once you install a newer version, your old home partition will contain some settings and preferences from the old install. This can cause conflict when the new install tries to mount the home partition and finds old config files.

I think the better way to do it the same as how I usually do it in windows. Create a larger partition and assign it a new drive (drive D). In linux you can just create a partition that such as /data and mount the drive here. Now you can dump all you data here.

---

