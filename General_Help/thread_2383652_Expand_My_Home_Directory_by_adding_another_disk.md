---
title: "Expand My Home Directory by adding another disk"
date: 2018-01-28
forum: General Help
---

### Post by microcode-roy on 2018-01-28
Hi,
       I have a dual boot machine, windows 10 and Ubuntu 16.04 LTS. Both are installed on a 250GB SSD shared 125 each for linux and windows
   I am using this machine for mainly embedded Linux development.I am installing yocto build system Poky and other similer systems and learning.
 As I move forward with more image build which are bulky by the way, my Home directory ( which is in 250GB SD) became full. I use Gparted and aquired as much as  possible from windows share.
But I think since I am in learning phase I cannot delete many previous builds as I am not sure.
So I purchased a 1TB normal harddiak and installed as two 500GB partitions and they are visiblle in windows and linux.
My problem is I need to expand my home directory to my 500Gb drive also. many tutorials or step by step instructions for my build systems will be based on home.
So since I am not that much sure about the consequences I am not sure if I use another location for that purpose.
So is it possible and if yes How I can make the 500Gb partition in the other drive as a part of my home folder?

Thanks

---

### Post by TheFu on 2018-01-28
Welcome to the forums.

If your HOME is a logical volume, then you can add to it using LVM from any connected disk. However, having LVs span across physical disks is dangerous, since a failure of either is likely to loose all data.  Backups are a must. Using LVM is an intermediate skill.

Or you can relocate your HOME to the new disk partition. This is a strong beginner skill. There are how-tos for doing this with step-by-step instructions. There are many forum posts about doing this here as well.

You didn't mention this, but storage in a HOME has to be Linux compatible, ext4 is probably best.  Cannot use NTFS.  Doing Linux development on NTFS is full of issues. 

There are a few other methods, but they are hacks.  One is using symbolic links for specific directories. It will work and it is quick, but _feels_ like a bad idea.  I use this on production systems until down time can be scheduled the following weekend.

And it should go without statement, but before you do any of these things, make a 100% know-you-can-restore backup.

---

### Post by microcode-roy on 2018-01-28
Thanks for the response. at present I have formatted the new drives as NTFS, but changing is not a problem, there is no data so far in it. So I can format it in ext4 easily, I think using G parted.
Regarding, Relocating the home to other disk , I have read articles. I think In that case I need to move the already existing home whole data also to new drive.
The symbolic link method I understood generally. But in that case,suppose I have formatted the new drive in ext4 and created a folder there , then I placed a simulink in home,  say 'poky' and if 'cd poky' and all other terminal commands in poky will behave exactly as in original home?, at least for the purpose of cross compiling  and deployment of images and sdks? 
Thanks

---

### Post by vanadium on 2018-01-28
The easiest scenario is leave you home in place, and expand storage under home by symlinking folders to the other disk. That disk *can* be in ntfs format, which is useful if you also want to be able to access the same drive from within MS Windows, which indeed is your use scenario.

Make sure your Windows system is fully shut down (disable the "fast start" feature so the ntfs partitions are properly closed when Windows is shut down) before accessing the ntfs partitions with Linux. File system checking of ntfs partitions should be done regularly from within Windows.

---

### Post by TheFu on 2018-01-28
> **vanadium said:**
> The easiest scenario is leave you home in place, and expand storage under home by symlinking folders to the other disk. That disk *can* be in ntfs format, which is useful if you also want to be able to access the same drive from within MS Windows, which indeed is your use scenario.

Make sure your Windows system is fully shut down (disable the "fast start" feature so the ntfs partitions are properly closed when Windows is shut down) before accessing the ntfs partitions with Linux. File system checking of ntfs partitions should be done regularly from within Windows.

If the OP is doing embedded Linux development, he needs file permissions and case sensitivity.  The tools demand that. There will be **constant problems** attempting to do that with NTFS.

The best way to make code work on both Unix and Windows is through a code repo to manage changes on both sides, without using the same storage.

Or using virtual machines.  There are many reasons for VMs when doing development.  They bring some amazing flexibility and the ability to backup entire build environments for later, as clients choose to stay on 2+ yr old OSes while the rest of the development moves forward.  VMs make supporting older systems possible for much longer, which leads to happier clients.  And it lets the developers keep moving forward with the latest stuff, as needed.

---

### Post by Morbius1 on 2018-01-28
> **vanadium said:**
> The easiest scenario is leave you home in place, and expand storage under home by symlinking folders to the other disk. 
That would be the way I would go. Or even mounting the new disk under a new folder within the existing home.
> That disk *can* be in ntfs format, which is useful if you also want to  be able to access the same drive from within MS Windows ... 
And I agree with that part of your statement.
> ... which indeed is  your use scenario.
That part is not clear. He mentions that these partitions are visible to both OS's which they would be if they were NTFS. Reformatting to ext4 removes that ability from Windows.

What is not apparent is if that is required for this  yocto development environment thingy. It appears to be installed in Linux and the "image builds" are taking up space in his home partition. Windows has no access to those image builds now so I don't think it's required that they do.

---

### Post by oldfred on 2018-01-28
If you want to move home.
 To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving) 

If you want to use symlinks, which is what I do.
TheFu is a systems person and very knowledgeable on servers and systems. 
But I am just a home user. And linking works well for me.
But for development I thought you wanted a separate server and versioning software like git or subversion.

      
 The actual user settings are small. My /home is 2GB with most of that as .wine' Because /home is small I now keep it as part of / (root) which is a total of 11GB with /home in my typical 25GB / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives. 
   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /mnt/data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /mnt/data and just configure / for install. 
   [http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by microcode-roy on 2018-01-28
> If the OP is doing embedded Linux development, he needs file  permissions  and case sensitivity.  The tools demand that. There will be  **constant problems** attempting to do that with NTFS. 
This is important. I have to be in home, otherwise some scripts 'complain'.
I think I will give a try by formatting one 500gb partition in ext4 and  using simulink.But in some cases I need to create the folders and  simulink before the script runs.
That 'fast boot' was sometimes nagging me by ubuntu  saying 'windows drive not closed'. Now I understood the cause.
I can format one 500Gb partition in ext4 and make it part of home. These parts I dont need to access from windows.
But the other 500Gb I think I can keep in ntfs which I can use to share any files between ubuntu and windiows in case I need
Thanks for the links, I will go through them and check again my options
Thanks for all the inputs.

---

