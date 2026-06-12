---
title: "Apache won't list symlinks or give access to them"
date: 2008-06-01
forum: General Help
---

### Post by Funzo22 on 2008-06-01
I have used apache2 on every version of ubuntu, it has been great I always do 'ln -s /home/dustin/Httpd /var/www/Shared' and then I'm good to go to share my Httpd folder, 

recently I reinstalled ubuntu (although I didn't touch my /home partition) and now apache2 won't show the symlink at all, I made sure all my permissions are 777 for the folder I want to share and the /var/www folder. 

The symlinks just don't show up at all in the directory listing, however directories and files that are actually in /var/www DO show up... weird huh? I attatched my config and I'm hoping someone can help me out


Thanks in advace

Edit: I also should note that when I try and go to the /Shared folder of the server manually, I get a "You don't have permission to access /Shared on this server." error

---

### Post by luke16 on 2008-07-05
I also have this problem. Gave permissions to the link, the link target, and the parent directory. Apache still ignores everything.

---

