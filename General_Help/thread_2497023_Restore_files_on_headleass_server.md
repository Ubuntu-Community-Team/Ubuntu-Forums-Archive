---
title: "Restore files on headleass server"
date: 2024-04-20
forum: General Help
---

### Post by OiPenguin on 2024-04-20
Hi! While attempting to set up backup with rsync, I've managed to delete our entire archive of home videoes (kids now 17 and 19)... I've got an Ubuntu server (headless, 22.04.4 LTS) set up with raid so surely the files should be there and possible to restore, however how do I do it? Please, can someone give me some valuable pointers.

Yours sincerely,

Lars

---

### Post by dragonfly41 on 2024-04-20
Oh dear, this is the second rsync disaster I have read in days ..

[https://ubuntuforums.org/showthread.php?t=2496829](https://ubuntuforums.org/showthread.php?t=2496829)

Because the data is so important my advice is wait for a cluster of others to respond. 
Don't act on one opinion.

To park in your memory (a) always have backups and (b) know how to use "dry run" in rsync.
The limited advice I have read is to take a copy of your raid setup then try recovery on the copy.
Yes that means more outlay but that is the cost.
Apart from that my thoughts are possibly testdisk but .. wait .. for incoming expert tips.

P.S.(1) there are specialist data recovery forensic expert services to try as last resort but they are costly.

P.S.(2) Further advice here. [https://www.reddit.com/r/linux/comments/ew7ni/i_****ed_up_an_rsync_delete_what_are_my_chances/](https://www.reddit.com/r/linux/comments/ew7ni/i_****ed_up_an_rsync_delete_what_are_my_chances/)

P.S.(3) And do not use your computer too much in the interim since the deleted space might be overwritten.
Use another PC to watch for forum replies here. Or use a LiveUSB.

---

### Post by aljames2 on 2024-04-20
+1

Giving this a bump, and while you wait, adding some additional reading on the topic of raid types and the objective when using them. Raid can be useful to provide redundancy in case a drive fails, it can give you time to replace a failed drive, and therefore keep your storage array alive. It is not a backup technology. It sounds like you were starting to realize you needed a backup plan. Rsync is a good choice and as Dragonfly has pointed out, there are safe ways of using it. Do you by chance have any other copies of these videos/data anywhere else in the world?  Can they be ripped off the original DVDs, USBs, Micro SSDs, Cloud, Tape, wherever?

[https://en.wikipedia.org/wiki/Standard_RAID_levels](https://en.wikipedia.org/wiki/Standard_RAID_levels)

---

### Post by dragonfly41 on 2024-04-20
Another reflection.
Do not attempt to install any recovery software on the same drive where data was deleted in error. You run the grave risk of overwriting the data you are hoping to recover. Hibernate your RAID and do the recovery in a separate PC or LiveUSB. And better plan is apply the recovery on a *clone* of the RAID. You will need a separate drive into which (hopefully) you write any recovered data. On one occassion I was  attempting recovery using TestDisk and PhotoRec and realised that I needed a *separate* bucket into which I saved recovered files. In LiveUSB experiment with GUI tools such as Grsync and LuckyBackup (both with dry run buttons). You might have to create (on another PC) a persistent LiveUSB using MkUSB (or Rufus in Windows) but on a large external drive (SSD) rather than the usual low cost tiny flash drive. This will give you space for saving any recovered files into persistent LiveUSB. With a clone of your RAID it will be safer to experiment. You can probably clone your RAID in a specialist cloning shop.  For example I use StarTech devices where you can clone devices. And also StarTech dual docking bay. Ask StarTech where is there a local shop for cloning.

[https://www.startech.com/en-gb/faq/raid-modes-explanation](https://www.startech.com/en-gb/faq/raid-modes-explanation)
[https://www.startech.com/en-gb/hdd/unidupdock](https://www.startech.com/en-gb/hdd/unidupdock)

P.S. Sorry, just noticed that UNIDUPDOCK is discontinued but some shop might still use it.

I use this:
[https://www.startech.com/en-gb/hdd/sdock2u313r](https://www.startech.com/en-gb/hdd/sdock2u313r) (plus ICY DOCK caddy MB882SP-1S-1B from FARNELL)

Worst case if this fails you will have space for future formal backups (perhaps two or three in separate physical locations). As pointed out by others (such as @TheFu) SSD's can fail. So think  n+1 redundancy in the future.

==================================

P.S. I have no knowledge of this recovery service but I offer this shop *as an example *(in the U.K).

[https://www.datarecoveryspecialists.co.uk/services/raid-recovery?gad_source=1&gclid=CjwKCAjwz42xBhB9EiwA48pT72wDCck5Eozfxkm_lDDtJRGI1QI8ArBhUY3WgwLWBgwpAIxXzV-PwBoCaXIQAvD_BwE](https://www.datarecoveryspecialists.co.uk/services/raid-recovery?gad_source=1&gclid=CjwKCAjwz42xBhB9EiwA48pT72wDCck5Eozfxkm_lDDtJRGI1QI8ArBhUY3WgwLWBgwpAIxXzV-PwBoCaXIQAvD_BwE)

Now I suggest there must be a similar service in OP's country. Just check their client base for references.

Quote from their site:

"[COLOR=#666666][FONT=arial]We provide an online diagnostic report of the recoverable data, allowing you to make an informed decision before purchasing an actual recovery."[/FONT][/COLOR]

---

### Post by OiPenguin on 2024-04-21
Thanks to both of you for your replies. I'll add some extra information:

- I'm aware of the dry-run option, and should of course have used it, but didn't. Also, if I did, I believe the faulty destination (see below) would have been untouched and I would probably have made this mistake anyway.

- I understand that I, for the future, will need to install a GUI on my server. I've not got the skills to safely rely on ssh + cli. Once this is solved, I'll install a desktop environment, log in with remote desktop and use the default backup (Deja Dup?).

- I'll elaborate slightly on the error I've done. I've used a script based on this "recipe", but believe I've mixed around source and destination, hence deleting most of what I was supposed to backup.
#!/bin/bash

# Source and destination directories
dest="/backup/destination"
src="/home/your_username"

# Run rsync command
rsync -av --delete "${src}" "${dest}"
(source: [https://www.slingacademy.com/article/ubuntu-how-to-write-an-rsync-backup-script/](https://www.slingacademy.com/article/ubuntu-how-to-write-an-rsync-backup-script/) )

- I'm not sure which type of Raid I'm using and don't know how to find out. Anyway, as I understand from other threads, Raid protects against disk failure, not errors like I've made. The files (or the reference to the files) will be deleted on all partitions almost instantly.

- I have now shut down my server to avoid any changes to my server before I have a solution.

- I appreciate the suggestions of data recovery shops and have sent a request to a local shop (since I'm in Norway, not UK).

- I may have some sort of backups, however the purpose of this rsync-attempt was to establish a proper routine for backups to disks which I could store outside the house. I do have two options: 1) An old NAS, which if I'm able to make it run, will probably have approx 80-90% of what was lost. I believe the disks are encrypted so if the NAS won't run the files will probably be hard to retrieve from the disks. 2) An old ubuntu server, made with spare parts, which won't start. If the non-start is due to disk failure, the files will be lost, however if its due to failure of some other components, the files should be retrievable from the disks, since they are not encrypted.

- Hence, my preferred solution is to recover files from my main server. I've read up a bit about Testdisk. I'm acutely aware of not installing Testdisk on the server, but on an external machine (i.e. the laptop I'm using now). However, if I use this machine and connect a proper SSD, how do I access the raid disks on my server from this machine. Through Nautilus/Networks?

---

### Post by OiPenguin on 2024-04-21
An update:

- I've been able to connect my old NAS to the network. I'm able to view the content, which is all 2013 and older. However, when attempting to access one of the sub folders I get the error: "failed to mount windows share software caused connection abort" 

- I've pulled out the disks from the non-working server (not the one where I made the rsync-mistake. It has three disks and I've connected them to my laptop with an Akasa external hard drive enclosure.

#1
Seagate Barracuda 160 Gbytes 7200.9
OS
Able to mount

#2
Samsung HD103UJ (1000GB/7200 rpm/32M)
1,0 TB (1&#8239;000&#8239;204&#8239;886&#8239;016 bytes)
Linux RAID Member (version 1.2)
/dev/sda
721ed0ef-f114-562d-1840-2e736637764c
Unable to mount

#3
Samsung HD103UJ (1000GB/7200 rpm/32M)
no info
Shown in Disks as JMicron USB to ATA/ATAPI Bridge (0100)
Won&#8217;t show in Gparted
Unable to mount

The essential challenge is mounting the disks. I assume the reason it will not mount is that I've set up Raid. However, since Raid 1 is exact mirroring of two disks (according to Wikipedia), shouldn't it be possible the disks individually? On the positive side, I have established that the disks are working, however not in the current old server, so I have to find a way to mount one or both disk to be able to retrieve the contents.

---

### Post by dragonfly41 on 2024-04-21
I am not a RAID user. I prefer to managed separate drives in caddies in StarTech dual docking bay.

Since it is important you follow the correct path, I consulted an AI assistant (phind.com) and posed this query:,

> A user by error using rsync deleted important files from a RAID drive in Ubuntu server. What advice can be given to attempt to recover deleted files from array? The user has a separate laptop to attempt recovery using tools such as testdisk. But how to recover from a RAID? What tools are recommended from Ubuntu repo? Scalpel?

I threw in Scalpel as an afterthought since there is a Ubuntu forum somewhere discussing forensic recovery tools.

I suggest that you start by trying Phind in your laptop browser with that query. It brings up some advice to follow (some covered earlier in this discussion). More ideas the better. Subscription is modest although you can try free.

Intuitively I still feel that you should explore investing in StarTech RAID bay.

I have evolved my own "off piste" methods of holding assets in containers in of all things a CherryTree notes editor. Might seem odd thinking but I can "wrap" assets in individual CherryTree *.ctd files including context notes.  I search for them using Recoll indexing engine using query ext:ctd. Hover over recoll query field to see cheat sheet.They are self contained containers of images, notes, code.  You can also use Recoll to search for text *within* the containers. Perhaps describing a family event.

But that is for future thinking after this incident. Priority is to find experts to try to revover. But note that you will be charged even if they fail to recover your lost files. Better for the future learn both home grown methods and external recovery specialists (with strong client base).


P.S. As you have researched, RAID protects from device failure, not human failure. Studying causes of failure is a hobby of mine. What can screw up?

Now here is an old thread. A very old thread.

[https://forums.tomshardware.com/threads/recovering-raid-0-data-by-placing-in-external-drive-cases.654268/](https://forums.tomshardware.com/threads/recovering-raid-0-data-by-placing-in-external-drive-cases.654268/)

---

### Post by dragonfly41 on 2024-04-21
Submitting this follow up query to Phind.com ..

> In breaking up an old NAS with three drives this error is shown. "failed to mount windows share software caused connection abort". Explain how to access such NAS drives from Ubuntu.

yields advice ..

>  .... install samba ... 

> Expanded version from session. Although some instructions do not copy and paste easily to ths forum and you should run your own Phind queries.

[COLOR=#1B1642][FONT=&amp]To access NAS drives from Ubuntu, especially after encountering the error "Failed to mount Windows share: Software caused connection abort," you can follow these steps based on the information provided in the sources:[/FONT][/COLOR][COLOR=#1B1642][FONT=&amp]
[LIST]
[*]Install Samba: If not already installed, you need to install Samba, which provides file and print services for various Microsoft Windows clients and can integrate with a Windows Server domain.
[/LIST]
[/FONT][/COLOR]
[COLOR=#1B1642][FONT=&amp][COLOR=#F8F8F2][FONT=Consolas][B][COLOR=#F1FA8C]sudo[/COLOR] [COLOR=#F1FA8C]apt[/COLOR] update
[COLOR=#F1FA8C]sudo[/COLOR] [COLOR=#F1FA8C]apt[/COLOR] [COLOR=#F1FA8C]install[/COLOR] samba[/B]
[/FONT][/COLOR]


[/FONT][/COLOR]
[COLOR=#1B1642][FONT=&amp]
[LIST]
[*]Configure Samba: The error you're encountering might be due to SMB1 being disabled by default in Samba 4.11, which is used in Ubuntu 20.04. You can enable SMB1 or specify a different protocol version in the Samba configuration file.
[/LIST]
[/FONT][/COLOR]
[COLOR=#1B1642][FONT=&amp]
[LIST]
[*]Enable SMB1: If your NAS requires SMB1, you can enable it by editing the Samba configuration file. However, be aware that SMB1 is considered insecure and its use is generally discouraged.
[/LIST]
[/FONT][/COLOR]
[COLOR=#1B1642][FONT=&amp][COLOR=#F8F8F2][FONT=Consolas][COLOR=#F1FA8C]sudo[/COLOR] [COLOR=#F1FA8C]nano[/COLOR] /etc/samba/smb.conf
[/FONT][/COLOR]


[/FONT][/COLOR]
[COLOR=#1B1642][FONT=&amp]Add or modify the following lines:
[/FONT][/COLOR]
[COLOR=#1B1642][FONT=&amp][COLOR=#F8F8F2][FONT=Consolas]client min protocol = CORE
[/FONT][/COLOR]


[/FONT][/COLOR]
[COLOR=#1B1642][FONT=&amp]Save and exit the file.
[/FONT][/COLOR]
[COLOR=#1B1642][FONT=&amp]
[LIST]
[*]Specify SMB3: For a more secure connection, specify SMB3 as the minimum and maximum protocol version.
[/LIST]
[/FONT][/COLOR]
[COLOR=#1B1642][FONT=&amp][COLOR=#F8F8F2][FONT=Consolas][COLOR=#F1FA8C]sudo[/COLOR] [COLOR=#F1FA8C]nano[/COLOR] /etc/samba/smb.conf
[/FONT][/COLOR]


[/FONT][/COLOR]
[COLOR=#1B1642][FONT=&amp]Add or modify the following lines:
[/FONT][/COLOR]
[COLOR=#1B1642][FONT=&amp][COLOR=#F8F8F2][FONT=Consolas]client min protocol = SMB3
client max protocol = SMB3
[/FONT][/COLOR]


[/FONT][/COLOR]
[COLOR=#1B1642][FONT=&amp]Save and exit the file.
[/FONT][/COLOR]
[COLOR=#1B1642][FONT=&amp]
[LIST]
[*]Restart Samba: After making changes to the Samba configuration file, restart the Samba service to apply the changes.
[/LIST]
[/FONT][/COLOR]
[COLOR=#1B1642][FONT=&amp][COLOR=#F8F8F2][FONT=Consolas][COLOR=#F1FA8C]sudo[/COLOR] systemctl restart smbd
[/FONT][/COLOR]


[/FONT][/COLOR]
[COLOR=#1B1642][FONT=&amp]
[LIST]
[*]Access the NAS Share: Try accessing the NAS share again. If you're using Nautilus (the default file manager in Ubuntu), you can do this by navigating to "Other Locations" and selecting the NAS device. If the issue persists, ensure that the NAS is correctly configured to share files and that there are no network issues preventing access.
[/LIST]
[/FONT][/COLOR]
[COLOR=#1B1642][FONT=&amp]
[LIST]
[*]Check for Updates: Ensure your system and Samba are up to date. Some users have reported that updating Samba resolved their issues.
[/LIST]
[/FONT][/COLOR]
[COLOR=#1B1642][FONT=&amp][COLOR=#F8F8F2][FONT=Consolas][COLOR=#F1FA8C]sudo[/COLOR] [COLOR=#F1FA8C]apt[/COLOR] update
[COLOR=#F1FA8C]sudo[/COLOR] [COLOR=#F1FA8C]apt[/COLOR] upgrade
[/FONT][/COLOR]


[/FONT][/COLOR]
[COLOR=#1B1642][FONT=&amp]
[LIST]
[*]Consult NAS Documentation: If you continue to experience issues, consult the documentation for your specific NAS device. There may be additional configuration steps required to enable file sharing with Ubuntu.
[/LIST]
[/FONT][/COLOR]
[COLOR=#1B1642][FONT=&amp]Remember, the exact steps may vary depending on your NAS model and the version of Ubuntu you are using. Always ensure that your system is secure and that you're following best practices for network security and file sharing [/FONT][/COLOR][COLOR=#1B1642][FONT=&amp][1]("https://askubuntu.com/questions/1229929/cant-acces-nas-anymore-after-upgrading-to-20-04")[/FONT][/COLOR][COLOR=#1B1642][FONT=&amp][2]("https://askubuntu.com/questions/1231885/ubuntu-20-04-cant-access-my-windows-network")[/FONT][/COLOR]

The key is to use precise prompts. The art of "prompt engineering". Or it is garbage in, garbage out.

---

### Post by MAFoElffen on 2024-04-21
Coming into this late, so I didn't read through the long post details, just skipped over the summary of it.

I don't see that as a problem with RAID itself (just another factor), but rather that you used an rsync option that deleted the files, once it confirmed that is backed them up (one-by-one)...

So you have "a backup" of them correct? Or was there a problem with the files rsync copied over? They could just be restored.

If you didn't have good copy of the files, then use "testdisk" or "photorec" to recover them.

---

### Post by OiPenguin on 2024-04-22
Thanks for the input. I'm scared of loosing my data so I'm currently awaiting an assessment and a price estimate from a professional. StarTech is interesting, but probably as a supplement to my server, not a replacement, once I've recovered my lost data.

---

### Post by OiPenguin on 2024-04-22
> **MAFoElffen said:**
> Coming into this late, so I didn't read through the long post details, just skipped over the summary of it.

I don't see that as a problem with RAID itself (just another factor), but rather that you used an rsync option that deleted the files, once it confirmed that is backed them up (one-by-one)...

So you have "a backup" of them correct? Or was there a problem with the files rsync copied over? They could just be restored.

If you didn't have good copy of the files, then use "testdisk" or "photorec" to recover them.

I'm afraid I don't have a proper backup. 
- The most outdated confirmed backup is 2000 (start) to 2013. Meaning 10 years is lost if this is the only one I'm able to recover.
- Another backup is a server with a (most likely) faulty power supply. My guess is that this is a backup from 2000 to approximately 2017, however I've yet to find out. The box has two 1TB disks set up as raid1. I've got an External sata hard drive case, but was unable to mount the disks on my Ubuntu-laptop, probably because the disks are part of a pair of Raid1 disks. Can I use testdisk to mount Raid1 disks in Ubuntu or do I need a further procedure? (I'm also searching for a new power supply, which I assume will be an easier solution.)
- The disks of the main server has been pulled out and delivered to a professional for assessment and a price quote.

Yours,

Lars

---

### Post by dragonfly41 on 2024-04-22
After hopefully the recovery shop pulls your data out of the fire I would sit back and think carefully about your future architecture.  Read here .. [https://www.reddit.com/r/editors/comments/12tl78y/is_raid_storage_still_worth_it_in_2023/](https://www.reddit.com/r/editors/comments/12tl78y/is_raid_storage_still_worth_it_in_2023/)

Do you need the hassle of RAID boxes? You can achieve redundancy in different ways and allowing you to take routine backups.  That is why I suggested the StarTech route.

The old RAID setup will be in some container. What is it?

Plan ahead where you will keep backups. Spread them in multiple locations. Remember the "deadman's handle" protocol. What happens if you fall under a bus. So recovery instructions must be documented too. Passwords?

Your server (spec?) can have an array of multiple plugin caddies, not necessarily  bound into your server tower casing.

Remember that if you try PhotoRec you will have a bunch of renamed files.  Further detective work needed to find the content. That is why I am taking a conscious step to place my assets into containers to aid last resort recovery.

There is a forensic tool I have just found which creates a forensic tree of assets. It s named ftree. It creats a json file of all filses in a location. Search HACK42 and DART. But this will not recover your data.

In conclusion give more information about the hardware containers of your RAID since others might have ideas. As written in link above RAID does not guard against human failure. Suggested use of GUI (Grsync, Lucky Backup) instead of command line but even there have a verification script that the profile is sane and follows best practice.

Having a local professional shop is your best hope.

Burn n+1 redundancy into your plans.

---

### Post by dragonfly41 on 2024-04-26
Any progress with the recovery shop? I am returning here since I remembered this recovery tool with good references .. although caveat I have never used it.

[https://www.grc.com/sr/testimonials.htm](https://www.grc.com/sr/testimonials.htm)

Contact old hand Steve Gibson and explain your plight.

---

### Post by OiPenguin on 2024-04-27
> **dragonfly41 said:**
> Any progress with the recovery shop? I am returning here since I remembered this recovery tool with good references .. although caveat I have never used it.

[https://www.grc.com/sr/testimonials.htm](https://www.grc.com/sr/testimonials.htm)

Contact old hand Steve Gibson and explain your plight.
Thank you. That looks like a very interesting program, although the website looks like its developed 20 years ago. I'm reading about the program now and I've not gone through all the information yet, but I have two questions which I've been able to answer:
- Can I make a bootable USB of this (Windows?) program from my Ubuntu machine?
- Can this program recover from disks set up with Raid?

You wrote *contact old Steve Gibson*. Are you suggesting that I actually contact him or rather that I purchase the software?

Regarding progress. The shop which has the disks updated me yesterday. After 3-4 days the disks are 65% analysed so I'll hear from them in the start of next week.

---

### Post by dragonfly41 on 2024-04-27
I was thinking that you might tap into his sphere of knowledge, possibly by trying to email him or via his forum. His research goes back to the days of spinning disks but has been updated to look at SSD performance. If you follow some of the YouTube chats his experience is interesting.
But .. reflecting overnight .. I'm not sure if that software can help with a human failure in inadvertently deleting files with rsync.   It might help other scenarios (cited often) where SSD's give up the ghost early in life.  So we have two scenarios: hardware failure and human failure. Keep up the research.
Good luck with the recovery. And of course you are planning now backup strategy.

[POSTSCRIPT]
But again .. I've just read advice from [@TheFu here post #6]("https://ubuntuforums.org/showthread.php?t=2497152") on that suggestion so I will withdraw the idea.

---

### Post by OiPenguin on 2024-05-04
An update. 

My disks are still with the local shop. I'm waiting for the result of the analysis and don't know why it takes so long time, nor the price of recovery.

In the meantime I've received a quote from another company. They charge $220 per disk for analyses. I've got three disks (the want to analyse the SSD with the OS on as well) which means about $660 for the analyses of three disks. Plus a further $2500 - 4500 for reconstruction of the data. When I enquired about the steep price the explanation was that Raid disks are more complicated.

Hence, if anyone has a suggestion as to how to to analysis and recovery on my own, please let me know. It is a viable option to invest some money, in hardware and software, to do this giving the extreme price estimate I've been given.

---

### Post by dragonfly41 on 2024-05-04
It seems that we are in the last chance saloon.

The first "local shop" is taking too long to assess. I would have asked up front for (a) references and (b) an estimate.

I think that you will have to take the risk to explore forensic recovery process yourself and learn from the experience (whether it succeeds or fails).

The next step is perhaps to try recovery through TestDisk and PhotoRec. If any images are recovered they will need to be categorised using labelling methods but we can consider that hurdle later if TestDisk/PhotoRec succeeds.

You will need a fresh drive, at least equal in size to your RAID, into which you might save recovered files. So get to the point where you have:

TestDisk/PhotoRec installed on LiveUSB (not RAID) and running on a LiveUSB.
Your RAID (or preferably a clone of your RAID) connected
A fresh drive waiting in sidewings to receive any recovered data.)




You wrote earlier:
> - I'm not sure which type of Raid I'm using and don't know how to find out. Anyway, as I understand from other threads, Raid protects against disk failure, not errors like I've made. The files (or the reference to the files) will be deleted on all partitions almost instantly.
It is vital that you understand type of RAID, ask the local shop which worked on it .. but gave you no results. Not hopeful with that route.

Some of recovery applications assume that you cannot access your RAID. But you made the error in deletlng so it is not hardware failure.

Here s one product which requires Windows to run.

[https://hetmanrecovery.com/download.htm?product_type=4](https://hetmanrecovery.com/download.htm?product_type=4)

Note: at this site a docking bay is suggested.

[https://hetmanrecovery.com/recovery_news/docking-station-an-additional-tool-for-data-recovery-from-raid.htm](https://hetmanrecovery.com/recovery_news/docking-station-an-additional-tool-for-data-recovery-from-raid.htm)

I use StarTech dual docking bay for multi drives (but have no experience with RAID recovery).

The first suggestion, although you gain advice from forum, is to subscribe to your own AI assistant. The one I recommend is PHIND.com.  The reason is that links to various references are given whereas other AI assistants only offer text replies.

This will cost you £10 per month subscription which you can close later after taking advice.

Remember that the "prompts" or "queries" for each session must be crystal clear.


Examples follow:

> What approach is recommended for a sole developer attempting to recover important family photos deleted in error. There is no hardware failure only human failure. Can deleted data held in RAID in Ubuntu be recovered? What tools are needed for self recovery since professional recovery shops are too expensive.

> If deciding to use Photorec it is understood that there will be no filenames attached to any recovered images. Are there methods for trying to relabel such recovered images? Perhaps an automation script allowing images to be viewed by an AI agent to caegorises into buckets. What AI scanning tools are suggested?

> Can AI scanning methods be pre-trained with existing samples of photos?

Here is one earlier session I received:

"For recovering data deleted in error on a Ubuntu system, several leading data forensic tools are available, each with its unique features and capabilities. Here's an expanded list of tools, including those you're already aware of, along with their specific use cases and requirements for RAID data recovery:"

"TestDisk: A versatile tool that can recover lost partitions, undelete files, and fix partition tables. It's widely used in forensics due to its user-friendly interface and powerful recovery algorithms. TestDisk supports various file systems, making it a comprehensive solution for Linux forensics".

"Photorec: Part of the TestDisk suite, Photorec is known for its ability to recover files without their original filenames. It's particularly useful for recovering media files".

"Foremost: A forensic data recovery tool pre-installed in Kali Linux but can be installed on any Linux distro. It can recover data in multiple media file formats and from images created with the dd command. Foremost is designed for forensic data recovery, making it suitable for uncovering embedded or hidden data elements from images".

"R-Undelete: Offers IntelligentScan technology for data recovery, including MBR and GPT recovery, and boot sector recovery on major file systems. It's capable of recovering files on ext, FAT, and NTFS systems".

"SafeCopy: This tool is effective for recovering data from damaged and bad sectors on a hard drive. It performs low-level IO operations to extract maximum possible data and can fix errors in data on CDs, DVDs, and even floppy drives".

"Scalpel: A powerful open-source file carving tool that extracts deleted files based on their file signatures and headers. Scalpel supports various file systems, making it versatile for Linux file recovery".
"
The Sleuth Kit: A collection of open-source command-line tools for digital investigations, including utilities like Autopsy and Photorec. It supports various file systems, providing wide coverage for Linux forensics".

"ddrescue: A GNU data recovery utility designed to retrieve data from damaged or corrupted storage devices. It operates in a progressive rescue mode, recovering easier-to-read data first before tackling more complex segments. ddrescue provides an interactive map and logging feature to track the recovery progress ".

"HACK42: While not detailed in the provided sources, HACK42 is a tool designed for data recovery and analysis, often used in forensic investigations. It's known for its ability to recover data from various storage devices and file systems".

"Autopsy: Part of The Sleuth Kit, Autopsy is a graphical interface to the disk forensics tools. It's used for disk imaging, file carving, and indexing, making it a comprehensive tool for digital forensics".

"DART (Digital Advanced Response Toolkit): A digital forensics toolkit that includes a variety of tools for disk imaging, memory analysis, and network forensics. It's widely used in law enforcement and cyber forensics for its comprehensive set of forensic tools".

"R-Linux: A data recovery tool that can recover files from ext2, ext3, ext4, ReiserFS, JFS, XFS, and Btrfs file systems. It's designed to recover files from Linux systems and is known for its ability to recover files even when the file system is severely damaged".


"For RAID data recovery, special requirements and tools may be necessary due to the complexity of RAID configurations. Tools like ddrescue and Foremost can be particularly useful for RAID data recovery, as they can operate on images of RAID arrays, allowing for recovery attempts even when the RAID configuration is damaged or the RAID controller is unresponsive. Additionally, understanding the specific RAID configuration (RAID 0, RAID 1, RAID 5, RAID 6, etc.) and the file system used can help in selecting the most appropriate recovery tool".

"When selecting a data recovery tool, consider factors such as ease of use, compatibility with your system, the specific file systems you need to recover from, and whether the tool offers a demo or trial version. This will help ensure that the tool meets your needs and can effectively recover your deleted data".

---

### Post by dragonfly41 on 2024-05-04
i should add a footnote. Since you will be using LiveUSB to be your "home forensic lab" by installing tools such s TestDisk/PhotoRec, ddrescue, R-Linux, and so on .. it should have reasonable size and importantly persistent. If not persistent you will have to reinstall these extra forensic apps every time you boot up. So search how to make *persistent* LiveUSB such as using MkUSB. And use USB 3.0 device and USB 3.0 port for speed.



Also glean information by studying multiple sites such as here (this one is in U.S.),

[https://www.salvagedata.com/raid-data-recovery/](https://www.salvagedata.com/raid-data-recovery/)

Note that data recovery vendors allow trials of their products to test if data can be recovered . without actually running the entire recovery. Avoid vendors who expect payment irrespective of whether recovery succeeds or not.

---

### Post by dragonfly41 on 2024-05-05
Although this writer has zero experience with RAID devices the broad model developing in mind (avoiding third party forensic data recovery specialists) is to create a mentor/mentee framework.


The idea is:
Subject (mentee) creates a local persistent LiveUSB expressly for forensic data recovery experiments on local drives.
Helper (mentor) creates a repository of forensic tools to download into mentee's LiveUSB in a series of eLearning processes (starting with PhotoRec).
One advice offered earlier by TheFu is that write capability to the target RAID must be disabled at earliest stage to avoid the further risk of overwriting data blocks to be recovered. But there is a cost penalty. they are not low costs.
Some of the data undelete products require Window 10 and so the nettle must be grasped to install Windows 10 on the projected LiveUSB which in turn accesses the RAID.
Write blocker research:
[https://www.opentext.com/products-and-solutions/partners-and-alliances/partner-directory/partner-directory-detail?id=001D000001nZXMPIA4](https://www.opentext.com/products-and-solutions/partners-and-alliances/partner-directory/partner-directory-detail?id=001D000001nZXMPIA4)
[https://www.opentext.com/products/listing#t](https://www.opentext.com/products/listing#t)
[https://www.opentext.com/products/tableau-forensic-bridges](https://www.opentext.com/products/tableau-forensic-bridges)
[https://www.opentext.com/products/tableau-forensic-bridges#overview](https://www.opentext.com/products/tableau-forensic-bridges#overview)
Tableau Forensic Bridge (write blocker for USB).
[https://security.opentext.com/tableau/hardware/details/t8u](https://security.opentext.com/tableau/hardware/details/t8u)
[https://security.opentext.com/video/demo/T8u-Introduction-and-Setup-Video](https://security.opentext.com/video/demo/T8u-Introduction-and-Setup-Video)
[https://www.forensicfocus.com/forums/general/what-can-happen-if-write-block-is-not-enabled/](https://www.forensicfocus.com/forums/general/what-can-happen-if-write-block-is-not-enabled/)
[https://www.forensicfocus.com/](https://www.forensicfocus.com/)
[https://ubuntuforums.org/showthread.php?t=2491362&highlight=mdadm+RAID+recovery](https://ubuntuforums.org/showthread.php?t=2491362&highlight=mdadm+RAID+recovery)
In further research into this discussion (since I do not use RAID)  I learned about mdadm.
sudo apt install mdadm
man mdadm
Next I searched this entire Ubuntu forum with keywords:
mdadm RAID recovery
One of many threads
[https://ubuntuforums.org/showthread.php?t=2491362&highlight=mdadm+RAID+recovery](https://ubuntuforums.org/showthread.php?t=2491362&highlight=mdadm+RAID+recovery)
read sage advice from TheFu.
Also i read about "write blockers".  but it is debatable whether such an investment is worthwhile.
My current thinking is that you should use a local LiveUSB which can be primed from remote repo to experiment with different tools.
Some require Windows so a LiveUSB (Ubuntu) with Windows virtual machine might be worth building.

---

### Post by dragonfly41 on 2024-05-07
Any progress with PhotoRec?
Setting aside the flood of references given earlier, another idea is for you to approach a local university in your country experienced in data forensics, talk to a professor in forensics and request to assign the recovery task to a forensics graduate as a case study.

[https://www.noroff.no/en/studies/university-college/digital-forensics](https://www.noroff.no/en/studies/university-college/digital-forensics)

---

### Post by OiPenguin on 2024-05-07
> **dragonfly41 said:**
> Any progress with PhotoRec?
Setting aside the flood of references given earlier, another idea is for you to approach a local university in your country experienced in data forensics, talk to a professor in forensics and request to assign the recovery task to a forensics graduate as a case study.

[https://www.noroff.no/en/studies/university-college/digital-forensics](https://www.noroff.no/en/studies/university-college/digital-forensics)

I've not attempted on my own yet. I heard back from the local shop yesterday and logged on remotely to view my files. Pictures are recovered to a great degree. Video files are still in process. Hence, it looks promising so far and I'm very happy if I don't have to attempt to learn how to do this on my own.

Thanks for all your good input. Although I haven't attempted recovery on my own, I've learned a lot through reading what you've written and some of the many references you've provided.

---

### Post by dragonfly41 on 2024-05-07
Good news. Follow the advice penned frequently by TheFu to backup (n times, locations).

---

