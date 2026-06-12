---
title: "Ubuntu Archive Automatic Signing Key"
date: 2007-01-24
forum: General Help
---

### Post by Surgeon General on 2007-01-24
i'm trying to update my dapper but everytime it goes to the security section, i get:

W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

i searched the forums but couldn't find any answer.

how does one fix this?

---

### Post by coldNsunny on 2007-01-27
Hi Surgeon General

I haven't seen that particular error but I have received key errors when updating and it was that I didn't have the repository key in my keyring.  The last half of the large number above is the key number, that is 437D05B5 in your case.  You can check if the key is in your key ring with (as root):
apt-key list

If the key is there I don't know what is up, But if it isn't then you need to get the key and add it to your keyring.  

As root:
gpg --keyserver hkp://subkeys.pgp.net --recv-key 437D05B5
gpg --export --armor 437D05B5 | sudo apt-key add -

I hope this solves your problem. I used the automatic sources list generator at this link: [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
to generate a sources list because I was having trouble with the repositories. In the list are the key numbers and commands to add the keys.
I saw this post on the forums: [http://ubuntuforums.org/showthread.php?t=346705&highlight=gpg+key](http://ubuntuforums.org/showthread.php?t=346705&highlight=gpg+key)
and when I tried this link: [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) Firefox downloaded the key to the desktop, I tried the same method with other repositories and I wasn't successful.  A post by someone more knowledgeable about obtaining the keys would be great - anyone?
I hope this helps.

---

### Post by Surgeon General on 2007-01-27
hi, i tried your suggestions and i still keep getting the error message. strange this dapper was installed from the official CD. maybe i should contact the ftpmaster since all seems to fail.

---

### Post by Surgeon General on 2007-01-27
some update. i tried including all keys of the ftpmaster to my dapper but i still get the same error message. most of the links i found in this forum that is having a similar issue like mine suggests getting the keys. i tried it but i'm still unable to get that error message erased.

any help is appreciated.

---

### Post by coldNsunny on 2007-01-27
Hi SG,
Did you get a new sources list from source-o-matic, and try that?  (Back up your current sources.list first, it should be in /etc/apt/) Perhaps it is a problem with the repository you are accessing.  If you still can't update from a different repository then it suggests the problem is with something in your set up.

---

### Post by Surgeon General on 2007-01-28
> **coldNsunny said:**
> Hi SG,
Did you get a new sources list from source-o-matic, and try that?  (Back up your current sources.list first, it should be in /etc/apt/) Perhaps it is a problem with the repository you are accessing.  If you still can't update from a different repository then it suggests the problem is with something in your set up.

hi, yes i used a fresh sources.list from your post (and was using the stock sources.list). did also all those copying of the gpg keys. :(

geez, i hate to reinstall.

thanks for the replies.

---

### Post by Surgeon General on 2007-01-28
just want to let those who follow this thread, my problem has been fixed. apparently the gpg key at security.ubuntu.com has been updated judging from the timestamp. so i did a "sudo apt-get update" and no errors!

---

### Post by coldNsunny on 2007-01-28
Hi SG,
That's good news.  After your post about not wanting to reinstall, I did a bit of googling and found a problem others were talking about in the Debian repositories and it turned out the key for the repository was changed.  I came back here to find that that was the problem for you too.  Good thing you didn't go through all the work of reinstalling.
Take care.

---

