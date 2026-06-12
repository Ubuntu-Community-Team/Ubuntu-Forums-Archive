---
title: "Disappearing files/cannot delete files/weird inodes problem..."
date: 2013-09-19
forum: General Help
---

### Post by john105 on 2013-09-19
Hi all,

I have a lovely new web development environment set up here, but unfortunately I had to reboot into Windows to use a particular program - after reboot some files were missing from a virtualhost where I had installed Wordpress. I discovered this because of PHP errors when accessing localhost.

I went ahead and reinstalled Wordpress which worked fine. I then had to reboot again for the same (irrelevant) reason. The 'latest.tar.gz' I downloaded and the 'wordpress' directory it extracted to are now undeletable; rm returns the message "no such file or directory" even though 'ls -al' clearly shows them. Also the 'wordpress' directory has lost it's 'd' flag in the permissions.

Running 'ls -il' shows the file and directory have inodes 68 and 69 respectively... those are weird inodes aren't they? Could this be diagnosic?

I have two SSDs in the machine but the web root is not on either of them. It is on a regular old spinning hard disk. Windows is set up to accelarate that disk using one of the SSDs but we're not booting Windows here so that shouldn't matter... unless the corrruption happened because I booted Windows NOT because I REbooted Ubuntu...

Any help much appeciated!

tldr; Files disappear. Can't delete files. What's going on? And what does inode 68/69 mean?

J

---

