---
title: "Understanding 'ssh'"
date: 2014-07-20
forum: General Help
---

### Post by delanov on 2014-07-20
Ubuntu shows the following when directory SSH is open.  I'm having a hard time understanding if SSH is set up correctly. Please take a look at the following and tell me if it looks right.  Gratefully confused.

ddval@ddval-p6653w:/etc/ssh$ ls
moduli            ssh_host_dsa_key.pub    ssh_host_ed25519_key.pub
ssh_config        ssh_host_ecdsa_key      ssh_host_rsa_key
sshd_config       ssh_host_ecdsa_key.pub  ssh_host_rsa_key.pub
ssh_host_dsa_key  ssh_host_ed25519_key    ssh_import_id

---

### Post by bapoumba on 2014-07-20
*Thread moved to **General Help**.*

---

### Post by Lars Noodén on 2014-07-20
It looks like you have openssh-server installed and that you are displaying the contents of the directory /etc/ssh  The list of filenames seems ok.  You can see more of a description of the files looking in the manual page for [sshd](http://manpages.ubuntu.com/manpages/trusty/en/man8/sshd.8.html)

---

### Post by delanov on 2014-07-20
Thanks for: manual page for sshd

---

### Post by Lars Noodén on 2014-07-20
If you want to see the official descriptions of the files in ~/.ssh/ then those are in the manual page for [ssh](http://manpages.ubuntu.com/manpages/trusty/en/man1/ssh.1.html).

---

### Post by delanov on 2014-07-20
> **Lars Noodén said:**
> If you want to see the official descriptions of the files in ~/.ssh/ then those are in the manual page for [ssh](http://manpages.ubuntu.com/manpages/trusty/en/man1/ssh.1.html).

Just finished reading your last link:  sshd — OpenSSH SSH daemon.  Now onto the next reading:  official descriptions of the files in ~/.ssh/

For the inexperienced, such as myself, mighty heavy stuff.  And to think all I want is:  Ubuntu in the family room ssh Mint in the laundry room:-)

---

### Post by Lars Noodén on 2014-07-20
The manual pages vary in quality, but the openssh ones are pretty good.   They won't make sense all at once, but they're worth checking to see what does make sense.  If you want to see more than you wanted to know about the configuration of either the client or the server, check out the pages for ssh_config or sshd_config.

---

### Post by delanov on 2014-07-20
> **Lars Noodén said:**
> The manual pages vary in quality, but the openssh ones are pretty good.   They won't make sense all at once, but they're worth checking to see what does make sense.  If you want to see more than you wanted to know about the configuration of either the client or the server, check out the pages for ssh_config or sshd_config.

Well I've invested many days and many nights trying to SSH, and I accomplished very little towards SSH-ing, however, I've gained knowledge about the Linux file system and that is very satisfying.  I continue on the path of SSH until I can SSH:-)

---

### Post by Lars Noodén on 2014-07-20
Ok.  It's pretty simple.  Just put openssh-server onto the machine you want to log into and then use ufw to open up the right port (22) if you have the firewall activated.

---

### Post by delanov on 2014-07-20
> **Lars Noodén said:**
> Ok.  It's pretty simple.  Just put openssh-server onto the machine you want to log into and then use ufw to open up the right port (22) if you have the firewall activated.

I typed ufw at the command line and disabled the firewall on both machines.  I did this and was finally able to ftp between machines.  The firewalls remain down on both machines.  I'll enable both firewalls and open port (22) on bot machines.  BTW when I checked both ssh config files i.e. (user and world) port (22) is preceded by #

---

### Post by Lars Noodén on 2014-07-20
[SFTP](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp) is built into openssh-server, so you can transfer files securely.  The file manager can support SFTP, too.  Press ctrl-L and then *sftp://xx.yy.zz.aa*, using the ip address for the second server.  Of course if you are used to Filezilla, that can do SFTP too.

---

### Post by delanov on 2014-07-20
> **delanov said:**
> I typed ufw at the command line and disabled the firewall on both machines.  I did this and was finally able to ftp between machines.  The firewalls remain down on both machines.  I'll enable both firewalls and open port (22) on bot machines.  BTW when I checked both ssh config files i.e. (user and world) port (22) is preceded by #

openssh-server and openssh-client are installed on mint and ssh is installed ubuntu.  I typed ssh IP# at mint and the cursor blink for about two minutes and timed out.

Typed ssh IP at ubuntu and get this  the following:

ddval@ddval-p6653w:~$ ssh 192.168.x.xx
ssh: connect to host 192.168.x.xxx port 22: No route to host

---

### Post by Lars Noodén on 2014-07-20
If the firewall is turned opened for SSH,

```

sudo ufw allow ssh

```

then you should be able to connect if you are on the same LAN.

Can you ping the machines from each other?

```

ping -c 3 -w 1 192.168.x.xx

```

That checks basic connectivity.  They are on the same LAN, right?

---

### Post by 1clue on 2014-07-20
You're having trouble right?

You might have a permissions issue.

Type this on each computer as the relevant user for each one:

```

ls -al ~/.ssh/

```

Your ~/.ssh directory and all its contents should be owned by you and writable by you.  Your id_dsa file must be -rw---------.  Your id_dsa.pub and authorized_keys and known_hosts should be -rw-r--r--.

---

### Post by delanov on 2014-07-20
> **Lars Noodén said:**
> If the firewall is turned opened for SSH,

```

sudo ufw allow ssh

```

then you should be able to connect if you are on the same LAN.

Can you ping the machines from each other?

```

ping -c 3 -w 1 192.168.x.xx

```

That checks basic connectivity.  They are on the same LAN, right?

Both machines ping and they are on the same Lan.  The firewall is down on both machines and port 22 is open on both machines.

***_I'm on the Mint machine and I  SSH Local 127.0.01  and I get the following:_***
wayne@wayne-15395 ~ $ ssh 127.0.0.1
wayne@127.0.0.1's password: 
Welcome to Linux Mint 11 Katya (GNU/Linux 2.6.38-16-generic i686)
Welcome to Linux Mint
 * Documentation:  [http://www.linuxmint.com](http://www.linuxmint.com)
Last login: Sat Jul 19 10:01:00 2014 from localhost

***_I'm on the Mint machine and SSH its IP 192.168.X.XXX_***
****wayne@wayne-15395~ $ ssh 192.168.X.XXX
The authenticity of host '192.168.X.XXX (192.168.X.XXX)' can't be established.
ECDSA key fingerprint is fb:6X:0X:bX:fX:6X:fc:6X:6X:6X:5X:9X:2a:0f:1X:dX.
Are you sure you want to continue connecting (yes/no)?  I type "yes" and I get the following:

Warning: Permanently added '192.168.X.XX' (ECDSA) to the list of known hosts.
Write failed: Broken pipe.

So I'm just SSH-ing the mint machine.

I have not checked the permissions on the files on this (MInt) machine.  I wanted to get your input on the output of these SSH attempts.

---

### Post by delanov on 2014-07-20
> **1clue said:**
> You're having trouble right?

You might have a permissions issue.

Type this on each computer as the relevant user for each one:

```

ls -al ~/.ssh/

```

Your ~/.ssh directory and all its contents should be owned by you and writable by you.  Your id_dsa file must be -rw---------.  Your id_dsa.pub and authorized_keys and known_hosts should be -rw-r--r--.

Here are the permissions.  AND it looks like I missed a step because I don' have id_dsa nor do I have an authorized keys file.  I believe I know how to correct this.  On the other machine (Ubuntu 14.04) I've been though this so I think I'm alright there.  thanks for jumping in with the heads up:-)

wayne@wayne-153952~ $ ls -al ~/.ssh/
total 20
drwx------  2 wayne wayne 4096 2014-07-18 09:40 .
drwxr-xr-x 70 wayne wayne 4096 2014-07-20 14:54 ..
-rw-------  1 wayne wayne 1766 2014-07-18 16:22 id_rsa
-rw-r--r--  1 wayne wayne  408 2014-07-18 16:22 id_rsa.pub
-rw-r--r--  1 wayne wayne  888 2014-07-20 15:27 known_hosts

---

### Post by delanov on 2014-07-20
Here's what the ~/.ssh directory looks like:

wayne@wayne-15395200001085 ~/.ssh $ ls -al
total 32
drwx------  2 wayne wayne 4096 2014-07-20 16:19 .
drwxr-xr-x 70 wayne wayne 4096 2014-07-20 14:54 ..
-rw-r--r--  1 wayne wayne  616 2014-07-20 16:19 authorized_keys2
-rw-------  1 wayne wayne  751 2014-07-20 16:12 id_dsa
-rw-r--r--  1 wayne wayne  616 2014-07-20 16:12 id_dsa.pub
-rw-------  1 wayne wayne 1766 2014-07-18 16:22 id_rsa
-rw-r--r--  1 wayne wayne  408 2014-07-18 16:22 id_rsa.pub
-rw-r--r--  1 wayne wayne 1110 2014-07-20 16:23 known_hosts

My new question is: How do I get this pub key to the other computer when I cannot connect to the computer.  Or do I need to??

When I SSH from either computer to the other it wants a password. I type in the pass word I use to log into the computer with ip 192.168.x.xxx, and I get the following response.  What can be changed to get rid of this password thing.

wayne@wayne-15395 ~ $ ssh 192.168.x.xxx
[email]wayne@192.168.x.xxx[/email]'s password: 
Permission denied, please try again.

---

### Post by billdozor on 2014-07-20
From my understanding, you are wanting to setup password-less SSH login with pub/private keys.

To do this:

[COLOR=#000000][COLOR=#444444]From the local client:[/COLOR][/COLOR]
1) Create public/private key pair

```
ssh-keygen -t rsa



Enter file to save the key (Enter for default).
Enter password twice to encrypt key pair.


```

Two files are created:

[LIST]
[*]$HOME/.ssh/id_rsa = private key (do not share) 
[*]$HOME/.ssh/id_rsa.pub = public key (this will go on server) 
[/LIST]


2) Put public key on remote server(s)

```
ssh-copy-id -i $HOME/.ssh/id_rsa.pub username@server



```

If ssh-copy-id is not installed, use scp instead:
```
scp $HOME/.ssh/id_rsa.pub username@server:~/tmp.pub

ssh username@server

cat $HOME/tmp.pub >> .ssh/authorized_keys
rm tmp.pub


```

3) Ensure ssh-agent is running and add private key passphrase

```
eval $(ssh-agent)

ssh-add


```
Enter private key passphrase to add private key to the ssh-agent.


4) Login to server, no password prompt because of ssh-agent/ssh-add
```
ssh username@server
```



*Note: You will have to run ssh-add one time for each session you are logged in to. There are GUI ssh-add programs available that will prompt you for the private key password upon login to the desktop. (Not sure of the name off the top of my head)

---

### Post by delanov on 2014-07-20
I can FTP between the two machines, however when I SSH a password is requested which I do not have ???

I suppose you call tell I'm becoming UN-hinged over this because I keep repeating myself:lolflag:

---

### Post by delanov on 2014-07-20
Thanks billdozer.  As soon as I can work through the items from your post I'll post the results:-)

---

### Post by 1clue on 2014-07-20
I don't think you have an ssh problem anymore.  It looks like a networking issue or a remote host problem.

Check your netmask for each box, and also check your gateway.

**ifconfig** will get you network information,

**netstat -rn** will get you routing information.

---

### Post by delanov on 2014-07-20
> **1clue said:**
> I don't think you have an ssh problem anymore.  It looks like a networking issue or a remote host problem.

Check your netmask for each box, and also check your gateway.

**ifconfig** will get you network information,

**netstat -rn** will get you routing information.

I think I'm alright on both ifconfig and netstat.

Thanks for the post.

---

### Post by Lars Noodén on 2014-07-21
> **delanov said:**
> I can FTP between the two machines, however when I SSH a password is requested which I do not have ???

[FTP](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp) is a different service and uses different daemons from SSH.  SFTP works over SSH.  Can you use SFTP to connect or does that give an error, too?

```

sftp 192.168.x.xx

```

---

### Post by delanov on 2014-07-21
> **Lars Noodén said:**
> [FTP](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp) is a different service and uses different daemons from SSH.  SFTP works over SSH.  Can you use SFTP to connect or does that give an error, too?

```

sftp 192.168.x.xx

```

[B][I]When I sftp local machine 'ddval', which I'm logged onto, I'm able to connect when I type in the machines log in password.
[/I][/B]
ddval@ddval-p6653w:~$ sftp 192.168.x.xxx
The authenticity of host '192.168.x.xxx (192.168.x.xxx)' can't be established.
ECDSA key fingerprint is 48:2c:85:78:15:21:da:79:71:0d:fa:a8:x.x.x.x.x
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '192.168.1.105' (ECDSA) to the list of known hosts.
[email]ddval@192.168.x.xxx[/email]'s password: 
Connected to 192.168.x.xxx.
sftp> ls
Desktop             Documents           Downloads           Music               
Pictures            Public              Templates           Videos              
deja-dup            examples.desktop    
sftp> 


[B][I]When I sftp Local 127.0.x.x I get the same as above:
[/I][/B]

When I ping the remote machine the two machines are connected. 

When I sftp to remote machine 'ddval' from local machine 'wayne  I'm ask for a password for 'wayne' by the remote machine 'ddval'. 

When I sftp to remote machine 'wayne' from local machine 'ddval'  I'm ask for a password for 'ddval'  by the remote machine 'wayne'. 

It appears that I need to establish a password for wayne on the ddval machine and a password for ddval on the wayne machine ???

Thanks for the post.

---

### Post by Lars Noodén on 2014-07-21
> **delanov said:**
>  What can be changed to get rid of this password thing.

wayne@wayne-15395 ~ $ ssh 192.168.x.xxx
[email]wayne@192.168.x.xxx[/email]'s password: 
Permission denied, please try again.

Do you have different account names on the two machines? You can specify a different user on the remote machine:
```

wayne@wayne-15395 ~ $ ssh **ddval**@192.168.x.xxx

```

Otherwise it will default to trying to log in with the user name of the local machine's current account.  That name may not exist on the other machine.  If it doesn't, then the server will give you a permission denied error like above without giving a clue about whether the username or password were wrong.  

The broken pipe error is something else though.

---

### Post by delanov on 2014-07-21
> **Lars Noodén said:**
> Do you have different account names on the two machines? You can specify a different user on the remote machine:
```

wayne@wayne-15395 ~ $ ssh **ddval**@192.168.x.xxx

```

Otherwise it will default to trying to log in with the user name of the local machine's current account.  That name may not exist on the other machine.  If it doesn't, then the server will give you a permission denied error like above without giving a clue about whether the username or password were wrong.  

The broken pipe error is something else though.

Yes there are different accounts on the two machines:

ddval@ddval-p6653w:~$  Ubuntu machine

wayne@wayne -15395 ~ $ Mint machine

OK - I type this for my records -->>  From Ubuntu type ->>  ddval@ddval-p665w.~$ ssh [email]wayne@192.168.x.xxx[/email].  Then use password for wayne, and after password is accepted, I'm logged onto wayne machine and command line of terminal becomes command line for wayne machine.

I used the above synopsis and it worked lik a charm :-)

I'm blown away by realization SSH-ing between the two machines boiled down to different account names :rolleyes:

So now I'm SSH-ing between two home bound computers with all firewalls down and ports 20, 21 and 22 open.  

When I SSH to Launchpad or Git, as well as other sites, I'll need to activate pair keys id_rsa and id_rsa.pub.  I've created keys on both machines and key data  reside at ~/.ssh, and the folder /etc/ssh.  I'm not sure if the data in the folders are all I need to make this happen.

I can provide copy of folders ~/.ssh and /etc/ssh for each machine if you want to take al look.


My total appreciation for all the help from all the posters cannot be put into type.  Thank you all. =d>

---

### Post by Lars Noodén on 2014-07-21
Great!

> **delanov said:**
> When I SSH to Launchpad or Git, as well as other sites, I'll need to activate pair keys id_rsa and id_rsa.pub.  I've created keys on both machines and key data  reside at ~/.ssh, and the folder /etc/ssh.  I'm not sure if the data in the folders are all I need to make this happen.

By the way, when you make the keys with [ssh-keygen](http://manpages.ubuntu.com/manpages/trusty/en/man1/ssh-keygen.1.html)  you can give the keys names which are easier to remember and use comments within the keys to keep them sorted.  

```

cd ~/.ssh/
ssh-keygen -t rsa -b 4096 -f launchpad_id_rsa -C "for launchpad"
ssh-keygen -t rsa -b 4096 -f git_id_rsa -C "git"

```

Whatever you put after **-C** will end up in the comment field in the public key (on the end of the line).  It makes a difference if you have more than one or two keys for a while so you can remember which one is which.  Usually personal keys go in ~/.ssh/ but you can keep them anywhere in your home directory or a sub folder there.  Probably it is best if the private ones are in private folders, like ~/.ssh/ defaults to.

---

### Post by delanov on 2014-07-21
Thank you Lars your help is greatly appreciated:D

---

### Post by delanov on 2014-07-21
> **billdozor said:**
> From my understanding, you are wanting to setup password-less SSH login with pub/private keys.

To do this:

[COLOR=#000000][COLOR=#444444]From the local client:[/COLOR][/COLOR]
1) Create public/private key pair

```
ssh-keygen -t rsa



Enter file to save the key (Enter for default).
Enter password twice to encrypt key pair.


```

Two files are created:

[LIST]
[*]$HOME/.ssh/id_rsa = private key (do not share) 
[*]$HOME/.ssh/id_rsa.pub = public key (this will go on server) 
[/LIST]


2) Put public key on remote server(s)

```
ssh-copy-id -i $HOME/.ssh/id_rsa.pub username@server



```

If ssh-copy-id is not installed, use scp instead:
```
scp $HOME/.ssh/id_rsa.pub username@server:~/tmp.pub

ssh username@server

cat $HOME/tmp.pub >> .ssh/authorized_keys
rm tmp.pub


```

3) Ensure ssh-agent is running and add private key passphrase

```
eval $(ssh-agent)

ssh-add


```
Enter private key passphrase to add private key to the ssh-agent.


4) Login to server, no password prompt because of ssh-agent/ssh-add
```
ssh username@server
```



*Note: You will have to run ssh-add one time for each session you are logged in to. There are GUI ssh-add programs available that will prompt you for the private key password upon login to the desktop. (Not sure of the name off the top of my head)

[B][I][U]Please note: To make this work I CD ~/.ssh.
[/U][/I][/B]
[email]ddval@ddval-p6653w:~/.ssh[/email]$ ssh-copy-id -i id_rsa.pub [email]wayne@192.168.x.xxx[/email]
The authenticity of host '192.168.x.xxx (192.168.x.xxx)' can't be established.
ECDSA key fingerprint is fb:65:01:b6:fa:6e:fc:61:67:60:59
Are you sure you want to continue connecting (yes/no)? yes
/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
/usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys
[email]wayne@192.168.x.xxx[/email]'s password: 

Number of key(s) added: 1

Now try logging into the machine, with:   "ssh 'wayne@192.168.x.xxx'"
and check to make sure that only the key(s) you wanted were added.

[email]ddval@ddval-p6653w:~/.ssh[/email]$ ssh [email]wayne@192.168.x.xxx[/email]
Agent admitted failure to sign using the key.
[email]wayne@192.168.x.xxx[/email]'s password: 
Welcome to Linux Mint 11 Katya (GNU/Linux 2.6.38-16-generic i686)

Welcome to Linux Mint
 * Documentation:  [http://www.linuxmint.com](http://www.linuxmint.com)

Last login: Mon Jul 21 12:29:21 2014 from ddval-p6653w.local
wayne@wayne-15395200001085 ~ $ cd ~/.ssh
wayne@wayne-15395200001085 ~/.ssh $ ls
authorized_keys

---

### Post by delanov on 2014-07-21
What does it imply:  Agent admitted failure to sigh using the key??

---

### Post by delanov on 2014-07-21
billdozer - I completed all of your suggestions and everything works.  I can now ssh between Ubuntu and Mint without using a password.  Thank you:-)

---

### Post by delanov on 2014-07-21
bildozer - I'm told to check 'Authorized_keys' to make sure only the key wanted was transferred.  I've tried Leafpad and gedit as root and the file won't open???

Well I mentioned I was unhinged from all of this:lolflag:  

Of course the proper way is:  cat authorized_keys to see inside :oops:

---

### Post by gordintoronto on 2014-07-22
Does your SSH server have a static IP address? That would make things a lot simpler.

You might find it easier to install putty on the client, and use that to access the server.

---

### Post by delanov on 2014-07-22
> **gordintoronto said:**
> Does your SSH server have a static IP address? That would make things a lot simpler.

You might find it easier to install putty on the client, and use that to access the server.

Non-static ip address

I'll install putty and give it a try.  However, with much help from the forum I'm now SSH-ing, and things "for now" are moving smoothly.  I'm on a new quest to understand Launchpad:confused:

Thanks form the post.

---

### Post by 1clue on 2014-07-22
From ssh:
cat ~/.ssh/authorized_keys*

There are two possible files:  authorized_keys and authorized_keyst2.  authorized_keys2 is deprecated but still functional.

Each is a list of public keys allowed to login as you.  Each key is a single long line, which probably wraps.

---

### Post by delanov on 2014-07-22
> **1clue said:**
> From ssh:
cat ~/.ssh/authorized_keys*

There are two possible files:  authorized_keys and authorized_keyst2.  authorized_keys2 is deprecated but still functional.

Each is a list of public keys allowed to login as you.  Each key is a single long line, which probably wraps.

Thanks 1clue,  I appreciate receiving your heads up.  I'll check it out with the cat :-)

---

