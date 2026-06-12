---
title: "Where's the 'Public' folder gone?"
date: 2024-07-29
forum: General Help
---

### Post by aj34 on 2024-07-29
Would appreciate help to try and locate the missing 'Public' folder on my Desktop PC (Ubuntu 20.04) although perhaps this is more a question for a Windows forum?

The 'Public' folder, in the folder 'Users', has gone awol. I can't find it anywhere on the HDD.

My PC is dual-boot and has two HDD's fitted. HDD 1 has the Ubuntu OS (which I use almost exclusively) and HDD 2 has a Windows OS (rarely used). I use HDD 2 to store all user personal files, i.e. within the Windows file structure. It's this second HDD that had a Public folder which appears to have vanished. Fortunately, I recently manually copied our personal files onto an external HDD which included the missing 'Public' folder and all subfolders and files within so I should be able to restore it but I'm interested to learn why it disappeared from HDD 2.

Whilst I know little about the software workings of computers, I can't believe I've accidentally deleted the folder without realising or being made aware (warning messages/popups etc).

Any suggestions as to what may have happened? If you're kind enough to reply, please avoid tech jargon and acronyms/abbreviations whenever possible, thanks.

---

### Post by yancek on 2024-07-29
>  The 'Public' folder, in the folder 'Users', has gone awol.

I would say that a 'folder' missing on your windows system is definitely a windows problem.  You are referring to the Public folder on your windows system partition in the Users folder?  If you rarely use windows, why would you store your files from Ubuntu on a windows ntfs filesystem partition?  You could create a partition with a Linux filesystem on that drive if you wanted.  If you share with others who use windows, it would be best to use a separate data partition even if it is ntfs as you can access it from Ubuntu.

You don't indicate which windows version you have but more recent versions always hibernate by default and if you booted into windows recently, it may have been left in a hibernated state which would make it inaccessible from any Linux.  If that is not the case, if you can see and access other folders/files on the windows partition, it is another problem.

To clarify, you can boot Ubuntu but that folder isn't available to you when logged into Ubuntu, correct?  You can boot windows but that folder is not available to you there, correct?
Have you tried to mount the partition from a terminal in Ubuntu to see if that directory is available?  Better to do this than using a GUI as you are more likely to get output in the form of warning or error messages.

---

### Post by oldfred on 2024-07-29
I never have used & did not really know I have a Public folder.
In Kubuntu it does show in Dolphin file browser.

[code][FONT=monospace][COLOR=#54ff54]**fred@z170-noble**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ cat /home/fred/.config/user-dirs.dirs [/COLOR]
# This file is written by xdg-user-dirs-update 
# If you want to change or add directories, just edit the line you're 
# interested in. All local changes will be retained on the next run. 
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped 
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an 
# absolute path. No other format is supported. 
#  
XDG_DESKTOP_DIR="$HOME/Desktop" 
XDG_DOWNLOAD_DIR="$HOME/Downloads" 
XDG_TEMPLATES_DIR="$HOME/Templates" 
XDG_PUBLICSHARE_DIR="$HOME/[COLOR=#ff0000]Public[/COLOR]" 
XDG_DOCUMENTS_DIR="$HOME/Documents" 
XDG_MUSIC_DIR="$HOME/Music" 
XDG_PICTURES_DIR="$HOME/Pictures" 
XDG_VIDEOS_DIR="$HOME/Videos" 
[COLOR=#54ff54]**fred@z170**[/COLOR]
[/FONT][/]

---

### Post by aj34 on 2024-07-29
Thanks for your swift responses. In answer to your questions:

*You are referring to the Public folder on your windows system partition in the Users folder? *[COLOR=#0000ff]Yes[/COLOR]

*If you rarely use windows, why would you store your files from Ubuntu on a windows ntfs filesystem partition?*[COLOR=#0000ff] Simply because this PC started life as a W10 only PC with one HDD so, for a year or two, all our personal files were stored in the Windows file structure and I continued to store personal files there when I installed Ubuntu. I have never made the decision to move all these personal files onto the Ubuntu HDD and wipe W10 from the PC (hedging my bets, I guess). From my limited understanding, I wouldn't be able to access my personal files when booted into Windows 10 if the files were on the Ubuntu HDD (partition?).[/COLOR]

*If you share with others who use windows... *[COLOR=#0000ff]The only other person who uses the PC uses whatever OS that I have setup, i.e. always boots into Ubuntu by default.[/COLOR]

*...it [W10 OS] may have been left in a hibernated state which would make it  inaccessible from any Linux.  If that is not the case, if you can see  and access other folders/files on the windows partition, it is another  problem. *[COLOR=#0000ff]Yes, I have access to all other user folders/files on the Windows partition including those I've saved there when using Ubuntu.[/COLOR]

*To clarify, you can boot Ubuntu but that folder isn't available to you when logged into Ubuntu, correct?* [COLOR=#0000ff]Correct. I'm always able to access files on the W10 HDD when booted into Ubuntu, which shows up in the Ubuntu File (manager?) as the second HDD as follows: Other locations > On this computer > 1000GB Volume.[/COLOR]

*You can boot windows but that folder is not available to you there, correct?* [COLOR=#0000ff]Hadn't thought of booting into W10 to look. Will try then report back.
[/COLOR][I]
Have you tried to mount the partition from a terminal in Ubuntu to see  if that directory is available?  Better to do this than using a GUI as  you are more likely to get output in the form of warning or error  messages. [COLOR=#0000ff]				[/COLOR][/I][COLOR=#0000ff]This is where my lack of knowledge let's me down. I don't fully understand the question. Fact is, I can always get access to the W10 HDD (partition?) from Ubuntu. Don't know what a "directory" is.[/COLOR]

Because I backed up personal files manually, I wonder if I accidentally "Moved" rather than "Copied" the "Public" folder. I backed up the folders/files in quite a piecemeal fashion so possibly could have done this.

[I]
I never have used & did not really know I have a Public folder in Kubuntu it does show in Dolphin file browser. [/I][COLOR=#0000ff]I think that's a different "User" folder. The one I have a problem with is part of the Windows folder structure, not Linux.[/COLOR]

---

### Post by TheFu on 2024-07-29
A few releases ago, Ubuntu (and the flavors) changed the permissions on $HOME to be 750, which means "other" cannot visit, view, see, modify, anything inside a HOME directory of any user, so the idea of a "Public" directory makes no sense.  Directory permissions don't allow it, at least the default permissions in Ubuntu systems.

There was an html_public/ directory that webservers would allow to be used.  I know apache supported it. Don't know about the others.
The way to access it was through **[http://server-name/~thefu/](http://server-name/~thefu/)**  That would map to ~thefu/public_html/ - just change the username for different users.  I never tried it with 750 permissions, but doubt it would work because the www-data userid wouldn't have read access to the HOME for any userids.

I know ZERO about MS-Windows and HOME directories shared on the network in anyway. Never used them myself.

---

### Post by yancek on 2024-07-29
>  [COLOR=#0000ff]I have never made the decision to move all these personal files onto the Ubuntu HDD and wipe W10 from the PC[/COLOR]

You don't need to do that.  If you have a windows OS installed, you can use the Disk Management tool in windows and shrink the system partition (usually referred to as the C:\ partition or drive and then create another partition on which to install just data.  Less chance that way of messing up your windows by accidentally deleting a system file but that's for another day and not related to your problem.  And yes, if you want to share between Ubuntu and Windows, you need a windows filesystem on the partition or some 3rd party software insalled on windows.

If you can access other folders/files on windows from ubuntu then hibernation is NOT the problem.

I would suggest that you do boot windows to see if the directory is still there.  If you can see and access other files and directories on windows from Ubuntu now, then the Public directory was probably moved/deleted accidentally.

> [COLOR=#0000ff]Don't know what a "directory" is.[/COLOR] 

Before windows and dos existed, other operating systems such as Unix and CP/M used the term directory which windows users call 'folders'.  I don't know why they did that.

The Public folder oldfred is referring to is different.  There is also a Public directory/folder in Linux /home/username directories which I've never used but think it is used for reasons similar to the one in windows.

Mounting and accessing a windows partition by manually doing it in a terminal might give useful information and is not difficult.  You can find countless tutorials online explaining how to do it.  Since we don't know your partition layout we can't give specific instructions.  The link below gives an explanation of the steps.

[https://www.simplified.guide/linux/disk-mount](https://www.simplified.guide/linux/disk-mount)

---

