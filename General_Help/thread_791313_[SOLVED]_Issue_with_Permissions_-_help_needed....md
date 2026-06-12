---
title: "[SOLVED] Issue with Permissions - help needed..."
date: 2008-05-12
forum: General Help
---

### Post by k3kiaze on 2008-05-12
**Background: **I could only use "[SIZE="2"]Wine winefile[/SIZE]" and certain other commands unless i went into terminal and "[SIZE="2"]su[/SIZE]" to get root access, and I hated using the terminal every time to do that. So I decided to repair permissions. Being a noob at Linux I googled many websites and did this: 

Boot into recovery mode and type "[SIZE="2"]chown -R root /[/SIZE]", when I rebooted I could not login and was given an error message that read "[SIZE="2"]user's $HOME/.dmrc file is being ignored ....[/SIZE]" so I logged into windows, googled again and did this next: 

In recovery mode typed: "[SIZE="2"]chown -R user:user /home/user[/SIZE]" rebooted, logged in, cannot access internet, cannot access hdd, cdrom, usb drive and "su" command in terminal does not work. So i rebooted to recovery mode again and did "[SIZE="2"]chown -R user:user /[/SIZE]" rebooted, I get the "[SIZE="2"]user's $HOME/.dmrc file is being ignored ....[/SIZE]" error message after I log in but with no access to drives/network.

**Current Situation:** When I click on the HDD in File manager, gives me an error something about "[SIZE="2"]org.freedesktop.DBus.Error.AccessDenied[/SIZE]". At this point I've given up trying to fix permissions and decided to clean install Ubuntu. But i have very important files in Ubuntu that I want to copy to somewhere, but have no access to drives/network.

**What I've tried doing:** Tried using the mount command in recovery mode, does not work I think I'm not using it correctly. Install Macdrive & Virtual Volumes on the windows partition but they don't see the Linux partition. Read somewhere on the internet that my user should belong to a group '[SIZE="2"]storage[/SIZE]', but no group '[SIZE="2"]storage[/SIZE]' exists.

**The Bottom line:** All I'm looking to do is copy my files either from Linux to windows or vice versa and reinstall Ubuntu. If somehow it's possible to get Ubuntu working again, that would be awesome. I haven't gone into details about my system and extensive error messages because 1. My post is too long as it is. 2. I have to go to Ubuntu write everything down and then restart into windows and 3. It's 4 am and I have to work tomorrow.

If you need any more info from me **please **let me know. I'm dying to get this issue fixed. Any help is appreciated. Thanks.

---

### Post by kesman on 2008-05-12
[http://www.fs-driver.org/](http://www.fs-driver.org/)

install this to be able to copy your files from linux partition to windows and then install ubuntu again.

Some applications require root access, that's how linux works so the "normal" user don't get to mess things up. Get used to it.

---

### Post by k3kiaze on 2008-05-12
I installed EXT2 IFS and it could see my Linux partition. Gave it a drive letter "[SIZE="2"]J:[/SIZE]" but could not access the drive J, said "[SIZE="2"]Disk is not formatted, Format Now?[/SIZE]" I said '[SIZE="2"]no[/SIZE]' of course. 

Anyway I decided to see what I had selected during Ubuntu installation, so i loaded the Install disk, and see that I had selected '[SIZE="2"]JFS[/SIZE]', so maybe that's why it did not work with EXT2 IFS. I tried to quit installation and it logged me into a temporary Ubuntu session from the CD. I could now see my WINXP and Linux partitions, and view all files, but could not copy files from linux to windows due to permission issues.

So I logged into Linux (normal) and changed permissions for the files I wanted to copy (grant other read and write access to folder) restarted to install cd, select Ubuntu demo (or whatever that 1st option is) and copied ALL my files YIPEE!!

Thanks for you reply kesman, you gave me the push in the right direction that solved my issue, but when you say "[SIZE="2"]Get used to it[/SIZE]" I have to say that's exactly what I'm trying to do, completely ditch WIN and use LINUX. So I have a few questions for you or anyone else reading this:

1. Do you recommend that I use EXT2 instead of JFS?
2. I want to have 1 user and that user should be able to do EVERYTHING (like root), what options do I need to choose?
3. and finally, If i ever need to repair permissions what command do I run? 'cos this is why I'm reinstalling LINUX now.

I understand that Linux is more advanced than windows, and therefore options aren't just simply presented to you, that's why I appreciate people helping people like me make this transition. Keep up the good work in the forums.:)

---

