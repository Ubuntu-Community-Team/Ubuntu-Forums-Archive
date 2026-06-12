---
title: "Connection issue when ssh using sudo"
date: 2024-04-05
forum: General Help
---

### Post by jwoodruff on 2024-04-05
I am trying to setup automated backups of my Ubuntu, (23.10) desktop computer (OpenSSH_9.3p1 Ubuntu-1ubuntu3.2, OpenSSL 3.0.10 1 Aug 2023) to an older desktop computer running a minimal Arch Linux installation with the i3 window manager using rdiff-backup.
The older desktop (Server) running Arch to which I would like to store my backups has sshd-server installed (OpenSSH_9.6p1, OpenSSL 3.2.0 23 Nov 2023) and and the Ubuntu machine I'm trying to backup, (Client) has sshd-client installed, (OpenSSH_9.3p1 Ubuntu-1ubuntu3.2, OpenSSL 3.0.10 1 Aug 2023). I have configured /etc/ssh/sshd_config on the Server to require public/private key authentication but permit root login.
I have also set up a "root equivalent" account on the Server in order to allow me to backup using a sudo rdiff-backup command.
I am able to connect to the normal user account  using the key pair authentication as well as execute rdiff-backup commands, (no sudo) to backup a test folder. My problem occurs when attempting to do a backup using a sudo rdiff-backup command to backup folders to the "root-equivalent" account on the Server. I get "connection closed by <ip address of Server> port <assigned port>" response immediately when attempting the sudo rdiff-backup command and also when simply attempting a ssh session into the "root-equivalent" account of the Server, - that is: ssh <root_equivalent_user>@<ip address of Server> -p <assigned port>.
I've been attempting to follow instructions from "TheFu" found here: [https://ubuntuforums.org/showthread.php?t=2496169&highlight=rdiff-backup](https://ubuntuforums.org/showthread.php?t=2496169&highlight=rdiff-backup).
I would prefer to do "Push" backups because, as I understand what I've read, the "root equivalent" account will be required. The server is not normally connected to the internet, (I have connected the two computers using a crossover cable) but my desktop is so I'd rather not set up any "root equivalent" accounts on that.
I did come across some instructions which suggested using "Match User" and "Match Address" methods, but have been unsuccessful in finding the proper means of employing these methods.    
I have created a second private key in /root/.ssh/id_rsa and edited the sudoers file in the Server by uncommenting: # %sudo ALL=(ALL:ALL) ALL with no success.
Is it possible the version difference between that on the Ubuntu Desktop and that on the Arch Linux Server is causing the problem?
If someone could provide me with some assistance or point me to some clear instructions, it would be greatly appreciated.
If I could succeed in simply ssh_ing into the server via sudo command, I think I would be able to put together a script to execute the automated backups successfully.
Thanks in advance for any assistance provided.

---

### Post by MAFoElffen on 2024-04-05
There are tricks to do that...

Does this old archived thread help you? [https://ubuntuforums.org/archive/index.php/t-2444949.html](https://ubuntuforums.org/archive/index.php/t-2444949.html)

---

### Post by jwoodruff on 2024-04-05
Thanks, I have looked at that thread - that is where I found the suggestions to "Use the Match User and Match Address methods" which I'm unclear on how to apply.
Another complication with this information for me is it is referring to a method to "Pull" backups and as I had mentioned, I'm trying to set up to "Push" the backups from my desktop to the server.
This thread also suggested creating a ~/.ssh/config file to simplify the connection. I have done that for my "normal user" ssh connections in (/home/me/.ssh) - which works great, however I can also successfully connect by entering the command: ssh <unprivileged user>@<ip address> -p <assigned port>.
My trouble occurs when attempting to log into the "root equivalent" account I created on the server using the command: sudo ssh <root equivalent user>@<ip address> -p <assigned port>, whether as root on my desktop, (sudo su) or from my user account (sudo) I could create a second config file but I wouldn't expect any better results.

---

### Post by TheFu on 2024-04-05
_Match User_ and _Match Address_ are configurations in the ssh-server config file **sshd_config**.  The manpage for sshd_config explains all the options nicely.  There are probably examples of using each too.  If not, there are examples posted on the internet.  The only trick is that you want those at the bottom of the config file, so they happen last.  At least that's how I do it.

I didn't read the first post. Walls of text are too hard for me to read. Sorry.

---

### Post by aljames2 on 2024-04-06
> **jwoodruff said:**
> ..I have created a second private key in /root/.ssh/id_rsa and edited the sudoers file in the Server by uncommenting: # %sudo ALL=(ALL:ALL) ALL with no success.

It appears you are creating keys under root itself.  Perhaps this can  work if you are allowing root login on the server, I don't.

Mine is here: root@b550a-rzn: /home/rsync-bak/.ssh#
I have another server using rdiff-backup in the same way, just picked this one since I'm on this machine.

This single purpose, root owned user is 'rsync-bak'. When I created the user I gave it an unused UID of 900, & no GUID. The user was created while I was root on that server, so this user is now owned by root but I have limited it's permissions on the server to only run 1 elevated command (sudo rsync), done by adding a statement in the sudoers file.  Everything I am running is either Ubuntu or Xubuntu so not sure what you may need to consider using Arch as your server.

---

### Post by jwoodruff on 2024-04-08
Ok - thanks to all - I think I've got the Match User / Address ok now.
However, now,
This works - 
ssh <root_equivalent_user>@<server_ip> -p <port>

and this works -
rdiff-backup -v5 backup --include /home/ --include /etc/ --include /usr/local/ --exclude '**' / "-p <port> <root_equivalent_user>@<server_ip>"::/root/Backups/

This doesn't work -
sudo ssh <root_equivalent_user>@<server_ip> -p <port>

nor does this -
sudo rdiff-backup -v5 backup --include /home/ --include /etc/ --include / usr/local/ --exclude '**' / "-p <port> <root_equivalent_user>@<server_ip>"::/root/Backups/
Both commands return -
Permission denied (publickey)
Any suggestions?

---

### Post by MAFoElffen on 2024-04-08
Because there are two problems with that, right off the bat.

If you sudo shh, the user becomes root, with has no loggin or password by default in Ubuntu. You would have to give root a password.

Second, there is a line in the /etc/ssh/sshd_config file which you would have to change the key 'PermitRootLogin; to 'yes'. It's default value is 'no', to not allow a root user to login via shh.

Does that explain what you keep asking?

---

### Post by TheFu on 2024-04-09
Since 20.04, sudo under ubuntu without a userid specified changes the HOME to /root/.  Did you setup ssh-keys between the local root account and the remote <root_equivalent_user>@<server_ip>?

To be certain, use **sudo -H**, if you aren't positive.

BTW, you keep ignoring my STRONG suggestion to setup a ~/.ssh/config file.  It will drastically simplify your commands AND effectively document the users and connections from system A to system B, C, D, E, F, .... Z.  No need to clutter up the different commands with users, ports, IPs. We set them 1 place and it gets used by all others.  Of course, you need to setup the correct client-side  ~/.ssh/config file based on the currently active user.

Root-equiv accounts don't get stopped by the lack of no-root-login-permitted (or whatever ssh has).  ssh looks for "root", not uid=0.  I don't have any PermitRootLogin set on any of my systems in the sshd_config.

---

### Post by jwoodruff on 2024-04-09
Thanks again for the help and the patience - I'm trying to learn this

I expect I haven't properly set up ssh keys between the local root account and the root equivalent user account on the server - I will work on that and try again.

I do have a /.ssh/config file which works great to simply ssh connect from normal user to normal user accounts - I do intend to add a "stanza" (as I understand it at this point just requires additional lines to be added) but I figure the first step is to get a successful login using sudo so I can get backups done properly, (and properly set up the new stanza)

Also, - to MAFoElffen, I have  changed the PermitRootLogin line in /etc/ssh/sshd_config file to Yes

---

### Post by TheFu on 2024-04-10
I made a mistake - searched for the wrong thing.

```
PermitRootLogin prohibit-password
DenyUsers root

```
is a setting in the target of the rdiff-backup command.  Because I do "pull" backups, not "push", those settings are on each client system to be backed up.  I further restrict ssh access with 
```
PasswordAuthentication no
AllowUsers ubuntu tf

Match Address 172.22.22.0/24,172.21.22.0/24,172.22.21.0/24
      PasswordAuthentication yes

Match User back99xx Address 172.22.22.99
     AllowUsers back99xx ubuntu 

```
at the bottom of the file.  Basically, I allow the back99xx user to login only from 1 IP and only using ssh-keys, since passwords are only allowed from my subnets for non-root users.
See how the specific restrictions get stronger as the file goes forward after I deny all root logins?  Sorry if this isn't clear.

---

### Post by jwoodruff on 2024-04-13
Thanks to all again - I will mark this as solved
I created a /root/.ssh directory and generated another key and appended the id_rsa.pub file to the authorized_keys file of the root equivalent account on the server. All seems ok now.
Also, I appended the appropriate entries in my ~/.ssh/config file to simplify the connection process as suggested.
My next steps will be to create the script and set up things to be automated

---

