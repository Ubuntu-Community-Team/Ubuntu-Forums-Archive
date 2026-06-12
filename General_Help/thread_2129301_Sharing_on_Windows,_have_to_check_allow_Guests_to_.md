---
title: "Sharing on Windows, have to check allow Guests to login - not liking username/passwrd"
date: 2013-03-25
forum: General Help
---

### Post by 777funk on 2013-03-25
I noticed a while ago that i have no luck in samba networking if I don't click "allow Guests to login". Every time I enter username and password it denies access. 

Where do I start? I tried a few different usernames and of course my ubuntu password on the Windows boxes. No go.

---

### Post by Morbius1 on 2013-03-26
> Every time I enter username and password it denies access. 
What username and password are you using? The Linux username and password or the Samba username and password?

If you want to be able to access the share from windows using your own username you have to add that name and give it a password in the samba password database:
```
sudo smbpasswd -a 777funk
```
If you want to allow user morbius to gain access to the share:

** You must create the user "morbius" on the server itself.
** Then add "morbius" to the samba password database:
```
sudo smbpasswd -a morbius
```

---

### Post by 777funk on 2013-03-26
Thank you Morbius. I just tried it and received a no go in the terminal. Here's what I got:

```
nick@NickUbuntu:~$ sudo smbpasswd -a 777funk
[sudo] password for nick: 
New SMB password:
Retype new SMB password:
Failed to add entry for user 777funk.
nick@NickUbuntu:~$
```

---

### Post by Morbius1 on 2013-03-26
Are you yankin' my chain?

How about this one:
```
sudo smbpasswd -a nick
```

---

### Post by 777funk on 2013-03-26
lol, I wish! I'm pretty clueless as to how networking works with Ubuntu. I tried it with my username to begin with... i.e. "nick" and my usual ubuntu password and I keep getting the message in Win7 that the folder I click is not accessible, you might not have permission, etc... 

So I just did the above from post #3 and thought maybe I was missing something. That didn't work either. Then I did the one with 'nick'. Same result. But if I check the allow guests to access this folder it works great.

---

### Post by Morbius1 on 2013-03-26
Post the output of the following commands:
```
testparm -s
```
```
net usershare info --long
```

---

### Post by 777funk on 2013-03-27
> **Morbius1 said:**
> Post the output of the following commands:
```
testparm -s
```
```
net usershare info --long
```

Ok, here's what I get:
```
nick@NickUbuntu:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    usershare owner only = No
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    print ok = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers


```

and

```
nick@NickUbuntu:~$ net usershare info --long
[Desktop]
path=/home/nick/Desktop
comment=
usershare_acl=Everyone:F,
guest_ok=n

[Nick's Documents]
path=/home/nick/Desktop/Link to My Documents/Nick's Documents
comment=
usershare_acl=Everyone:F,
guest_ok=y

info_fn: file /var/lib/samba/usershares/my documents is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[Link to Nick]
path=/home/nick/Desktop/Link to Nick
comment=
usershare_acl=Everyone:F,
guest_ok=y

[My Music]
path=/mnt/Windows/Documents and Settings/Nick/My Documents/My Music
comment=
usershare_acl=Everyone:F,
guest_ok=y

[My Videos]
path=/mnt/Windows/Documents and Settings/Nick/My Documents/My Videos
comment=
usershare_acl=Everyone:F,
guest_ok=y

[Ashley's Computer]
path=/home/nick/Desktop/Ashley's Computer
comment=
usershare_acl=Everyone:F,
guest_ok=n

[My Pictures]
path=/mnt/Windows/Documents and Settings/Nick/My Documents/My Pictures
comment=
usershare_acl=Everyone:F,
guest_ok=y


```

---

### Post by Morbius1 on 2013-03-27
If you are having issues with these:
> [My Music]
path=/mnt/Windows/Documents and Settings/Nick/My Documents/My Music
comment=
usershare_acl=Everyone:F,
guest_ok=y

[My Videos]
path=/mnt/Windows/Documents and Settings/Nick/My Documents/My Videos
comment=
usershare_acl=Everyone:F,
guest_ok=y

[My Pictures]
path=/mnt/Windows/Documents and Settings/Nick/My Documents/My Pictures
comment=
usershare_acl=Everyone:F,
guest_ok=y
Then post the output of this command:
```
ls -dl /mnt/Windows
```

These probably won't work if "Link" means symlink since Samba won't follow symlinks unless you do something Samba regards a security issue:
> [Nick's Documents]
path=/home/nick/Desktop/Link to My Documents/Nick's Documents
comment=
usershare_acl=Everyone:F,
guest_ok=y

[Link to Nick]
path=/home/nick/Desktop/Link to Nick
comment=
usershare_acl=Everyone:F,
guest_ok=y

That leaves this one:
> [Desktop]
path=/home/nick/Desktop
comment=
usershare_acl=Everyone:F,
guest_ok=n
What is the output of this command:
```
ls -dl /home/nick/Desktop
```

---

### Post by 777funk on 2013-03-27
Here's what that gives me:

```
nick@NickUbuntu:~$ ls -dl /home/nick/Desktop
drwxrwxrwx 3 nick nick 4096 Mar 26 20:49 /home/nick/Desktop


```

---

### Post by Morbius1 on 2013-03-27
There is nothing wrong with your smb.conf and aside from some questionable choices as to what you are sharing there is nothing wrong with that share definition so there is nothing to fix. 

You may have issues after Samba allows access to your Desktop folder due to permissions of the things within it but there doesn't appear to be reason why guest access works and authenticated access does not. Especially if you are trying to access the share as "nick".

---

### Post by 777funk on 2013-03-27
> **Morbius1 said:**
> There is nothing wrong with your smb.conf and aside from some **questionable choices** as to what you are sharing there is nothing wrong with that share definition so there is nothing to fix. 

You may have issues after Samba allows access to your Desktop folder due to permissions of the things within it but there doesn't appear to be reason why guest access works and authenticated access does not. Especially if you are trying to access the share as "nick".

Questionable choices... Told you I was a newb to networking. ;) Could you expound on what you mean by questionable choices? I'm learning here.

thanks again.

---

### Post by Morbius1 on 2013-03-27
Sharing your desktop is not something I would do since by definition everything on it is executable. Then you are sharing what appears to be symlinks on the desktop which samba can't follow and I'm not exactly sure what to make of this:
> 
[Ashley's Computer] 
path=/home/nick/Desktop/Ashley's Computer 
comment= 
usershare_acl=Everyone:F, 
guest_ok=n
To me it looks like a share of a mount of a remote share of someone else's system. I'll have to try that myself someday to see if that's even possible although I'm not sure why I'd ever need to do that.

---

### Post by 777funk on 2013-03-28
Thanks for that info. This is on a home network. Would it be considered  unsafe to share the desktop in an environment where I trust everyone on  the local network and the wireless transmission is behind a security  key? Again still learning here obviously.

Also the folder you mentioned by the name of "Ashley's Computer" is less  complicated than it sounds. It's simply a backup of a computer that  recently was being replaced (old P4 that was getting tired of booting  properly). I put it there so I could bounce this data onto the new  computer that we just replaced it with.

---

### Post by 777funk on 2013-03-29
Bump and I'm curious on the sharing of the desktop. Is it unsafe to share the desktop in an environment in which I trust everyone using the *LOCAL* network?

---

### Post by bab1 on 2013-03-29
> **777funk said:**
> Bump and I'm curious on the sharing of the desktop. Is it unsafe to share the desktop in an environment in which I trust everyone using the *LOCAL* network?
 I'm not sure that * unsafe *  is the correct word to use in this context.  I would think of it as imprudent.  

User created shares (usershares) were created to allow mortal users (non-root) to be able to create shares on an ad-hoc basis.  You loose fine grained control using these usershares.  Any thing you share via *usershares *is either: 1.) available to you only or 2.) if configured, available to  **all user** accounts or 3.)  make the share available to **any casual user** that happens to be on the network you are using.  User shares are an all or nothing choice.  

Trust is not limited to nefarious ways.  If you share data be prepared to loose control of it.  It can just as easily be deleted or modified by accident as by mischief. 

I think you should seriously consider @Morbius1 advice.  

My own best practices are [LIST]
[*]Usershares are for the users own directory -- let him/her make the decision 
[*]Never share anything to a user that does not have a Samba account
[*]Never share anything by usershares outside of the home directories
[*]
[/LIST]

Are all of your users in the smbpasswd database?  You can list them with this command```
sudo pdbedit -L
```

---

