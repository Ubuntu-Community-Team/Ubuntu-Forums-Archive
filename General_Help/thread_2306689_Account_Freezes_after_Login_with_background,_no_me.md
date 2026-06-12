---
title: "Account Freezes after Login with background, no menu; Guest Works"
date: 2015-12-17
forum: General Help
---

### Post by justin76 on 2015-12-17
I've been running Ubuntu 14 for a while now. I came home today, and a program was frozen on the screen. So I restarted the computer and when I logged back on, it got stuck with just a background after I entered my password. I only have one main account and a guest account as options. The guest login works fine, but it's so restricted that I can't do anything. For some reason I can't use su or susu on a terminal and get to my folders. I've restarted several times with no results. So I went online and looked at possible solutions. The following solution is what I've tried. 

sudo apt-get with ubuntu-desktop and purge nvidia* 


The biggest problem is that I can't run it. I can't get to a terminal if I log onto my account, so I restarted and tried from safe mode dropping into the root shell, but that wouldn't let me run it either. It says something about being read only. I'm really stuck, and I can't find any resources online. What can I do short of reinstalling the entire operating system?

---

### Post by lisati on 2015-12-17
Are you running 14.04 or 14.10?

---

### Post by justin76 on 2015-12-17
14.04 LTS. As far as I know, I haven't downloaded any updates the last few days.

---

