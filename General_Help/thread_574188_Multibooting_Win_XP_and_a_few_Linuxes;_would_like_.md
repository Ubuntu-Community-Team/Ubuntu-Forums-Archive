---
title: "Multibooting Win XP and a few Linuxes; would like to share FF, TBird, Picasa for all."
date: 2007-10-12
forum: General Help
---

### Post by brjoon1021 on 2007-10-12
Hi,

I want to make my life easier and have Firefox, Thunderbird, and Picasa (a google picture editing and organizing application) be shared between all of the OS's: Win XP, Ubuntu, PCLOS, Linux Mint, maybe another Linux.

This article peeked my interest: [http://www.thinkdigit.com/index.php?action=article&prodid=1118](http://www.thinkdigit.com/index.php?action=article&prodid=1118)
-It is about sharing FF and TBird between Windows and Linux.

I have some questions about the mechanics of doing this.

1. I assume that I install the respective versions of FF, TBird and Picasa in each OS.

2. FAT32 seems to be the most OS friendly filesystem. So, I believe that the data for each of these applications must be put in a separate FAT32 partition as the article above describes.

3. Are there any tips, tricks or caveats that you would have concerning doing this ?

4. Do you think that Google Picasa could be shared the same way ? I already have a large FAT32 storage partition where I save all pictures, files, music, videos etc... so that Windows and Linuxes can access them.

I am not too experienced with Linux. This is probably the most difficult thing that I have tried to do, so any tips or warnings would be appreciated. I am especially wondering if anything will go awry when windows or one of the Linuxes updates its FF, Tbird or Picase to a new version. Will that hose anything up ?

Thanks,
B.

---

### Post by Brucevdk on 2007-10-12
Actually back when I used to dual boot I actually used another method to share my Firefox/Thunderbird/Gaim profiles (I personally 
prefer this over creating a separate FAT32 partition) which should basically work for any program.

*NOTE: a little warning up front. Even though it worked fine in my case, I can't guarantee it will for you. As you'll read below, the process, among other things, still involves installing a file system driver for Windows.*

Basically this method involves creating symbolic links (actually junction points) from the NTFS partition to the ext3 partition that Ubuntu uses (yes this is actually possible).

You'll need to install [ext2ifs]("http://www.fs-driver.org/") (a freeware file system driver for accessing ext2/ext3 partitions from Windows) and [NTFS Link]("http://sourceforge.net/project/showfiles.php?group_id=161885&package_id=182554") (exposes junction point functionality through a set of shell extensions).  After rebooting all you have to do is copy the folders to your ext3 drive and create a junction point to it.

So basically the end result will be:
```

Documents and Settings
- Application Data
-- Mozilla
--- Firefox -> ${ubuntu}/home/${user}/.mozilla/firefox
--- Thunderbird ->${ubuntu}/home/${user}/.thunderbird
--- etc.

```

So even if you can't manually modify the profile path (because it's hardcoded in the program or whatever), it doesn't matter because the program is "fooled" to think it is writing to C:\Documents and Settings\Application Data\${program}.

Even if a certain program had platform specific configuration files you would only have to duplicate those and could create individual symbolic links to those they have in common. Though I have to admit I've forgotten whether or not it's possible to link to individual files.

*NOTE: explorer will crash when you try to rename junction points starting with a dot (used to indicate hidden files under *nix), use the move command in a command prompt to rename the profile directories.*

**To answer your questions**
The above instructions should answer 3 and 4. To answer your question whether upgrading the individual software packages will cause any problems, in the case of Thunderbird and Firefox I can say it will generally not as long as the versions don't differ too much. Say you were using the latest release of Firefox under Ubuntu (2.0.0.6) and a previous one under Windows (2.0.0.5) all that would happen is that Firefox when starting up would verify if the extensions still worked.

---

### Post by brjoon1021 on 2007-10-12
thanks for your help

---

