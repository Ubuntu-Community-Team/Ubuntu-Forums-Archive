---
title: "ssh-keygen - Permission denied"
date: 2016-03-07
forum: General Help
---

### Post by marchello_lippi2 on 2016-03-07
Hi all, 

I'm about to create private and public keys using ssh-keygen. 
Honestly I do not remember what I tried to do previously. 
This is one-person pc. 

$ ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/home/user1/.ssh/id_rsa): 
/home/user1/.ssh/id_rsa already exists.
Overwrite (y/n)? y
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
open /home/user1/.ssh/id_rsa failed: Permission denied.
Saving the key failed: /home/user1/.ssh/id_rsa.

How do I resolve it? 

$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:        14.04
Codename:       trusty

---

### Post by SeijiSensei on 2016-03-07
Make sure the directory /home/user1/.ssh and the files it contains are writable by user1.

---

### Post by marchello_lippi2 on 2016-03-07
[COLOR=#DD4814][COLOR=#000000][SeijiSensei]("http://ubuntuforums.org/member.php?u=698195"),[/COLOR][/COLOR][COLOR=#000000] [/COLOR] 

I tried 

$ sudo chown user1:user1 /home/user1/.ssh -R

but after that the same error appear. 
What else should I do to make sure [COLOR=#000000]the directory /home/user1/.ssh and the files it contains are writable by user1 ?[/COLOR]

---

### Post by SeijiSensei on 2016-03-07
I don't know why that doesn't work.  You could delete the id_rsa* files and start from scratch.

---

### Post by marchello_lippi2 on 2016-03-07
[COLOR=#DD4814][COLOR=#000000][SeijiSensei]("http://ubuntuforums.org/member.php?u=698195"),[/COLOR][/COLOR][COLOR=#000000] [/COLOR]

[COLOR=#000000]It works now, thanks for help.[/COLOR]

---

