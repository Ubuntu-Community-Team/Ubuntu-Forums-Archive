---
title: "My Sloppy Ubuntu Edgy Ways"
date: 2007-03-30
forum: General Help
---

### Post by Unoone on 2007-03-30
Help me change my sloppy Ubuntu ways.

I have been using Ubuntu since Hoary. My methods of using Ubuntu seemed to serve me well thus far until Edgy came along. I don't know maybe my usage habits are not compatible with Edgy. I hope that my sloppy ways won't hinder my fun with Feisty.

I always started out by installing Ubuntu from the text interface in the past up until Dapper. Maybe things got really messy when I began to use the Gui based live3d Gnome installer. 

In any case, I use the Ubuntu installer on my PC's to set up a basic Ubuntu Edgy install.  I use one Ext3/root partition, a Ext2/boot and a Swap partition for each PC. I know that "they" say you should use a /home partition for Linux systems. I don't. See, I'm sloppy. :) 

Then I go on a setup my fat32 drive if I dual boot with Windows on one PC. All that's left is my sloppy ways of using a fine Ubuntu install. I may even use some crazy names for folders. I'm silly like that. I can go on like this for weeks without a care in the world. Somebody stop me!:) 

All of a sudden reality set's in. I attempt to do something like, burn off some data from my crazy named and questionably organized content. Or I try to copy one folder or another over to my fat32 drive. Remember my content is crazy. One of my directories looks like home/user/_whatthe_/what_what/ that's what. The folder in question is filled with other nonsense like /that's what/eggs_123456789900_sunnysideup/welldone. As my folder /that's what/eggs_123456789900_sunnysideup/welldone copies over to my fat32 drive I get an error. The error is "Error "Invalid parameters" while copying...". I'm like arghhh! What's up with this? I'm just copying a sloppy file to a fat32 drive. I check out the folder and see that "root" now owns that folder. Imagine that, the sneaky thieving "root" stole my sloppy folder. Maybe "root" doesn't like something about my sloppy folder. I can't reown the folder, "root" won't give it up. If I want to move the folder around inside my /home directory "root" lets me do that. I just can move it to my fat32 drive. Neither can I successfully burn any of these "root" owned folders and read them on a data DVD outside of my Ubuntu system.

I figure that I have to change my sloppy ways in order to keep using Ubuntu. Sloppiness always served me in the past. I got away with anything since Hoary. Now Ubuntu Edgy won't stand for it. The problem is that I like being sloppy. I recently started to use Dreamlinux and Kanotix. These Distros don't care about my sloppy ways. They even encourage me to be as sloppy as I wanna be. I can do anything I want to and get away with it in these Distros. Windows let's me wade neck deep in some of the sloppiest stuff you've ever seen.

If anyone of you "proper" orderly  Ubuntu users has tips for a fellow sloppy Ubuntu user please share. I need to learn to live under the refined rule of the "root" controlled system in Ubuntu Edgy and beyond. Thanks.

Long live "root".

---

### Post by phidia on 2007-03-30
Sometimes in copying files from one system to another (even within linux) the permissions get borked.

You can do > sudo chown (your username) /sloppy\ ham&eggs /folder
That should give you permission on the files to do whatever-you can select/change permissions on the file once you own it.

As to procedure or methods I don't think there is any one "right " way. 
You can install from the alternate cd iso if you don't care for the gui install. Sometimes, I think, the alternate (text based) installer does a better job and offers options not found on the livecd.

---

### Post by Smuve on 2007-03-30
Yea, I hear ya.  Root doesn't like to share.  I have a separate shared data drive (FAT32) and sometimes it has a data folder that sometimes gets some .debs.  I really don't know when it happened, or if it was like that all along, but I tried to execute a .deb and it wouldn't let me.  Root owned the drive and left me with rw permissions only.

My solution:  Right now I'm up to my eyeballs in converting that drive to ext3.  Then I can do whatever I want again.

---

### Post by Smuve on 2007-03-30
... and don't forget chown **-R** from phidia's suggestion above.

---

### Post by dannyboy79 on 2007-03-30
when you say you can't change the owner, do you mean that when you right mouse click on it thru nautilus or konqueror? or do you mean when you try to chown it? becuase sudo chown will change the owner of any directory or file!! also, sudo chmod will change the permission of any file or directory. so could you be a little more specific.

---

### Post by Adramelech on 2007-03-30
Error "Invalid parameters" i think that is cause by '-' characters on your files names, try making -- the last option. eg

cp -R -- source dest 

I remember '--' used as an end of option marker.

about the FAT thing, fat dont have permissions on files, so probably everything you get there get owned by root.

---

### Post by Unoone on 2007-03-30
Thanks for your replies  people. Yeah &#8220;root&#8221; keeps showing it's ugly spuds now in Edgy more than ever. Most of the time I wish that &#8220;root&#8221; would just stay deep down under foot until I needed it. Maybe the Ubuntu developers activated more security features that increased "root's" activity in areas that were overlooked in the past. It's seems that since Edgy "root" is set at some paranoid level of security. As I said before I could be as sloppy as I needed to be in the past Ubuntu versions. And I have yet to change my ways for other Linux Distros or Windows.

But for my web work I'm ever so clean, /website/neat_and_clean/for_every_folder/. However I can't speak for other users character naming habits.:)

---

### Post by Unoone on 2007-03-30
> **phidia said:**
> 

You can do ""
That should give you permission on the files to do whatever-you can select/change permissions on the file once you own it.



I can't chown -R user:user /anything. I think this is now due to the spaces between the characters in my folders names.  My questionably named folder contents contain so many files that manually editing all of the folder names is impossible. :(

---

### Post by Unoone on 2007-03-30
> **Smuve said:**
> 
My solution:  Right now I'm up to my eyeballs in converting that drive to ext3.  Then I can do whatever I want again.

It seems that "root" digs Ext3 partitions. In this case "root" still lassos any folder that it wants and won't let me share it with fat32 drives.

I just did a an ls -l on my directory and found that all of the folders in that directory looked like they are owned by my user profile.

I dragged the first 15 or so folders over from my Ext3 to a fat32 drive with no errors. When I got to the 16th folder, "Error "Invalid parameters" while copying "/media/hda/folder/silly:equals root lock.html."  Linux "root" don't like them colon punctuations in file names.  Windows don't like them colons none neither ya hear? Windows automatically filters them out as you type with a loud "beep" and some childish visual warning. Maybe Linux "root" should have auto character filters like Windows or something?

But scratch your head over this one. Some of the folders that do the "Error "Invalid parameters" while copying" mess had no illegal characters. In fact manually changing the folder name did nothing. I had to make a new folder and rename to the same name as to error folder. I changed /sloppy joe  to /sloppy_joe, still got and error. Then I added a new folder named /sloppy joe2 and dragged all of the contents over from /sloppy joe into the new folder. I could now copy /sloppy joe2 over to my fat32 drive without the error. 

Is Linux now getting way to proper for my Windows trailer park/ghetto ways?  Shoot, I love dumping a jumbo cup of frosty freeze into an expensive crystal bowl, adding two twinkies, a bag of M&M's and squirting a bottle of dollar store microwavable hot fudge all over the top.:)

---

### Post by dannyboy79 on 2007-03-30
NOT true, you can use a global rename script. At least to erase the spaces. Also, if you use tab completion there is no problem with chowning anything. I just did it on my own computer. I have a 250gb external usb drive attached as we speak and yes, each file has permissions and they are owned by myself as well as the group is myself. I also would like to point out that Ubuntu has used sudo from the start (i thought anyway). are you trying to do this from nautilus? try gksudo nautilus, then try to move stuff around. this may be easier. also, once you open nautilus with root privalages, you would be able to also change the owner as well as the permission I believe. I am leaving 1 location and going to another right now so I can maybe help you with the rename script later, I have already helped another person with this. bye

---

### Post by Unoone on 2007-03-30
> **dannyboy79 said:**
> NOT true, you can use a global rename script. At least to erase the spaces. Also, if you use tab completion there is no problem with chowning anything. I just did it on my own computer. I have a 250gb external usb drive attached as we speak and yes, each file has permissions and they are owned by myself as well as the group is myself. I also would like to point out that Ubuntu has used sudo from the start (i thought anyway). are you trying to do this from nautilus? try gksudo nautilus, then try to move stuff around. this may be easier. also, once you open nautilus with root privalages, you would be able to also change the owner as well as the permission I believe. I am leaving 1 location and going to another right now so I can maybe help you with the rename script later, I have already helped another person with this. bye

Thanks for the tip. I found this link-

[http://www.linux.com/guides/abs-guide/contributed-scripts.shtml]("http://www.linux.com/guides/abs-guide/contributed-scripts.shtml")

I'll try the rename scripts out.  Using gksudo nautilus doesn't help in these cases as the problem is character related as far a permissions are concerned. I think.:)

---

### Post by Unoone on 2007-03-30
You would think that the Ubuntu developers would know or sense that we sloppy Windows born users are here. We are drawn to the clean fast Ubuntu Linux features. Do we want to dot every -i- and cross every -t-?  Nooooooooo. So why not just add these common shell scripts to the panel in the admin settings for us to just dump on directories and auto-fix our sloppiness?:) 

I'm all for seeing Ubuntu Linux operate as carefree as possible.

---

### Post by dannyboy79 on 2007-03-30
what command are you using to mount your fat32 partition? are you just plugging it in and it automounts? you can see what pmount is using by typing in mount at the command line to see what options it's using. if that's the case than you may need to unmount it and remount it using these options for good reasons! I have pasted some info from a website I found. I actually have a very similar fstab for my fat32 partitions but mine is 
/dev/hdb1       /home/daniel/fat32      vfat    rw,uid=1000,gid=1000,iocharset=utf8,umask=0000  0       0

if you have other users that you would like to be able to mount it and unmount it than add the "users" option. Also, this is for static mount, this drive is installed in the compouter. if you want to setup a removable drive with certain mount options than you should look into dev rules. if you create a fstab entry for say sda1 than how do you know that the same device will be /dev/sda1 and not /dev/sdb1? you can set this up with udev rules. 

**I have pasted this from another website:** (udev-basic)
You'd have to add your own udev rule. Here's what I did for my Sansa e260:

1. Create a file under /etc/udev/rules.d, name it 60-sansa.rules for example
2. Add the following content:
Code:

# My own rules for camera, sansa player etc.
SUBSYSTEM!="usb_device", ACTION!="add", GOTO="sansa_rules_end"

# SanDisk Sansa e260
ATTRS{idVendor}=="0781", ATTRS{idProduct}=="7420", SYMLINK+="sansa_e260", MODE="666", GROUP="audio"

LABEL="sansa_rules_end"

3. Reboot (I didn't find a reliable way to restart udev)

You will have to replace ATTRS{idProduct}=="7420" with your own product ID which you can find by either running udevmonitor or using some GUI like usbview or KInfoCenter in KDE.

If you can't really follow this or it's not enough info for you, check this out ([http://gentoo-wiki.com/HOWTO_D-BUS,_HAL,_KDE_media:/](http://gentoo-wiki.com/HOWTO_D-BUS,_HAL,_KDE_media:/)) it's for  D-BUS, HAL, KDE but using Gnome or XFCE shouldn't matter as they both use D-bus and Hal I believe!

**FROM ANOTHER WEBSITE:**
If you have a dual boot Linux/Windows machine you may want to have a central place to store your valuable personal files. Until Windows learns to read ext2, and Linux to write NTFS, the safest way remains slicing a FAT32 partition which you can read and write from both OSs.

So mounting a FAT32 partition should be simple, right? Edit /etc/fstab, put there vfat as partition type and mount. It does work, but often you need more than that. Merely mounting a vfat with defaults options makes all files executable, owned by root, all-lowercase files.

Enough to not let you work on a real project. So here it is, my hacked magic line to do it:

 /dev/hda6 /mnt/g vfat  auto,users,uid=username,gid=users,umask=0022,fmask=0133,check=s,shortname=winnt 0 0 

-  uid=username is my username
-  umask=0022, all directories will be rwxr-xr-x
-  fmask=0133, all normal files will be rw-------
-  check=strict, can&#8217;t hurt :)
-  shortname=winnt: if you create a file in uppercase, it will show that way!

---

### Post by Unoone on 2007-03-30
Much thanks dannyboy79! I will apply your fstab edit tips to my fat32 mounts. :) 

The "blank-rename.sh" works fine from the link in my earlier post. It replaces all of the blank spaces in my directories from /sloppy joe to /sloppy_joe. Cool!:) 
Although it killed my html data folder links in the directory.:(

I have to remember not to use this script on directories with html folders. Maybe a shell script that removes all illegal Linux characters from my directories folder names is all that I need.

Now I need a shell script that automatically removes all of the illegal Linux characters like colons :, etc from my directory folder names. I have a book on Linux shell scripting somewhere but I'm too busy right now building stuff with Linux to sit down and master the shell script language.:( 

Can someone help me out here? Maybe other sloppy Ubuntu users will benefit also.:)

---

### Post by Unoone on 2007-03-31
I remember reading this info-

[https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows?action=show&redirect=SwitchingFromWindows]("https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows?action=show&redirect=SwitchingFromWindows")


For most generic use situations this info in fine. But many of us Windows converts  share files with others and download data from websites. Th-s data doesn't always comply with Linux. When this happens you run into problems like what I have been experiencing since Edgy. It's seems that Ubuntu is more strict as to how it handles illegal filename characters now. I never even thought about this in my past usage of Ubuntu as it was never an issue for me. 

To deal with this current situation I have been searching for file linux management utilities. Hopefully these will allow me to sweep my directories and automatically weed out and fix any illegal character names from my files.

I installed GwenRename, KFileReplace, KRename and file-rename-utils from a Source Forge project. The only thing that did anything useful for me so far has been a shell script which remove spaces from file names. I have not been able to successfully remove all vfat illegal characters from my filenames with file-rename-utils. I haven't figured out how to operate the stuff.:) 

Has any Ubuntu/Windows user reading this thread ever hassled with this situation?

---

### Post by dannyboy79 on 2007-04-02
ok, well first how many different situations are we talking about? I mean do you just have a bunch of files named with a ! or a bunch with say :    or what is the real scope of this. If you know what character the majority of the files are I can help you write a little script to find them and direct the results into a file. then we can use that file as in input for renaming them. is this a fat32 partition or ntfs partition that's giving you hell. or are you trying to copy these files from fat32 or ntfs to ext3 and you can't because ext3 doesn't like them? just trying to clarify whats occuring here. I did find this in the man mount.

iocharset=name 
Character set to use when returning file names. Unlike VFAT, NTFS suppresses names that contain unconvertible characters. 
utf8 
Use UTF-8 for converting file names. 
uni_xlate=[0|1|2] 
For 0 (or `no' or `false'), do not use escape sequences for unknown Unicode characters. For 1 (or `yes' or `true') or 2, use vfat-style 4-byte escape sequences starting with ":". Here 2 give a little-endian encoding and 1 a byteswapped bigendian encoding. 

so I am thinking that maybe you could add another option to your mount command for the ntfs partition and it should mount them or is that not the issue? just clarify what you're trying again and I'll see what I can do.

did you check out this program?

[http://en.wikipedia.org/wiki/GPRename](http://en.wikipedia.org/wiki/GPRename)

---

