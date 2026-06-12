---
title: "Making folders secure"
date: 2006-12-02
forum: General Help
---

### Post by bg1256 on 2006-12-02
In Windows, I could make certain folders invisible, if I didn't want other people to be able to view them if I was logged onto my computer. I used this to keep financial records and other personal items away from immediate view.

I'm wondering if there is a way to do something similar in Ubuntu. I only have one username, but I am always logged on. And living in a dorm, I often have friends over who experiment with my computer, given it's a Linux system, and they've never seen it before.

But I'd like to be able to keep certain folders from view, or at least make them password protected. Is there any way to do something like that?

---

### Post by Saphira on 2006-12-02
name the directory with a . in front of it like .hidden or such it wont show up in an ls call or unless you do an ls -a and it wont show up if you click on home in gnome

---

### Post by CatKiller on 2006-12-03
Some other options, if you want to keep your computer logged into a particular account are to either make a different account for when you want to access your personal data and make it so that your normal account can't access it, or to make a new partition on your hard drive to store your personal data, and only mount it when you need to look at that data.

---

### Post by aysiu on 2006-12-03
Along the lines of what CatKiller's suggesting, you can change ownership to root for that folder and then make the permissions read/write for root only.

```
sudo chown -R root:root /path/to/folder
sudo chmod -R 600 /path/to/folder
``` That way, you'd have to launch Nautilus or Konqueror as root (and enter a password) in order to view the folder.

---

### Post by bg1256 on 2006-12-03
Thank you all for the help.

Just one more thing to make Ubuntu life easier :p

---

