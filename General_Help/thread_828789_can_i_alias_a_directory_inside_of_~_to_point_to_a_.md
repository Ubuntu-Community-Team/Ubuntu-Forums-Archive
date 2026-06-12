---
title: "can i alias a directory inside of ~/ to point to a ftp server?"
date: 2008-06-14
forum: General Help
---

### Post by kraymore on 2008-06-14
is it possible for me to create a directory inside my home directory that will link to space on a web server accessed by ftp with a username and password ?

i thought this might be a good way to backup very important files externally.  

thanks

---

### Post by bingoUV on 2008-06-14
Possible. It is not called aliasing, but mounting the remote filesystem locally. See curlftpfs [http://curlftpfs.sourceforge.net/](http://curlftpfs.sourceforge.net/). See if you can find it in add/remove programs.

---

### Post by niteshifter on 2008-06-14
@bingoUV: Thank you! I've been symlinking scripted gFTP commands to do this. I should get out more often ;)

@kraymore: Encrypting such stuff is recommended. You're not the only one with access. GPG / Seahorse is one easy solution.

---

### Post by kraymore on 2008-06-14
i'm a little confused about what my curlftpfs /etc/fstab entry ought to be

this is the example the curlftpfs says for /etc/fstab

curlftpfs#ftp.host.com /mnt/host fuse rw,uid=500,user,noauto 0 0

i am unsure how to change that to include a login and password.  

its also unclear if its possible to do the ftp through ssh which is installed on the server i am accessing.  

also would be default user belong to the fuse group by default ?  

thanks to the reply poster, it works great.  i've just got to iron out this part now.

---

### Post by bingoUV on 2008-06-14
Use sshfs then : [http://fuse.sourceforge.net/sshfs.html](http://fuse.sourceforge.net/sshfs.html)
You can setup ssh keys as in [http://pkeck.myweb.uga.edu/ssh/](http://pkeck.myweb.uga.edu/ssh/) so that you do not need to enter a password. I don't know how to make fstab entry. If all else fails, you can put the sshfs command in /etc/rc.local so that it runs at every boot time even if there is no fstab entry.

---

### Post by kraymore on 2008-06-14
hmm..  not sure if sshfs is what i need.  i dont admin the webserver i'd be backing up my files at so i can't do anything on that box other than ftp.  i was hoping i could make use of my SSL certificate on the webserver for ftp sessions, but that is not a requirement, more a luxury.  i will see about getting help with the /etc/fstab entry for the curlftpfs filesystem.

---

### Post by bingoUV on 2008-06-14
You don't need to admin the server to use sshfs. As you mentioned in the last post, ssh is installed on the server, and you wanted to do ftp through ssh. Sshfs is capable of doing this, though it might be wrong to call it doing ftp over ssh.

---

### Post by kraymore on 2008-06-15
i did not say my web server had SSH.  i said it had SSL.  i will find out though since it sounds like sshfs would be better.  

i got it working 

my fstab entry looks like this

curlftpfs#myuserlogin:mypassword@www.mywebsite.com/public_html /home/user/mount fuse rw,allow_other,uid=1000,user,noauto 0  0

after i reboot it requires a simple

sudo mount /home/user/mount

before anything will see it

--

what i'm not liking is curlftpfs will cause my ~/ directory to stall upon listing or viewing the contents.  nautilus or ls -al wont advance at all.  i'm thinking thats because the mount point is inside my /home directory.  i will change that.  whatever is happening its definitely curlftpfs

---

### Post by bingoUV on 2008-06-15
> **kraymore said:**
> 
its also unclear if its possible to do the ftp through ssh which is installed on the server i am accessing.


> **kraymore said:**
> i did not say my web server had SSH.  i said it had SSL.


Anyway. I have used ftpfs (in the good old LUFS days, 5-6 years ago) and it used to stall ls etc. It should be fine if you mount it inside a directory one level deep in your home. Anywhere in /media would also be fine.

---

