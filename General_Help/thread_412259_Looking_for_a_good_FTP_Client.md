---
title: "Looking for a good FTP Client"
date: 2007-04-17
forum: General Help
---

### Post by malfist on 2007-04-17
Hello,

I'm looking for a good FTP client for work with my webpage and I can't seem to find one for Ubuntu. I've looked at gFTP which is pretty good but I need something that can check for files that have been updated (kinda like SVN) and update them or visa-versa. I would prefer it to be platform indepenant but that is not a requirement. This computer is too slow to load the java VM though so...

Any help would be appreceated.

---

### Post by leibowitz on 2007-04-17
What do you want, GUI? Console? Firefox Plug-in ?

GUI)
* I remember using Kbear, or just Konqueror (I don't like those two, but they should do better than gftp) get more at [http://kde-apps.org/index.php?xcontentmode=236](http://kde-apps.org/index.php?xcontentmode=236)
* FileZilla, still in some long-beta-alpha-gamma release cycle and buggy (can be harmful) Don't try this at home.

Console)
* lftp and other tools are very powerful (but I don't use them either)

plug-in for firefox)
* fireftp, that's a great plug-in and cross-platform (I don't use it)

Finaly I just use Nautilus cause it suits my needs. But I don't think any of those will suits yours. Maybe you can start writing your own, or saying what exactly you need to change in gftp and maybe I will do just that in one or two years (I'm just too busy right now).

---

### Post by malfist on 2007-04-17
The site is actually http, I'm just connecting to it through ftp to make it easier to update and change. I GUI would be nice, but not nessecary, I've used SVN though the command line.

---

### Post by Espreon on 2007-04-17
Well if you want an FTP app sorta thing try FileZilla under Wine, it works great!

---

### Post by aysiu on 2007-04-18
FileZilla is now native (don't need Wine any more). FireFTP is also a good client.

---

### Post by malfist on 2007-04-18
I will check them out, thank you.

---

### Post by spliskin on 2007-04-18
kasablanca is a great ftp client.

---

### Post by malfist on 2007-04-18
Where can I find the native FileZilla, sourceforge only has the windows (that I've been able to find).

---

### Post by aysiu on 2007-04-18
> **malfist said:**
> Where can I find the native FileZilla, sourceforge only has the windows (that I've been able to find).
**Step 1**:
[Enable extra repositories](http://www.psychocats.net/ubuntu/sources)

**Step 2**:
Install FileZilla by pasting this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo apt-get update && sudo apt-get install filezilla
```

---

### Post by malfist on 2007-04-18
E: Couldn't find package filezilla

Extra repositories are enabled.

---

### Post by aysiu on 2007-04-18
> **malfist said:**
> E: Couldn't find package filezilla

Extra repositories are enabled.
Are you using 6.10 (Edgy Eft) or 7.04 (Feisty Fawn)?

I think it's available for only those two versions of Ubuntu:
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=filezilla&searchon=name&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=filezilla&searchon=name&subword=1&version=all&release=all)

---

### Post by leibowitz on 2007-04-18
There's package for Dapper and Edgy in here[1]
[http://download.tuxfamily.org/3v1deb/pool/dapper/3v1n0/](http://download.tuxfamily.org/3v1deb/pool/dapper/3v1n0/)
[http://download.tuxfamily.org/3v1deb/pool/edgy/3v1n0/](http://download.tuxfamily.org/3v1deb/pool/edgy/3v1n0/)

Or just use the repositories[1]
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) dapper 3v1n0
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy 3v1n0

[1] Use one or the other (Dapper OR edgy; depending on your version. Not both!)



If you go the repositories way, you have to
- Add the line provided "deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) dapper 3v1n0" in the file /etc/apt/sources.list
- update your sources using "sudo apt-get update"
- install filezilla "sudo apt-get install filezilla"

---

### Post by Espreon on 2007-04-18
> **spliskin said:**
> kasablanca is a great ftp client.

Yeah but it is slow in my experience with it, I would recommend FileZilla to everyone since it is fast, straightforward and reliable.

---

### Post by louieb on 2007-04-18
Call me crazy if you like, but I use gnome-commander. It sometime crashes. But I just like the GUI. and it does have a compare directory menu item.

---

### Post by crispy_420 on 2007-04-18
What is wrong with gFTP? It is the the repos and it works.

---

