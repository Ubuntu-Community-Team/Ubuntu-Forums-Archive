---
title: "chmod to give a remote server read priveleges to a client home directory"
date: 2021-07-26
forum: General Help
---

### Post by Old Jimma on 2021-07-26
Hello Ubuntuers!

I've set up a server computer to backup a home directory on a client computer. 

The user name on the server is: **serverusername**.

The server ip address is: **serveripaddress**.

The home directory of the client computer is: **/home/username**

On the client computer, I want to issue a chmod command that gives **serverusername** computer read permission to /home/client and everything within (below) /home/client

On the client computer I need to change read permissions for /home client using the chmod command.

This is what I think the command should look like:

**chmod -R servername#serveripaddress o=r  /home/username**

Am I correct?

If I'm not correct, would you kindly offer a correction?

Thanks!
Old Jimma from the Old Country

---

### Post by GhX6GZMB on 2021-07-26
**chmod** only changes the permissions for files/directories, meaning **drwxrwxrwx** (user/group/other).
If you want to change ownership, you need to use **chown**, which only applies to **user:group**.

As I understand it, you want to allow an external server to access and read a certain file structure, but it is not a group member, so: **other**.
In that case, your command on the client would be:

**chmod -R o+rx /home/username**

"x" is needed for "other" to traverse the subdirectories.

Now, **how** your server gets access is a completely different story.

---

### Post by scorp123 on 2021-07-26
> **Old Jimma said:**
>  
This is what I think the command should look like:

**Just no, no, no.** Messing with file permissions and file ownerships at your currently low level of knowledge is bound to destroy things. The safest approach for you would be to install **"openssh-server"** on the server, and the package **"rsync"** on both client and server, and then push your backup onto the server.

```
rsync -avz --progress /path/you/want/to/backup serveraccount@serveraddres:/path/where/the/backup/should/go/
```

Taddaaa. No need to mess with permissions or anything!!

---

### Post by Old Jimma on 2021-07-27
Hi scorp123:

Thanks for your reply and what would seem to be the exact solution to almost what I want to do, maybe not quite. 

I'm not going to use rsync. Maybe later but not for starters.

But thanks for your reply. It gives me something to think about.


Take care!
Old Jimma from the Old Country

---

### Post by Old Jimma on 2021-07-27
HI mi9104:

Thanks for your reply.

I'm accustomed to using chmod commands that are more like what you wrote. 

I wondered about your command. Doesn't it give rx privileges to ALL OTHERS?? (cap letters added only to try to communicate clearly, and not irritate you. Sorry if they did. Hope you see my point.)

What I want is to issue privileges only to one very specific other: **serverusername@serveripaddress**   

Thanks,
Old

---

### Post by scorp123 on 2021-07-27
> **Old Jimma said:**
> What I want is to issue privileges only to one very specific other: **serverusername@serveripaddress**   

That command does **NOT WORK LIKE THAT.**

You really need **rsync**.

The core of the problem is that you are conflating local file permissions, local file ownership, local file access control lists with network protocols, e.g. topics that do not really have anything to do with each other. You'd have to implement some kind of central directory service (e.g. LDAP or Active Directory) and some kind of file sharing / network protocol (e.g. SMB or NFS) that is governed by that central directory to make all these things work in tandem, hand in hand. Long story short: Way too complicated. Takes months to aquire the needed skills and know-how for each of these, and then takes days and several attempts to get it implemented in a way that would work.

Just use "rsync" and push the backup from client to computer. Takes like 5 minutes to implement this and it's not complicated at all.

---

### Post by Old Jimma on 2021-07-27
Thank you for your thoughtful reply, scorp123.

I've read authoritative web sites that have indicated that a secure server must have been granted permission. to have access to a client. This tread is about following up on that assertion to learn more.

Sorry this post has frustrated you. Ok if you want to give up.

I hope others will offer advice.

Take care,

Old

---

### Post by scorp123 on 2021-07-27
> **Old Jimma said:**
>  I've read authoritative web sites that have indicated that a secure server must have been granted permission. to have access to a client. 

First of all: Which web sites exactly? Not all web sites that claim to be *"authoritative"* are really deserving of such a title. 

Second: It really depends on what exactly they were talking about. Were they talking about a Windows environment with an Active Directory infrastructure, where every server computer and also client computer also has an Active Directory account, and thus giving one machine read access over the files of another machine actually *does* work?

Linux is not Windows and such things don't work like that here. Not without some massive tweaking and installing lots of extra services and extra packages, e.g. LDAP, NFS, and the like.

What does work and is straightforward is SSH (and by extension: "rsync" via SSH), e.g. you can exchange SSH keys between systems and then "User A" on Client A could login as "Admin B" on Server B. Or vice versa, whichever way you want the communication to take place. That's easy to implement, but does not involve any manipulations of any local file permissions. Since both sides (e.g. "User A" on Client A, "Admin B" on Server B ...) work with the files they already have permissions to there's no need to *"grant the other system permissions"* or manipulate any local files to get this to work.

And for the record: I'm not *"frustrated"*, I'm trying to prevent you from hosing your own system with commands that might have potentially unwanted side-effects and not do what you think they do.

---

### Post by ActionParsnip on 2021-07-28
Well obviously a server needs to grant access to the client for it to work. Isn't that what all this chmod nonsense is about.
I'd give a +1 to the rsync option. Swap SSH keys and you are set. The transmission of data will also be secured. 
If you setup a central authentication system like LDAP then you can use a single account instead and apply permissions based on those accounts. You don't have this (as far as I can tell) so you will need to work with local authentication systems. You can't just use another system's username in a chmod command on a remote system. Authentication doesn't work like that.
The accounts on a system are held in /etc/passwd and do not store any accounts for any other system than itself.

---

### Post by Old Jimma on 2021-07-28
Hi AcitonParsnip:

Thanks for your reply. I appreciate it.

I realized that I omitted what may be a few key pieces of information:

Both the client and server are my machines. On the client, I want to grant priveleges to the server to read files. 

Learning how to do that is the only objective of my post. Thank you for your comment on rsync. However, at this point of my project 
[LIST]
[*]**I'm interested in understanding the security issues, only.**
[/LIST]


To achieve further understanding about the security issues I wondered more about a recommendation make previously 
> 
to use the code  **rsync -avz --progress /path/you/want/to/backup serveraccount@serveraddres:/path/where/the/backup/should/go/** and not be concerned about permissions



My specific question is: **once a person A knows the home directory name and IP address of another persons (B) computer, what's to stop person A from hacking person B using, for example, the code listed above?**

I'll look foward to understaning your reply, ActionParsnip!

Thanks,
Old

---

### Post by scorp123 on 2021-07-28
> **Old Jimma said:**
>  My specific question is: **once a person A knows the home directory name and IP address of another persons (B) computer, what's to stop person A from hacking person B using, for example, the code listed above?**


Simple: There'd be a password prompt. Without knowing the exact username and the password on the remote system, that command will take you nowhere. And password-authentication is something that can be turned off so that only key-based authentication is possible. And if the systems are supposed to communicate over the Internet then it is good practice to do exactly that. Meaning: You are either in posession of the SSH key and can login, or you do not have the needed SSH key file and can't get in, even if by some dark black magic you were to know the correct password for the remote user account. "You shall not pass!" as Gandalf put it. And key-based authentication can be even escalated further: You could set a passphrase on that key. Meaning: Even if by some dark black magic you were to obtain a copy of the SSH key file you still would not be able to get in if you didn't also know the passphrase for the key. And even this can be escalated even further: you could implement a 2-Factor Authentication mechanism e.g. with Google Authenticator if you wanted to. Meaning: Even if by some dark black magic an intruder were to have a copy of the needed SSH keys and even if they were to know the needed passphrase for those keys, with 2-Factor Authentication they'd still be hitting a wall. Because now they'd also need to be in posession of your mobile phone where Google Authenticator is running.

SSH and by extension running "rsync" over SSH is as safe as you could possibly be, and the security can be tightened to really paranoid levels if you wanted to.

And then there are programs such as **"fail2ban"**. Which can be set to listen for failed SSH login attempts and then automatically ban any wannabe intruder and completely block their IP address from ever reaching your system again. It's also good practice to use that.

---

### Post by Old Jimma on 2021-07-28
Hi ActionParsnip:

Just realized that at least a part of the permission issues on the client machine will be setting up ufw so that it blocks all other ip addresses except the server's ip. 

Also, maybe another part of it includes specifying in ufw to accespt ssd (or is it ss "something else"). I am 105 years old and I forget things now and then.

The purpose of my post was to find out if there was anything other than those 2 things to cover the security issues. I vaguey recalled reading that the chmod may be needed... but I really didn't see any way to be very specific about allowing a specific person/ip address using chmod.

In my ancient clumsiness I amy have suggested that username and user ip could be... because of how that can be used with chown.

Alot of people don't know that when you turn 105, you begin to realize that there are more "ch" things to confuse than you had ever thought about.

Hope you have a great day.

Old

---

### Post by scorp123 on 2021-07-28
> **Old Jimma said:**
>  I am 105 years old ...

Impressive. :-D

---

### Post by TheFu on 2021-07-28
**chmod** works on the local machine or over NFS mounts.  There is no remote version of the command.  
If you ssh into the remote system, the chmod commands are "local" to that remote system.

Whenever in doubt, check what the manpage says.

Now, you can limit ssh/scp/rsync/sftp access to specific users@specific client hostnames/IPs, but that isn't chmod. That is ssh.  The sshd_config file has settings  to limit which users from which remote systems can connect.  **Match** is the keyword in that config file.  For example, I don't allow any ssh-based access to my systems, except from one of my internal, trusted, subnets.

At the bottom of the sshd_config file, is
```
PasswordAuthentication no
Match Address 172.22.22.0/24,172.21.22.0/24,172.22.21.0/24
      PasswordAuthentication yes
```

This says no passwords can be used, unless the client is from one of 3 subnets, then password-based authentication can be used.  So, any other subnets (including the internet) must use either ssh-keys or ssh-certs for authentication.

In the OP, you wrote:
```
chmod -R servername#serveripaddress o=r /home/username
```

a) servername#serveripaddress isn't valid for any chmod command. Not ever.
b) *o=r*  will set ------r-- permissions, so the user or any members of the group cannot access the file.  "Other" means anyone who isn't the owner or in the group.  It is highly unlikely you really want this.  I suspect you want *u=rwx,g=rwx,o=r* ... or in octal, 774 (-rwxrwxr--). Much shorter that way.  664 would be -rw-rw-r-- and is also good for data.  644 would be fine too, -rw-r--r--

Seems a refresher on basic Unix permissions is needed.  "Ubuntu permissions" web search will find a tutorial, but any Unix permissions tutorial is 100% fine and the same skills. There's no difference between all Unix-based permissions and what Ubuntu does.

---

### Post by CharlesA on 2021-07-28
> **scorp123 said:**
> Simple: There'd be a password prompt. Without knowing the exact username and the password on the remote system, that command will take you nowhere. And password-authentication is something that can be turned off so that only key-based authentication is possible. And if the systems are supposed to communicate over the Internet then it is good practice to do exactly that. Meaning: You are either in posession of the SSH key and can login, or you do not have the needed SSH key file and can't get in, even if by some dark black magic you were to know the correct password for the remote user account. "You shall not pass!" as Gandalf put it. And key-based authentication can be even escalated further: You could set a passphrase on that key. Meaning: Even if by some dark black magic you were to obtain a copy of the SSH key file you still would not be able to get in if you didn't also know the passphrase for the key. And even this can be escalated even further: you could implement a 2-Factor Authentication mechanism e.g. with Google Authenticator if you wanted to. Meaning: Even if by some dark black magic an intruder were to have a copy of the needed SSH keys and even if they were to know the needed passphrase for those keys, with 2-Factor Authentication they'd still be hitting a wall. Because now they'd also need to be in posession of your mobile phone where Google Authenticator is running.

SSH and by extension running "rsync" over SSH is as safe as you could possibly be, and the security can be tightened to really paranoid levels if you wanted to.

And then there are programs such as **"fail2ban"**. Which can be set to listen for failed SSH login attempts and then automatically ban any wannabe intruder and completely block their IP address from ever reaching your system again. It's also good practice to use that.

All valid points.

Not to mention, that in the case of running SSH on two servers that are local to you, ensuring the port SSH is running on isn't open to the internet is also a good idea.

It shouldn't be exposed by default unless you are:
A) Running IPv6 with no Firewall (cuz everyone get a public IP)
B) Port Forwarding the SSH port on your router over IPv4 (cuz you are more likely than not behind NAT)
C) Connecting the machine directly to the internet with no firewall enabled.

If you use a strong password and not expose SSH to the internet at large, you are fine for 99% of things. If you want to be more secure, you can set up key-based authentication and then disable password authentication, so the connection cannot be brute forced via guessing passwords.

More info here:
[https://www.digitalocean.com/community/tutorials/how-to-harden-openssh-on-ubuntu-18-04](https://www.digitalocean.com/community/tutorials/how-to-harden-openssh-on-ubuntu-18-04)

File permissions took a while for me to wrap my head around when I first started out - it's even worse if you take assumptions from the Windows world since Linux file permissions work in a completely different way from Windows permissions.
This guide should be pretty helpful:
[https://www.linux.com/training-tutorials/understanding-linux-file-permissions/](https://www.linux.com/training-tutorials/understanding-linux-file-permissions/)

---

### Post by TheFu on 2021-07-28
ssh key-based authentication is not just more secure. It is more convenient. I don't understand why everyone doesn't just use keys instead of passwords. Makes no sense to me.  Being prompted once per login to unlock ssh keys, but having full access to all your systems over ssh, scp, sftp, rsync from that point until logout is crazy convenient.

---

### Post by Old Jimma on 2021-08-17
Thanks, Scorp123.

I'm giving this a try. Looks very promising.

Old

---

