---
title: "ssh script"
date: 2007-08-11
forum: General Help
---

### Post by melojo on 2007-08-11
Hello,

can anyone point me in the right direction on creating a script to login to another machine via ssh and start vmware, virtual xp server and run games or other progams via xp.  I hope this makes sense.  What I am wanting to do is create a shortcuts on my daughters ubuntu machine so she can run some xp apps from my ubuntu machine making it as easy as possible for her.  I have ssh working and have done this manually but I am wanting to automate the process.

---

### Post by kidders on 2007-08-12
Hi there,

You may not need much of a script to do this sort of thing, provided there would be no reason to acquire root privileges on a remote box. Check out SSH's man page for details on executing commands on remote machines.

You may have figured this out already, but you can replace password-based authentication with key-based authentication, allowing you to use SSH to invoke remote processes non-interactively (assuming the private key you use is unencrypted). The goal would be to at least manage to run a test on the remote host with a single command, without having to type any password, so you could turn it into a desktop shortcut or something. For instance...```
ssh melojo_box uname -a
```Once you get that far, that's half the battle.

Another possible approach would involve running a web server on the host machine ... something that's certainly worth considering if you already have a web server on it for some other reason. Your daughters could then visit a web page, and click the applications they wanted to start up, but I won't go down that road, unless you want me to. It's a little off topic.

I hope that helps.

---

### Post by HermanAB on 2007-08-12
$ ssh herman@servername
Password: whatever
$ sudo vmware

BTW, you won't be playing games on VMware, it is slow.  However, it works and I prefer things that are slow and reliable to things that are fast and unreliable, but that doesn't work with games...

---

### Post by melojo on 2007-08-13
Thanks for the replies!!!
The only games that would be played in this manner is hoyle card & puzzle and monopoly and all seem to work fine.  I made a small script but I have to enter a password when it asks I will add the password: option to it.  Is their a way to have the XP vertial machine to start also.  Vmware starts but then I have to click to start XP:)

---

### Post by melojo on 2007-08-14
Hello all,

I could not  get ssh to accept a password from a script and found this on the net [http://wiki.met.tamu.edu/index.php?title=SSH_Logins_Without_Providing_a_Password](http://wiki.met.tamu.edu/index.php?title=SSH_Logins_Without_Providing_a_Password) and got it to auto login useing authrized keys.  Hope this helps if anyone else wants to auto login through ssh.

---

### Post by HermanAB on 2007-08-14
SSH will not accept a password from a script.  That is done by design.  In order to log in without a password, you have create a public/private key pair, then upload the public key to the server authorized_keys file.  Some Googling will get you going.

---

### Post by vtechstu on 2007-09-18
I'm sorry to drudge up an old post, but I'm not having much luck with getting this working.  I followed the steps in the link above [ssh login without password]("http://wiki.met.tamu.edu/index.php?title=SSH_Logins_Without_Providing_a_Password")

but when I ssh to the machine, it tried all authentication methods, then gives a permission denied (publickey). 

Any ideas?  Thanks!

---

### Post by vtechstu on 2007-09-21
Problem solved...I was using the wrong user to log in with, and root account was diabled.  Thanks anyway to anyone who looked.

---

