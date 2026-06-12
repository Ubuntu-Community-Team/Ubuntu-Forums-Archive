---
title: "How to make the ''ask for password' pops up when using scp to copy to remote server"
date: 2018-06-14
forum: General Help
---

### Post by liweitt on 2018-06-14
Hi,
I'm trying to copy file between two 'Ubuntu Server 16.04 LTS' servers(Ubuntu1,Ubuntu2).
I used putty to connect Ubuntu1(I'm new to Linux...I think i'm using SSH, i loaded the private key and connected the server)

Here are the commands i used, the ''ask for password' didn't pop up and the copy failed.

root@Ubuntu1:~# cd /var/opt/mssql/data
root@Ubuntu1:/var/opt/mssql/data# scp dbm_certificate.* root@Ubuntu2:/var/opt/mssql/data/
Permission denied (publickey).
lost connection


Any suggestions would be appreciated.

---

### Post by deadflowr on 2018-06-14
Where was the private key loaded to?
You want to copy the public key from the client (putty) to the server.
never copy the private key.

---

### Post by Dennis N on 2018-06-14
Check out **gigolo** for Ubuntu to Ubuntu file operations. It's in Software. 
[https://www.maketecheasier.com/manage-remote-filesystems-with-gigolo/](https://www.maketecheasier.com/manage-remote-filesystems-with-gigolo/)
Uses password authentication by default.

---

### Post by liweitt on 2018-06-14
The private key was a file that i loaded into putty and then connected the Ubuntu1.

What is copy the 'public key'?

---

### Post by deadflowr on 2018-06-14
Keys are generated in pairs.
One private one public.
The public key is what you need to upload to the server
While the private is kept safe on your client.
Some basics here:
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys")

---

### Post by liweitt on 2018-06-14
Thanks Guys,

resolved by running following command on Ubuntu2
sudo sed -i "/PasswordAuthentication no/c\PasswordAuthentication yes" /etc/ssh/sshd_config
sudo sed -i "/PermitRootLogin prohibit-password/c\PermitRootLogin yes" /etc/ssh/sshd_config
sudo systemctl reload sshd.service

---

### Post by deadflowr on 2018-06-14
What works works, right?
If that solution worked for you, you can [mark this thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") if you wish.

---

