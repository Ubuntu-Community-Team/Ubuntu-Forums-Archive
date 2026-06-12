---
title: "Installing IglooFTP PRO"
date: 2007-05-09
forum: General Help
---

### Post by PerlMountain on 2007-05-09
[size=1][edit]I did search but couldn't come up with a lot of info[/edit][/size]

Hi,

Obviously I'm really new at all of this. We're transitioning our production development office enviro over to Linux from WinBlows.

I do limited work in shell on clients web servers as well as our own.
I am _NOT_ a "real" *nix admin, though the sound of it puts a gleam in my eye ;)

--Help please--

I installed GFTP and can do nothing except connect to the box, download and upload. I cannot edit files on-the-fly, cannot right-click, set perms, etc.

I like the look and sound of Igloo. I currently use Ipswich WS-FTP Pro.

I found this, it looks fairly simple, except:
"***then "cd" in the newly created directory ***"
[quote=igloo]
Installing IglooFTP PRO
Compressed Tar Archive: 

Decompress the archive "tar xvfz filename", then "cd" in the newly created directory and type "Install" .[/quote]

[list][*]Where do I put the tarball?[/list]

Jumping ahead here to save redundancies:
[list][*]Is this going to be the same place I put all tarballs when I want to install something else?[/list]

Thank you .. and off we go!

PME

---

### Post by rai4shu2 on 2007-05-09
Just stick it on the Desktop. Should be fine. Then just "tar xvfz ~/Desktop/filename", etc.

Personally, I prefer FileZilla.

---

### Post by PerlMountain on 2007-05-09
Tey, thank you.

I'll take a look at filezilla also.

TY :)

PME

---

### Post by aysiu on 2007-05-09
You could also try installing the .rpm. That may be easier.

Paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
wget -c http://www.iglooftp.com/dl/linux/IglooFTP-PRO-1.2.5-1.i386.rpm
sudo apt-get update
sudo apt-get install alien
sudo alien -i IglooFTP-PRO-1.2.5-1.i386.rpm
```

---

### Post by PerlMountain on 2007-05-09
Sweet,

That worked perfectly. Previously, I had followed some instructions I found (or maybe didn't follow), unpacked the tarball etc, but I couldn't get it fired up.

I'm still trying to figure out our computers though, I'm a ways off from being done with them :)

Thanks for that :)

PME

---

### Post by aysiu on 2007-05-09
By the way, the four most popular graphical FTP clients among forum users are gFTP, Filezilla, FireFTP (Firefox extension), and Konqueror: [What's your favorite graphical FTP client?](http://ubuntuforums.org/showthread.php?t=413665&highlight=ftp+client)

---

### Post by PerlMountain on 2007-05-09
> **aysiu said:**
> By the way, the four most popular graphical FTP clients among forum users are gFTP, Filezilla, FireFTP (Firefox extension), and Konqueror:[/url]

Cool, I may have to try them all. I tried gFTP, but it's got some things I don't like, for example, I MUST be able to save passwords for servers, I work on too many of them to have to look up passwords and I use crazy passwords I can't even remember.

The thing that has me baffled is while automatically installed software, like gFTP creates a quick-launch right there in my desktop programs pull-down, but if I install something manually, I have NO idea where it's at or where to launch it from.

It took me 2 hours to launch uTorrent under Linux.

My wife gave me that program URL 3 days ago when we started downloading different *nix OSs, on Win, and I had it installed and running a download of a Ubuntu Torrent in about 30 seconds from the first time I ever laid eyes on the download URL.

I'm trying to get myself proficient enough at *nix so that I can just switch permanently, but I've got to have a test system set up for work before I do. I'm going to cut my fingers off if I can't switch off of WinBlows pretty soon.

*Almost* all _**I**_ need is an FTP client, Notepad and some things to batch files. I don't do any of the graphic design, flash, video editing or anything like that here.

My wife and daughter will need help because they do all of the major design work, so I've got to learn support for this OS to some extent.

Thank you for everything :)

PME

---

### Post by nix4me on 2007-05-09
I prefer KFTPGrabber.  It's the most compatible and feature rich FTP client I have found.

nix4me

---

### Post by PerlMountain on 2007-05-09
Thank you, I'll be looking into several this week.

I just want to find a good one and keep it. I like WS_FTP Pro, but it has some issues. It's also a Win program, I could maybe use Wine, but I'd rather stick with as much *nix software as possible. I didn't even try to use it.

Thank you,

PME

---

