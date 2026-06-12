---
title: "Recent issues with NFS shares (various 17.10 flavors)"
date: 2017-10-31
forum: General Help
---

### Post by kalyp on 2017-10-31
Hello,

I have a weird issue on a computer running Ubuntu, and one Xubuntu, both 17.10. Another computer, running 16.04.3, does not have this issue.
On the 17.10 computers, I cannot cut, move or rename files on NFS shares from the window manager (true for Nautilus on Ubuntu, and Thunar on Xubuntu). No problem at all from the command line, and permissions are correct, but within the window manager these actions are not possible (nothing happens) and the corresponding entries on a right click are grayed.
Any idea what's going on? I *think* it's only been for a few days (ie after some recent upgrade) but I'm not positive when that might have happened nor which package change might have triggered this. 
This is really annoying as most of my files are on an NFS-mounted share... (no issue mounting the same share using CIFS, BTW, but I need NFS because I use symbolic links that are not handled by CIFS).

Any help much appreciated, I haven't found anything relevant online.

Thanks in advance!!

PS just noticed this is likely a duplicate of [https://ubuntuforums.org/showthread.php?t=2375595](https://ubuntuforums.org/showthread.php?t=2375595) - didn't find it when looking at the time.

---

### Post by HermanAB on 2017-11-01
Run nautilus from a terminal, so that you can see the error messages when you browse the NFS server.

---

### Post by kalyp on 2017-11-01
Thanks! I should have thought of this one :) however, no error. See attached screenshot. No error either when I drag a file to a folder attempting to move it.
[ATTACH=CONFIG]277370[/ATTACH]

---

### Post by HermanAB on 2017-11-01
Hmm, what happens when you try cp and mv from the command line?

---

### Post by kalyp on 2017-11-01
Works with no problem, which is why I'm so puzzled, it doesn't look like a permission issue.
Note that from nautilus I can copy, but not paste (pasting locally is fine, not to a NFS share). Impossible operations are move, rename, cut, paste, and new folder (anything that writes to the NFS share within nautilus / thunar). All of these are totally fine via a terminal.
Thanks :)

---

### Post by kngharv on 2017-11-06
I got exact same issue.  nothing show up in /var/logs neither.  This is one of those things I*HATE about Linux (I've been using Ubuntu since 8.04 continuously).   Ubuntu staff just decided to make some small changes just to prove rest of users that we are still newbie thus these Ubuntu employees feel good about themselves... sigh...

---

### Post by kalyp on 2018-01-23
Bumping this thread just in case someone has more information since November. I still have this issue, which is incredibly annoying as most of my files are on NFS share and that makes nautilus/thunar useless - I have to do everything from a terminal.
Thanks!

---

### Post by kngharv on 2018-01-24
> **kalyp said:**
> Bumping this thread just in case someone has more information since November. I still have this issue, which is incredibly annoying as most of my files are on NFS share and that makes nautilus/thunar useless - I have to do everything from a terminal.
Thanks!

I have the same issue as well.  This it doesn't matter what kind of file manager I*use:  nautilus, nemo, etc, all graphical file manager will have this permission issue.

if i log in through terminal, everything works fine, mv, rm, etc.

and apparently you and I are the only two person uses graphical file manager over NFS?

---

### Post by wildmanne39 on 2018-01-24
Hello kngharv, please start a new thread to get help with your issue in the appropriate forum with a descriptive title instead of posting in an old thread you are more lie to get the help you need.

Thanks

---

### Post by kalyp on 2018-01-25
Doesn't it make more sense to keep both our issues together since it seems to be the exact same one? kngharv, if you start a new thread, please post it here so that I can subscribe to it.
It does appear we are the only two persons using graphical file managers over NFS, yes :)

---

### Post by kumharas on 2018-02-07
We are three persons now. I justed upgraded ubuntu to 17.10 yesterday and got exactly the same issue. 
Any solution?

---

### Post by kalyp on 2018-02-07
Sorry, not for me. Still opening a terminal whenever I want to copy/rename/move a file, which is extremely annoying. Anyone has filled a bug about this yet? if not I'll do it...

---

### Post by feydreva on 2018-03-27
Hello, 

I have same issue : 
[https://askubuntu.com/questions/1000973/nautilus-cannot-write-into-1st-directory-of-a-nfs-share/1012455#1012455](https://askubuntu.com/questions/1000973/nautilus-cannot-write-into-1st-directory-of-a-nfs-share/1012455#1012455)

seems to be a nautilus bug..

---

### Post by kngharv on 2018-04-08
it's not a nautilus bug.  because I*am using nemo, and it has the same bug.  I suspect the bug is in x-server somewhere.

---

### Post by kngharv on 2018-05-28
I did that first:

[https://ubuntuforums.org/showthread.php?t=2375595](https://ubuntuforums.org/showthread.php?t=2375595)

no one can help me regardless.

---

