---
title: "Rsync over SSH"
date: 2013-07-15
forum: General Help
---

### Post by asai on 2013-07-15
Hi, 

I am trying to set up a backup to my server with the use of rsync and SSH. I have done this before with success, but for some reason I can't get the RSA keys to function.
I am a bit frustrated right now, and hope someone can help...

I have a local machine A and remote machine B. I want to rsync from B to A.
On A I have a script to ssh into B. And for this I need a RSA so I don't need to give a password, because I would like to run this script as a cron job.
From A i generate a rsa pair files and I copy the .pub file to B. But for some reason this doesn't work.
I'm confused... :(

---

### Post by cool110 on 2013-07-15
On the remote machine you need to add the contents of the public key to ~/.ssh/authorized_keys and check it has permissions set to 600.

---

### Post by asai on 2013-07-15
Thanks for your reply, but no change... :(

---

### Post by Lars Noodén on 2013-07-15
Can you log in with plain ssh using your new key pair?  In addition to the permissions above, your public key must be on the remote machine in the file ~/.ssh/authorized_keys, on one single line, whole and unbroken. 

Once you can log in with ssh using the keys, you can try with rsync.  It will need to be told to use the keys.

```

rsync -a -e 'ssh -i /home/asai/.ssh/some_rsa_key' /path/to/src/ *xx.yy.zz.aa*:/path/to/dest/

```

---

### Post by asai on 2013-07-15
No I can't log in with ssh unless I type in my password.

---

### Post by SeijiSensei on 2013-07-15
Delete the file ~/.ssh/authorized_keys on the remote.  Then on the machine where you created the key pair, use the command "ssh-copy-id you@remote_server" and enter your password when prompted.  This creates the .authorized_keys file if it does not exist and copies the public key to it.  See if that fixes the problem.

Rsync uses SSH by default so you don't need to do anything special to implement it.  

Another alternative for password-free rsync transfers is to run rsync in daemon mode on the remote.  Run "man rsyncd.conf" for details.

Remember, too, that if you are using your credentials you will be limited to remote directories where you have write privileges.  If you are doing an extensive backup, you'll probably want to run as root.  You can copy ~/.ssh/authorized_keys on the remote to /root/ssh/.authorized_keys.  Then you can use "root@remote_host" as the target.

---

### Post by ricardoeureka on 2013-07-15
Try following the steps described in this document [http://troy.jdmz.net/rsync/index.html](http://troy.jdmz.net/rsync/index.html)

---

### Post by markbl on 2013-07-15
> **asai said:**
>  .. I want to rsync from B to A. ..

From A i generate a rsa pair files and I copy the .pub file to B. But for some reason this doesn't work. ..


Your problem is that you have this around the wrong way. B is your client, A is your server. You generate the keys on the client and copy the public key to the server (using ssh-copy-id btw).

---

### Post by asai on 2013-07-16
Didn't make any difference... :(
My problem is really that the destination machine runs windows.
I am trying to run backup of my server at home which is a Ubuntu server.
I have cwRsync on the windows machine, and in that package there is the ssh-keygen.
So i thought it was on the win machine the keygen is run and the pub file goes to the server?
I have tried both, with no success.

---

### Post by markbl on 2013-07-16
> **asai said:**
> Didn't make any difference... :(
My problem is really that the destination machine runs windows.
Er, perhaps that was rather a pertinent thing to tell us!?
> 
I am trying to run backup of my server at home which is a Ubuntu server.
I have cwRsync on the windows machine, and in that package there is the ssh-keygen.
So i thought it was on the win machine the keygen is run and the pub file goes to the server?
I have tried both, with no success.
If both machines are just on your local home lan then ssh security is not really a big deal. I use deltacopy (free rsync client/server) on my windows pc and just use rsync directly from linux (i.e. not via ssh).

---

### Post by asai on 2013-07-16
Yes, sorry about the lack of information initally...
The win pc is at my office and the server is at home, so I have to use ssh.

---

### Post by ricardoeureka on 2013-07-16
> **asai said:**
> Yes, sorry about the lack of information initally...
The win pc is at my office and the server is at home, so I have to use ssh.
Well, you really missed "a little" peace of information :D

You will need ssh running on the windows box in oder to make it possible. Check cygwin
[COLOR=#666666][FONT=arial]www.**cygwin**.com/&#8206;
[/FONT][/COLOR]

[COLOR=#444444][FONT=arial]Linux-like environment for Windows making it possible to port software running on POSIX systems (such as Linux, BSD, and Unix systems) to Windows[/FONT][/COLOR]

---

### Post by asai on 2013-07-16
Thanks for your replies. I think I will try another aproach to the case...

---

### Post by steeldriver on 2013-07-16
maybe --> [http://winscp.net/eng/docs/task_synchronize](http://winscp.net/eng/docs/task_synchronize)

---

### Post by HiImTye on 2013-07-17
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
what type of keys does the windows machine make?

---

