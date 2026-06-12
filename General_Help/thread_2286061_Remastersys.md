---
title: "Remastersys"
date: 2015-07-09
forum: General Help
---

### Post by tom171 on 2015-07-09
Anyone know if there's a way to install remastersys or somewhere to download it from?  I found the remastersys.gpg.key, but looks like you also need the precise main file?  Is there a way to install with just the key?  I'm very new to Linux.  I believe I need the precise main file as well.  remastersys.com no longer exists and last time I installed through geekconnection I believe, but that doesn't seem to exist anymore either.  I've formatted and reinstalled my system since then.  I like that it made an exact copy of my system onto a live cd with installation option.

---

### Post by TheFu on 2015-07-10
I thought remastersys was deprecated. It had a good run. There are other options - but I don't recall any of their names right now. Sorry.

The web search I'd use is "remastersys vs"  that should show alternatives.

Since mastering a little scripting and ansible, I haven't needed to make a "master" ISO.  That isn't to say there aren't excellent reasons for a tool like this.

Being new to Linux, you might appreciate a free power-user PDF book. This directed learning will ensure certain basic knowledge isn't missing. [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)

---

### Post by sudodus on 2015-07-10
> **tom171 said:**
> ... I like that it made an exact copy of my system onto a live cd with installation option.

If you 'only' want an exact copy of your system, there are several alternatives.

Linux systems are portable between computers, as long as you avoid installing proprietary drivers. So you can run an exact copy of your system in another computer (from an internal drive or from an external drive (eSATA or USB)). ***Clonezilla*** is a tool for cloning alias exact copying.

You can even run a system, where the files are copied including the file permissions (which is not an exact copy). You can use the [One Button Installer](https://help.ubuntu.com/community/OBI) for this purpose. If you manage the bootloader manually, you can also make a copy with ***rsync*** or some other method, which can keep the file permissions.

---

### Post by tom171 on 2015-07-18
I see that I still have remastersys on another copy of Linux.  Is there a way to extract it from there and copy the files over to a different install?

---

### Post by sudodus on 2015-07-18
If you have a .deb file (containing remastersys), it might work.

---

### Post by TheFu on 2015-07-18
> **sudodus said:**
> If you have a .deb file (containing remastersys), it might work.

The downside is that dependencies will be locked until the .deb file is removed. That is a risk when no using a package manager, so if you do go this way, best to install, use, remove.

---

