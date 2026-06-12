---
title: "samba share with ftp client"
date: 2014-03-19
forum: General Help
---

### Post by Rakesh_vijayan on 2014-03-19
Dear friends 


I have a frequent requirement ,that I have setup  samba server in Location(A) and I Need to access the share from  Location (B) How it possible to access . Is it possible to access with  ftp client if so what port do I need to specify in filezilla client . 

Advance appreciation of you help


Thanks

---

### Post by kurja on 2014-03-19
I don't think ftp can get to your smb share. Maybe set up an ftp server instead? Or better yet, vpn, or maybe use ssh..?

Exactly how do you want to use the share?

---

### Post by mastablasta on 2014-03-19
smb://hostIP

if locations are more distant i suggest installing ftp server (e.g. filezilla) and then connect via sftp to it.

---

### Post by Lars Noodén on 2014-03-19
Samba works well over the LAN but for access over the Internet, SFTP / SSH would be your best option.  Clients like FileZilla and Nautilus support SFTP out of the box, so no changes are needed there.  On the server side you only need to add the package openssh-server to get SFTP and SSH.  No further configuration is needed except to forward port 22 on your externally facing router to your server and maybe also [set up key login](https://www.digitalocean.com/community/articles/how-to-set-up-ssh-keys--2) and disable password login / root login.

---

### Post by Rakesh_vijayan on 2014-03-19
> **Lars Noodén said:**
> Samba works well over the LAN but for access over the Internet, SFTP / SSH would be your best option.  Clients like FileZilla and Nautilus support SFTP out of the box, so no changes are needed there.  On the server side you only need to add the package openssh-server to get SFTP and SSH.  No further configuration is needed except to forward port 22 on your externally facing router to your server and maybe also [set up key login]("https://www.digitalocean.com/community/articles/how-to-set-up-ssh-keys--2") and disable password login / root login.

location B clients are ubuntu users so I can't use \\server\user . let me know  Lars Nooden users are not tech savvy They need GUI for access my samb . If you have configuration for  SFTP please share it to me 

Thaks for all people who read and replay

---

### Post by kurja on 2014-03-19
Set up a user account for remote users with access to desired folder, and have them ssh/sftp into it, Nautilus -> file -> connect? All gui.

---

### Post by Lars Noodén on 2014-03-19
FileZilla and Nautilus are GUI apps that support SFTP.  So to connect to an SFTP server, no additional software is needed.  In Nautilus, for example, go to the location bar (press ctrl-L if necessary) and enter the URL for the server:

```

sftp://user@xx.yy.zz.aa/path/to/dir/

```

Obviously substitute the relevant user name, server IP number and directory path.

As far as setting up basic SFTP goes, just install the package openssh-server.  That will automatically install and run an SFTP server for you.  No additional configuration is needed to connect to it over the LAN.  If you are connecting over the Internet, then you will have to forward port 22 (SSH) on your router from the extrernal ip address to your server.  The details of that depend on the router itself and vary from model to model and brand to brand.  So after you have LAN access via SFTP you can take a look at your router.

Nautilus can use keys.  So it is worth looking into setting up key access.  It is easy once you know how, but maybe that first time can be confusing.  If you do get keys working, you can turn off password access.  If you do not get keys working be sure to use strong passwords.

---

### Post by mastablasta on 2014-03-19
+1 on using keys rather than passwords.

that way you can set it up for them to automaticly connect to your server + and as a bonus connection will be more secure.

---

### Post by Rakesh_vijayan on 2014-03-19
> **Lars Noodén said:**
> FileZilla and Nautilus are GUI apps that support SFTP.  So to connect to an SFTP server, no additional software is needed.  In Nautilus, for example, go to the location bar (press ctrl-L if necessary) and enter the URL for the server:

```

sftp://user@xx.yy.zz.aa/path/to/dir/

```

Obviously substitute the relevant user name, server IP number and directory path.

Nautilus can use keys.  So it is worth looking into setting up key access.  It is easy once you know how, but maybe that first time can be confusing.  If you do get keys working, you can turn off password access.  If you do not get keys working be sure to use strong passwords.


Nautilus-connect-server woks fine for me It is complicated to the user to enter to much details, second options is gud solution I use this command to mount the remote file ( sudo sshfs rakesh@10.10.10.10:/home/rakesh /home/nadeen/Desktop/rakesh/  ) but 
it show the permission problem . I give full permission for both the home directory /home/rakesh and mount directory /home/nadeen/Desktop/rakesh 
when I try to enter into the mount directory following message appeared 

nadeen@ns:~$ cd /home/nadeen/Desktop/rakesh/
bash: cd: /home/nadeen/Desktop/rakesh/: Permission denied
nadeen@ns:~$ 


please see the attachment it will show the problem that I am facing

---

### Post by Lars Noodén on 2014-03-19
I would guess the problem arises because it was mounted with sudo.  I don't know the ins and outs of FUSE but as far as I know it works with user permissions.  Just plain sshfs without sudo should do it:

```

sshfs rakesh@10.10.10.10:/home/rakesh /home/nadeen/Desktop/rakesh/

```

You'll have to unmount first.

```

fusermount -u /home/nadeen/Desktop/rakesh/
# or 
sudo fusermount -u /home/nadeen/Desktop/rakesh/

```

---

### Post by kurja on 2014-03-19
> **Rakesh_vijayan said:**
> Nautilus-connect-server woks fine for me It is complicated to the user to enter to much details,

I don't have a linux/ubuntu system in front of me right now but I'm pretty sure you can add the connection as a shortcut to the left side pane on Nautilus, so your users would just click that.

edit - those shortcuts are called bookmarks in Nautilus. Just open the connection once, then add to bookmarks, should be very easy for user to access.

---

### Post by Rakesh_vijayan on 2014-03-19
> **Lars Noodén said:**
> I would guess the problem arises because it was mounted with sudo.
[/code]

wow great help for me and ubuntu users . Let me know Lars If I add this entry in my fstab does it will work at boot time when I tried with the following command at fstab > sshfs#rakesh@10.10.10.10:/home/rakesh /home/nadeen/Desktop/rakesh/  fuse defaults,idmap=rakesh 0 0at the boot time I got error message "An error occur while mounting rakesh@ip  press S to skip and M to manually configure  .And also will you give me good steps for change credential to key password

---

### Post by Lars Noodén on 2014-03-19
If you put sshfs in fstab, the root problem you had above with sudo will also come back.  It will have to be launched as the user.  You could make an icon for a script to do that or there might be a more appropriate way to have it happen when the user logs in graphically.  Maybe .xsession?

About the keys, there are lots of tutorials, but the concept is simple.  Generate a key pair and then (carefully) put the public key on the remote machine.  It goes in the file ~/.ssh/authorized_keys there and should be whole and unbroken, one key per line.  

You generate the keys locally with [ssh-keygen](http://manpages.ubuntu.com/manpages/saucy/en/man1/ssh-keygen.1.html).

```

ssh-keygen -t rsa -b 2048 -f ~/.ssh/servername -C 'some comment about usage'

```

If you have more recent versions of ssh and sshd, you can use other key types such as ecdsa and ed25519.

---

### Post by Lars Noodén on 2014-03-19
I think I spot the error.  

```

sshfs#rakesh@10.10.10.10:/home/rakesh /home/nadeen/Desktop/rakesh/ fuse defaults,noauto,user,idmap=user,reconnect 0 0

```

That should prevent it from getting mounted automatically.  It should also let the user (or a user script) to mount it without root intervention.

---

### Post by HermanAB on 2014-03-19
FWIIW, smbclient provides an FTPlike interface to Samba shares.  RTFM for details.

---

### Post by kurja on 2014-03-19
> **HermanAB said:**
> FWIIW, smbclient provides an FTPlike interface to Samba shares.  RTFM for details.

I doubt you can do anything to an smb server from outside of lan with that. Can you?

---

### Post by Rakesh_vijayan on 2014-03-20
> **Lars Noodén said:**
> I think I spot the error.  

```

sshfs#rakesh@10.10.10.10:/home/rakesh /home/nadeen/Desktop/rakesh/ fuse defaults,noauto,user,idmap=user,reconnect 0 0

```

That should prevent it from getting mounted automatically.  It should also let the user (or a user script) to mount it without root intervention.

I can't test this one if my key based authentication is success . because client need to authenticate server at boot time .how it possible
.
   I have problem with key authentication with the remote server . I use the following this command 

```
ssh-keygen

ssh-copy-id rakesh@publicip 

ssh-add


```

Above  is not working in real environment, which ask me password .configurations of the server is  { Bsnl-----pfsense firewall ---portforward to server ip }

But below  testing was success login in my virtual box
```
ssh-keygen
This
ssh-copy-id rakesh@local server 

ssh-add


```

Thanks

---

### Post by Lars Noodén on 2014-03-20
Once the key pair is generated, the public key needs to go into the account on the remote server.  Usually that is ~/.ssh/authorized_keys  Be sure that the directory and the authorized_keys file have fairly restrictive permissions.  The directory .ssh should be 700 or something like that.  And the key file should be 644, 640 or 600.  Also double check that you are using the right matching keys, if you have more than one pair about and that you have copied the public key, leaving the private key behind on the client.  

Then if that does not work try manually transferring the public key.  You can use nano or vi or whatever to edit the authorized_keys.  Erase the old one and paste in the new one, making sure that it is all on one line, unbroken, and not allowed to wrap.  

If that does not work, then check the value of *AuthorizedKeysFile* in /etc/ssh/sshd_config to make sure it matches where you have put the public key.

(/usr/bin/ssh-copy-id is just a shell script to do a public key transfer.  You can look at the source with 'less' but it only handles a narrow range of contingencies for when things go right the first time.  You can try it with -n to do a dry run first to see what might happen.)

---

### Post by Lars Noodén on 2014-03-20
Also, is the key in the agent?

```

ssh-add -l

```

If not then the key has to be specified by the client when connecting.

```

ssh -i /path/to/some/key/.ssh/some_key_rsa rakesh@10.10.10.10

```

or added to the agent explicitly.

```

ssh-add /path/to/some/key/.ssh/some_key_rsa

```

What version of Ubuntu are you using on the client?  It might have some additional key chain software to automatically load the key when the user logs in graphically.

---

### Post by Rakesh_vijayan on 2014-03-20
[/code]

What version of Ubuntu are you using on the client?  It might have some additional key chain software to automatically load the key when the user logs in graphically.[/QUOTE]

Both are 12.04 client is 64bit . command ssh-add -l in client show this message 
```
nadeen@ns:~$ ssh-add -l
2048 12:e5:d2:86:ba:70:51:e2:da:69:7c:ed:94:66:be:45 nadeen@ns (RSA)


```

server 

```
rakesh@mtu:~/.ssh$ ssh-add -l
Could not open a connection to your authentication agent.
rakesh@mtu:~/.ssh$ 

```


If that does not work, then check the value of *AuthorizedKeysFile* in /etc/ssh/sshd_config to make sure it matches where you have put the public key.
```


RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile      %h/.ssh/authorized_keys


```

It already enabled by removed the # sign 

> nadeen@ns:~/.ssh$ ssh -i /home/nadeen/.ssh/id_rsa.pub rakesh@pubip
rakesh@pubip's password: 


Still my client ask the password 

I appreciate your help[ 						 							 						 					]("http://ubuntuforums.org/member.php?u=168643") 				 				 					 						 	[**[COLOR=#DD4814][B]Lars Noodén**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=168643") 	 
 						[IMG]http://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-offline.png[/IMG]  					 					 I don't know why my ubuntu ask for the password . I tried all the possibilities  by adding A's id_rsa.pub  to B authorized_keys  and   vice versa

---

### Post by Lars Noodén on 2014-03-20
The private key stays on the client and is the one used for authentication:

```

[s]ssh -i /home/nadeen/.ssh/id_rsa.pub rakesh@pubip[/s]
ssh -i /home/nadeen/.ssh/id_rsa rakesh@pubip

```

---

### Post by Rakesh_vijayan on 2014-03-20
> **Lars Noodén said:**
> The private key stays on the client and is the one used for authentication:

```

[s]ssh -i /home/nadeen/.ssh/id_rsa.pub rakesh@pubip[/s]
ssh -i /home/nadeen/.ssh/id_rsa rakesh@pubip

```

I try both of them  below picture 
[IMG]http://s4.postimg.org/5b8y3907x/loginto_server.png[/IMG]

autorized key of server

[IMG]http://s28.postimg.org/w4lsidial/autersikey.png[/IMG]
.ssh directory of the server

[IMG]http://s9.postimg.org/tv2s4edm7/serverssh1.png[/IMG]

Client key 

[IMG]http://s29.postimg.org/jd6ad9bc7/client_key.png[/IMG]


I appreciate you lar

---

### Post by Lars Noodén on 2014-03-20
It looks like it might be a permissions problem.  On rakesh, you need to fix the permissions for .ssh and some of the files in that directory.

```

chmod o-w ~
chmod 700 ~/.ssh/
chmod 600 ~/.ssh/*
chmod 644 ~/.ssh/*.pub

```

Then what are the permissions for the home directory?  They look off, too.

```

ls -ld ~

```

Depending on what they are, they might have to be fixed before ssh will allow the use of files within ~/.ssh

---

### Post by Rakesh_vijayan on 2014-03-21
> **Lars Noodén said:**
> It looks like it might be a permissions problem.  On rakesh, you need to fix the permissions for .ssh and some of the files in that directory.

```

chmod o-w ~
chmod 700 ~/.ssh/
chmod 600 ~/.ssh/*
chmod 644 ~/.ssh/*.pub

```

Then what are the permissions for the home directory?  They look off, too.

```

ls -ld ~

```

Depending on what they are, they might have to be fixed before ssh will allow the use of files within ~/.ssh
I don't have Internet from the last night that why I am late to express my thanks to great man 

Finaly the problem solve by the help of my great friend Lars Noodén now I can login to to server with out password to ssh . I can mount the home directory of my remote server to my client ubuntu . Problem in ssh was permission "Lars Nooden" Pointed that before setting ssh key based login when I got message permission denied I give 777 for that user  I was not aware this cause in future ,Lars give me a clear answer . 

Second one with Fstab not works   ```
sshfs#rakesh@10.10.10.10:/home/rakesh /home/nadeen/Desktop/rakesh/ fuse defaults,noauto,user,idmap=user,reconnect 0 0
```

so I just create a script and put that into the startup ,Problem solved ,Thank you very much lars

---

### Post by Rakesh_vijayan on 2014-03-21
I wish to get enter into more deep in this topic with you all .How can I make it more secure this setup for ssh and sshfs connection ,lars already point some in ssh .

---

### Post by kurja on 2014-03-22
SSH / SSHFS with keys as Lars advised you to set up, is already very secure.

---

### Post by Lars Noodén on 2014-03-22
Keys are about as good as you can get.  If you are interested in the topic you can decide how many bits to use in your RSA key or you can consider whether using one of the new key types in the newer versions of OpenSSH (ecdsa and ed25519) do more of what your want.  

There are also dongles like Yubikey, but I don't know about them.  

Less seriously, in the newer versions of sshd, you have [AuthenticationMethods](http://manpages.ubuntu.com/manpages/trusty/en/man5/sshd_config.5.html) which would allow you to require both a key and a password, not that it is a good idea to do so.  If you wanted to drive everyone there really, really crazy you could implement one-time passwords instead of normal ones.  There used to software for that, maybe it is still around.   However, it doesn't look like the newer versions of OpenSSH have been backported to 12.04 LTS, which is ok because just a key (with a strong passphrase) is considered good these days though 'two-factor' authentication is all the rage.

---

