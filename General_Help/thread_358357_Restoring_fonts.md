---
title: "Restoring fonts"
date: 2007-02-10
forum: General Help
---

### Post by splax on 2007-02-10
When browsing the web for a solution to clean up my fonts a bit, I found [_this_]("http://ubuntuforums.org/showthread.php?t=292729&page=2") thread. I followed what it said and entered the lines into the terminal (uh.. a couple of times actually, I'm quite sure this is where the problem lies) and after logging out and back in the fonts were like [_this_]("http://img300.imageshack.us/img300/8558/screenshothm8.png").

Is there any solution available to restore my fonts to how they previously were? Your time is greatly appreciated.

---

### Post by kerry_s on 2007-02-10
Well if you follwed the guide there should be a backup.

sudo mv /etc/fonts.backup /etc/fonts

If you over wrote the backup with the fugly fonts try

sudo dpkg-reconfigure fontconfig-config
select> autohinter> always> no
or
sudo dpkg-reconfigure fontconfig
or
sudo fc-cache -v
or
sudo defoma-reconfigure -f


Remember you need to restart X to see changes( ctrl +alt + backspace )

---

