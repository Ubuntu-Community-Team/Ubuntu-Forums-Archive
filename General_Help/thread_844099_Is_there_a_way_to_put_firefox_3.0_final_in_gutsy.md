---
title: "Is there a way to put firefox 3.0 final in gutsy?"
date: 2008-06-29
forum: General Help
---

### Post by Swmmrman on 2008-06-29
Been trying for a few days now.  Im not eager to go to hardy as i have web servers/forums on this comp and backing them up has always proved difficult.
I would like to have firefox 3 final.  But have found no way to do this.  I have seen the betas and RCs but not the final.  can anyone help me.

---

### Post by Bubba64 on 2008-06-29
I just installed the main release. I downloaded the targz to open in the archive, then extracted it into home and opened the FF file and drug the launcher to the top panel where a window opens to name the launcher. This if the final release was simple and will not be updatyed from any repositories though, but it had all my bookmarks and addons from FF2 installed in FF3

---

### Post by bingoUV on 2008-06-29
Download from here : [http://www.mozilla.com](http://www.mozilla.com). It will be a tar.bz2 archive. Save it to a directory. On command-line, go to the directory and type
```

tar -xvjf firefox-3.0.tar.bz2
cd firefox
./firefox &

```

---

### Post by Swmmrman on 2008-06-30
Bleh i did both of the above while i was bored at work today(I have alot of free time and boss that doesnt mind me playing with linux).  Was hoping that there was something Cleaner...

---

### Post by danwood76 on 2008-06-30
Cleaner?

You could install it where FF2 currently resides and add a symlink from /usr/sbin to the firefox executable.
Then add the menu item.

Theres not a lot more to do than that is there?

---

### Post by Swmmrman on 2008-06-30
I guess not.  i have been relying to much on prebuilt debian packages.  Kinda silly.  I compiled java.  Installed VMware server from scratch..  But i need a .deb for firefox 3.0.....

---

