---
title: "Receiving this when trying to change permissions: &quot;no valid sudoers sources found&quot;"
date: 2018-10-20
forum: General Help
---

### Post by Lloyd_Hayes on 2018-10-20
Running into permissions issues with external hard drives again. However, when I go to change permissions via chmod, I am now get the following:

sudo: [/etc/sudoers]("https://ubuntuforums.org/etc/sudoers") is world write writeable
sudo: no valid sudoers sources found, quitting
sudo: unable to initialize policy plugin

What does this mean?

I was changing permissions with 'chmod' on a portable hard drive formatted as a Windows NTFS drive. Evidently, I was successful, but I also got this message. And online explanations on the problem and it's fix, if a fix is needed, have gone over my head.

---

### Post by Impavidus on 2018-10-20
NTFS doesn't support UNIX-style permissions, so chmod isn't going to work on such a drive. On NTFS, permissions are faked using the mount options. The default should be sensible.

The permissions on /etc/sudoers should be 440 (read permission for owner and group, nothing else), the owner and group should be root:root. On your system /etc/sudoers is world writable, which means that every user on the system (including those that are not allowed to use sudo) can reconfigure sudo to allow them to do everything, which is of course a big security risk. sudo no longer works, but (assuming you still trust your system) you may be able to get a root shell by booting into recovery mode (don't forget to remount the filesystem in read-write mode) and fix it, or use a live disk for that.

However, I wonder what command you tried, leading to the breakage of sudo. If it was some recursive chmod, chances are your system is so messed up that you can better try a fresh install.

---

### Post by Lloyd_Hayes on 2018-10-22
2 issues.

1st. I am excluded from the mount folder. It is assign to root only. This is why I go in and change the permissions on it.
2nd. The system is excluding me from the 'ROOT' group.

3rd. Doing a fresh install on whim is not why I use any operating system. This is the main idea that I hate about the Linux community. I have files on my computers which are decades old.

On a netbook with a different version of Linux, the "/etc" dir, along with all of the main root directories, shares permissions. I didn't have that on this one. I changed the "/etc" to being open to everyone due to problems that I was having getting software to even work. 

I have the ultimate security since I am the only person who uses this computer. Something that I have complained about for years with nearly every operating system is that security away from the Internet is not needed when there are a restricted number of people using a computer, or in my case, just one person using the computer. And as for the Internet, Internet security can be enhanced by simply unplugging the Internet connection.

---

### Post by Lloyd_Hayes on 2018-10-22
On the idea of doing a fresh install, my computer is NOT connected to the Internet 24/7.

---

### Post by Lloyd_Hayes on 2018-10-22
Here was the originall command that got me the messages.
"lloyd@lloyd-desktop:/media/lloyd$ sudo chmod -R 777  [/media/lloyd/Seagate-006-001]("https://ubuntuforums.org/media/lloyd/Seagate-006-001sudo:")"

The full content was this:
lloyd@lloyd-desktop:/media/lloyd$ sudo chmod -R 777 [/media/lloyd/Seagate-006-001sudo:]("https://ubuntuforums.org/media/lloyd/Seagate-006-001sudo:")[/etc/sudoers]("https://ubuntuforums.org/etc/sudoers") is world writable
sudo: [/etc/sudoers]("https://ubuntuforums.org/etc/sudoers") is world write writeable
sudo: no valid sudoers sources found, quitting
sudo: unable to initialize policy plugin

I use external usb hard drives extensively. I have over 60 or 70 TB of files in external storage. This idea of USB devices being a security risk is a farce when you are the only person using that computer. So being blocked from USB devices is a major issue for me.

As **Linus Torvalds **said about a year or so ago to a small group of people, Linux is a great system if the Security People would stay out of it.

---

### Post by oldfred on 2018-10-22
If using NTFS for external partitions, the owner & permissions are set by the mount. And even though it may say root, it is read & writeable by everyone.
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)
       Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion. 
    But newer copies of Windows have added the "fast start up" complication. That leaves all NTFS partitions with the hibernation flag set. And Linux will not mount read/write to prevent damage. Or any forced write will disappear when Windows restores the hiberfile.

> 
I changed the "/etc" to being open to everyone due to problems that I was having getting software to even work. 
This destroyed your system. You may be able to change back to root:root but some are not root to have system fully work.

If you had issues with programs, better to have resolved those issues.

---

### Post by Lloyd_Hayes on 2018-10-23
After installing a couple of backup pieces of software, my permissions were suddenly all restricted to "ROOT" except for my "Home" Folder. Also, in terminal mode, it went from being "lloyd@lloyd" to "lloyd@lloyd-desktop" Access to connected USB drives was denied. In short, various pieces of software quit working properly. Understand that I use USB hard drives all of the time. They don't make a hard drive which can hold all of the files that I access all of the time. I have 2 internal hard drives, but one is another backup. Main drive is 4 TB, and internal backup is 6 TB. Then I have around 60 or 70 TB in external hard drives which are in regular use.

When I had problems in the past with various USB drives, it was simply a matter of changing the permissions on the "Media" folder to 777 which cured this issue. And this has happened several times in the past year after updates.

However, "Software Update" quit working, along with some other pieces of software, after the new backup software was installed. Changing the "/ETC" permissions allowed all of these software to start working again. But about a month after changing it, I am unable to use "sudo" anymore.

In looking at a small netbook running Lubuntu, I noticed that the permissions on all of the main root directories have shared permissions. While on my desktop running Studio, it showed "root" only permissions.

As for the owner "chown", that is unchanged. 
Only the permissions "chmod" to "/etc" were changed, which allowed "Software Update" to work again.

The 2 pieces of backup software that I had installed when this started were "Deja Dup" and "Timeshift".

---

### Post by oldfred on 2018-10-23
This would indicate you booted a different install:
       "lloyd@lloyd" to "lloyd@lloyd-desktop" 
    
I make sure I use a different name for each install, since I have multiple installs:
      fred@Bionic-Z170N:~$ 

It is never recommended to use 777 as permissions. That is then like NTFS, but lets a rogue process also execute.

I use this which sets my data partition(s) similar to /home settings:
      
 sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, [COLOR=#ff0000]do NOT[/COLOR] run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown -R $USER:$USER /mnt/data
[http://askubuntu.com/questions/324705/first-full-backup-on-usb-permission-denied/324942#324942](http://askubuntu.com/questions/324705/first-full-backup-on-usb-permission-denied/324942#324942)

If multiple installs and/or multiple drives often best to run the Summary Report. If nothing else to document configuration.
       BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by Impavidus on 2018-10-23
With that recursive chmod you indeed broke your system so much that a fresh install is the best way out. If you don't like fresh installs, don't break your system so badly. I never did. Small problems can most of the time be fixed. You should work with the system, not against it, even if you're the only human user on your computer. Else it won't take long before you break it again.

/etc should not be writable by everybody, not on Ubuntu, not on Lubunt, not on any other Linux.

---

### Post by The Cog on 2018-10-23
> **Lloyd_Hayes said:**
> I changed the "/etc" to being open to everyone due to problems that I was having getting software to even work.
Because of that, I suggest that you do a full install. And don't go changing system files permissions again next time: many people who do that end up with a system that simply won't boot at all.

If you have trouble running software next time, it would be better to ask than to mess with system file settings that way. While you are doing the install, consider making a separate partition for your /home folder, so that all the user settings and data files can be retained while the OS is re-installed. Actually, I like to keep two root partitions, about 20G each, and alternate betwen them when I install so that I have the old install to go back to if needed.

---

### Post by 1clue on 2018-10-23
The big question here is not whether the chmod broke something (it certainly would break everything, if it were on a filesystem with support for UNIX permissions) but rather whether simply installing on NTFS broke something. I think the system was effectively broken as soon as you installed on NTFS. It's possible that the system may have worked due to whatever the default mounting options were.

File and directory permissions are a huge part of UNIX security.

If you could locate an installed Ubuntu of exactly the same release, you could possibly move all your NTFS data onto another drive with a UNIX-compatible filesystem, then then write a script to recursively examine each file and folder to get the correct permissions, and set the permissions on the compromised system based on the other system.

Really though I recommend backing up your data and doing a reinstall. It will be easier.

---

### Post by Lloyd_Hayes on 2018-10-25
Issue fixed.

I don't like 2 partitions on the same drive. I have 2 drives installed in my desktop, with the 2nd being a backup drive. The 2nd drive is not mounted normally except when doing a backup.

As I mentioned above, I installed "Timeshift" about 3 weeks ago. It will automatically mount drives under "Root" only permissions when used. I had made a full system backup shortly after installing "Timeshift".

After figuring out the problem here, and hearing this re-install business, I made sure my data files were backed up to the 2nd drive also. I then did a 'Restore' using "Timeshift." This corrected the system to it's previous state 3 weeks ago. Altered and new data files had to be copied back to my system drive.

"Software Update" is working and I used it to do a new update for the system files again.

There were system files which failed to write back during the restore process due to permissions issues, but apparently they were not needed.

"Sudo" is working now, along with what appears to be the rest of my system.

So at this point, I consider the system to be fixed.

---

### Post by The Cog on 2018-10-25
Good news. Thanks for the update.
You get bonus points for having a good backup - many people don't.

However, I do think that having separate system and data partitions is worthwhile. It makes re-installing (and upgrading - I always install a new version rather than upgrading in-place) dead easy. It's rather like Windows using C: for the system and D: for data.

You can use the "Thread tools" pull-down (top right) to mark the thread solved.

---

### Post by 1clue on 2018-10-25
The really good news here is that now you know your backup strategy actually works.

Back in the 80s and 90s I spent a lot of my money and also a lot of my company's money getting backup devices and using them. Then one day I needed to restore and found out that my tape drives were "write only." At that point I checked all my backups, both personal and business, and realized they were ALL write-only.

I pay a lot more attention to backups and their restorability now....

---

### Post by 1clue on 2018-10-25
I'm not sure exactly what sort of backups you're doing, but something to keep in mind:

If you're doing a "live" backup (where your backup media could be used as a replacement for a failed drive) then it has to be the same filesystem type and format as the original. NTFS is a distinctly poor choice for Linux system files. There are lots of UNIX-specific choices out there.

If you're storing archives on a usually-disconnected drive, then it doesn't really matter what format the backup drive is, as long as it's big enough to hold the file and can handle files that large.

If your backup drive is always connected then it's not really a backup drive.

---

### Post by Lloyd_Hayes on 2018-10-29
I am pretty sure that I posted that my system is fixed a few days ago. But I don't see my post here.
I had installed the program "Timeshift" to backup my entire system to a 2nd internal drive. I was unaware of the issue of changing permissions on the system directories, since I have done so in the past without incident. But I guess it depends upon which folders they are.
Anyway, once I understood the problem, I ran Timeshift recovery to bring my system back to it's state as it was a month previously. (After backing up my new or changed date files.) After doing this, I had to update the system files again,  and copy my newest data files back to my main hard drive. But my system is fixed.

---

### Post by coffeecat on 2018-10-29
> **Lloyd_Hayes said:**
> I am pretty sure that I posted that my system is fixed a few days ago. But I don't see my post here.

Post #12 of this same thread perhaps - [https://ubuntuforums.org/showthread.php?t=2404134&p=13811309&viewfull=1#post13811309](https://ubuntuforums.org/showthread.php?t=2404134&p=13811309&viewfull=1#post13811309) - where you write: 

> **Lloyd_Hayes said:**
> Issue fixed.

<snip>

So at this point, I consider the system to be fixed.

?

---

