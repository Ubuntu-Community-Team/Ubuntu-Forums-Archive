---
title: "trying to execute a terminal command automatically"
date: 2008-05-21
forum: General Help
---

### Post by cclofton on 2008-05-21
Hi there, I've been using and loving ubuntu now for a few months, and I decided to try installing kubuntu on an old laptop. All is fine, except that thunar cannot browse over ssh, so, I've set up fuse, and by running the following command...
sshfs my_username@192.168.1.82:/home/my_username/ /media/mountpoint
everything works beautifully - I can browse and edit my home directory on my other pc just fine. 

So, all I want to do is get this command to run automatically, but nothing seems to work. I have searched everywhere. I have tried putting it in the commands to run automatically on startup - doesn't work. I've tried writing a bash script that I can execute by just double clicking- doesn't work. I've tried creating a launcher on the panel with this exact command - it comes up in the terminal, asks for a password, then disappears having not mounted it. 

So, what I really want to know is what the difference is between manually entering the command in the terminal, and creating a launcher or adding it to the list of programs to execute at startup. Why won't it work? 

By the way, I took the instructions and the command from: 
[http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/](http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/)
and the attempt to automate it from comment 82 - but it didn't work

Thanks in advance if you can help

---

### Post by bingoUV on 2008-05-21
Using passwordless authentication should be easier. Try [http://sial.org/howto/openssh/publickey-auth/](http://sial.org/howto/openssh/publickey-auth/).

---

