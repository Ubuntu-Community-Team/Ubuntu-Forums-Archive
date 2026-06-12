---
title: "Error:  can't open /etc/sudoers: Permission denied"
date: 2008-02-26
forum: General Help
---

### Post by Front187 on 2008-02-26
EDITED FOR CLARITY AND UPDATES:

I cannot execute sudo in the terminal.
```
addam@addam-laptop:~$ sudo
sudo: can't open /etc/sudoers: Permission denied.
```

I cannot execute any graphical based program that requires access to sudo.  They hang indefinitely when I try.

My /etc/sudoers permissions are correct.
```
-r--r-----  1 root root       505 2008-02-27 11:38 sudoers

```
The above is the equivalent of 0440

I cannot access sudo as root
```
root@addam-laptop:~$ sudo
sudo: can't open /etc/sudoers: Permission denied

```

The contents of my sudoers file is the install default.
/etc/sudoers
```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```

My /etc/group file appears to be correct.
```
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:addam
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:addam
fax:x:21:
voice:x:22:
cdrom:x:24:haldaemon,addam
floppy:x:25:haldaemon,addam
tape:x:26:
sudo:x:27:
audio:x:29:addam
dip:x:30:addam
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:addam
sasl:x:45:
plugdev:x:46:haldaemon,addam
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
dhcp:x:101:
syslog:x:102:
klog:x:103:
scanner:x:104:hplip,addam
nvram:x:105:
fuse:x:106:
ssl-cert:x:107:postgres
lpadmin:x:108:addam
admin:x:109:addam
crontab:x:110:
ssh:x:111:
avahi-autoipd:x:112:
messagebus:x:113:
avahi:x:114:
netdev:x:115:addam
haldaemon:x:116:
powerdev:x:117:haldaemon,addam
slocate:x:118:
addam:x:1000:
dirmngr:x:119:
postgres:x:120:
gdm:x:121:
```

I'm not sure how /etc/passwd is parsed, or if it even plays a role, but here it is:
```
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
list:x:38:38:Mailing List Manager:/var/list:/bin/sh
irc:x:39:39:ircd:/var/run/ircd:/bin/sh
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
dhcp:x:100:101::/nonexistent:/bin/false
syslog:x:101:102::/home/syslog:/bin/false
klog:x:102:103::/home/klog:/bin/false
hplip:x:103:7:HPLIP system user,,,:/var/run/hplip:/bin/false
avahi-autoipd:x:104:112:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
messagebus:x:105:113::/var/run/dbus:/bin/false
avahi:x:106:114:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
haldaemon:x:107:116:Hardware abstraction layer,,,:/home/haldaemon:/bin/false
addam:x:1000:1000:addam,,,:/home/addam:/bin/bash
postgres:x:108:120:PostgreSQL administrator,,,:/var/lib/postgresql:/bin/bash
gdm:x:109:121:Gnome Display Manager:/var/lib/gdm:/bin/false

```

All my *sudo permissions in /usr/bin
```
addam@addam-laptop:/usr/bin$ ls -l|grep sudo
lrwxrwxrwx  1 root   root          4 2008-02-19 18:23 gksudo -> gksu
lrwxrwxrwx  1 root   root          7 2008-02-09 01:13 kdesu -> kdesudo
-rwxr-xr-x  1 root   root      41840 2007-10-31 21:45 kdesudo
-rwsr-xr-x  1 root   root      91776 2007-06-15 08:49 sudo
-rwsr-xr-x  1 root   root      91776 2007-06-15 08:49 sudoedit

```

/etc/pam.conf is empty except for comments.

I am going to kill myself. :(

---

### Post by Sam Lars on 2008-02-26
That line only meant that if it had errors it would remount but with read-only.  If that's really the problem, you wouldn't be able to write anything at all... and it shouldn't affect opening.
You are opening it with sudo, aren't you?

---

### Post by Front187 on 2008-02-26
> **Sam Lars said:**
> That line only meant that if it had errors it would remount but with read-only.  If that's really the problem, you wouldn't be able to write anything at all... and it shouldn't affect opening.
You are opening it with sudo, aren't you?

Ahh, I didn't know that.

When I edited the fstab, I edited it via a Live CD as root.  Also, I assume I should change it back to its original state?

---

### Post by astrotech226 on 2008-02-26
If the user you are attempting to edit the sudoers file is not in the group "admin", I think you get permission denied, *EVEN* if you use sudo to edit the file.

---

### Post by Front187 on 2008-02-26
> **astrotech226 said:**
> If the user you are attempting to edit the sudoers file is not in the group "admin", I think you get permission denied, *EVEN* if you use sudo to edit the file.

Yes, this is true.  I was able to change the permissions of sudoers via a Live CD, but I was not able to edit sudoers using visudo (or any other text editor for that matter.)  How is it that I can edit my sudoers file if I don't have access to sudo? 

Here is my groups file, if this helps.

```
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:addam
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:addam
fax:x:21:
voice:x:22:
cdrom:x:24:haldaemon,addam
floppy:x:25:haldaemon,addam
tape:x:26:
sudo:x:27:
audio:x:29:addam
dip:x:30:addam
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:addam
sasl:x:45:
plugdev:x:46:haldaemon,addam
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
dhcp:x:101:
syslog:x:102:
klog:x:103:
scanner:x:104:hplip,addam
nvram:x:105:
fuse:x:106:
ssl-cert:x:107:postgres
lpadmin:x:108:addam
admin:x:109:addam
crontab:x:110:
ssh:x:111:
avahi-autoipd:x:112:
messagebus:x:113:
avahi:x:114:
netdev:x:115:addam
haldaemon:x:116:
powerdev:x:117:haldaemon,addam
slocate:x:118:
addam:x:1000:
dirmngr:x:119:
postgres:x:120:
gdm:x:121:

```

---

### Post by astrotech226 on 2008-02-26
Looking at your groups file, the only users that can edit the sudoers file would be root and addam.  If you are attempting as another user, you need to add them to the "admin" group.

If you can't edit the sudoers file, even from the Live CD, here's what I'd try.  Boot up the Live CD and get a terminal.  Then do:

```
sudo passwd
```

This will allow you to set a root passwd.  Once you do that:
```

su -
```

And then enter your new root password.  After that, you should be able to easily mount drives and edit those files.  And if you are trying to save the file in an editor like vi, you will probably get a permission denied.  That's because the file is read only.  Simply leave the vi editor with ":wq!".

---

### Post by Front187 on 2008-02-26
^^^ Thanks :)

Can someone post an example of the contents of their sudoers file, so that I know if mine is correct?

---

### Post by astrotech226 on 2008-02-26
This should be the stock file after an install.

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```

---

### Post by bodhi.zazen on 2008-02-26
No need to set a root password. Ubuntu uses sudo, use :

```
sudo -i
``` to get a root shell :twisted:

gksu for graphical applications, kdesu in KDE

To sys admin , if you can not sudo, boot to recovery mode, or use a live CD.

You really should not change the ownership / permissions of system files to edit them.

You should use visudo to make edits, or ```
sudo visudo
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

	gksudo : [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

To set a root password : ```
sudo passwd
```

To lock it again : ```
sudo passwd root -l
```

---

### Post by Front187 on 2008-02-27
Okay, so I booted into recovery mode.

I made a file containing the information in the sudoers file listed above.

```
mv -f ./sudoer /etc/sudoers
```

I used this to move the file into /etc/sudoers.

I then changed the permissions and group/owner.

```
chmod 0440 sudoers|chown root:root sudoers
```

I logged back into ubuntu with high hopes, but to no avail.


Checklist:

[LIST]
[*]It's not the permissions of sudoers
[*]It's not the owner/group of sudoers or the group file itself
[*]My filesystem is not being mounted read only
[*]It's not the content of sudoers
[/LIST]

Any other suggestions?  I'm running out of patience, probably going to restore soon.

EDIT:
Here are the contents of my passwd file.  I'm not sure how this is parsed, maybe somebody can confirm that all is well with it.

```
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
list:x:38:38:Mailing List Manager:/var/list:/bin/sh
irc:x:39:39:ircd:/var/run/ircd:/bin/sh
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
dhcp:x:100:101::/nonexistent:/bin/false
syslog:x:101:102::/home/syslog:/bin/false
klog:x:102:103::/home/klog:/bin/false
hplip:x:103:7:HPLIP system user,,,:/var/run/hplip:/bin/false
avahi-autoipd:x:104:112:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
messagebus:x:105:113::/var/run/dbus:/bin/false
avahi:x:106:114:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
haldaemon:x:107:116:Hardware abstraction layer,,,:/home/haldaemon:/bin/false
addam:x:1000:1000:addam,,,:/home/addam:/bin/bash
postgres:x:108:120:PostgreSQL administrator,,,:/var/lib/postgresql:/bin/bash
gdm:x:109:121:Gnome Display Manager:/var/lib/gdm:/bin/false

```

My username is **addam**

---

### Post by astrotech226 on 2008-02-27
So you still can't open the file?
```

sudo visudo
```

Gives you a permission denied?  Just out of curiosity, I know that your groups file has you in the admin group.  Can you verify it with the "groups" command?

---

### Post by Front187 on 2008-02-27
> **astrotech226 said:**
> So you still can't open the file?
```

sudo visudo
```

Gives you a permission denied?  Just out of curiosity, I know that your groups file has you in the admin group.  Can you verify it with the "groups" command?

I can successfully edit sudoers using visudo in recovery mode.  Before I was using a Live CD, which was much more of a pain in the ***.

The output of groups ```
$groups
addam adm dialout cdrom floppy sudo audio dip video plugdev scanner lpadmin admin netdev powerdev

```

---

### Post by bodhi.zazen on 2008-02-27
You need to add your user to the admin group

You can directly edit /etc/group via nano or vim ;)

Then reboot.

---

### Post by astrotech226 on 2008-02-27
> **bodhi.zazen said:**
> You need to add your user to the admin group

You can directly edit /etc/group via nano or vim ;)

Then reboot.

They already verified they are in the admin group.  Do you think they could have something wrong in pam or something else that's making sudo not use the admin group?

---

### Post by bodhi.zazen on 2008-02-27
Can't sort it out from the information provided. It the problem with sudo access or just /etc/sudoers ?

---

### Post by Front187 on 2008-02-27
> **bodhi.zazen said:**
> Can't sort it out from the information provided. It the problem with sudo access or just /etc/sudoers ?

sudo access.

I can't use the sudo command AT ALL.

Also, any GUI program that requires my password to run hangs indefinitley

I have posted my /etc/group /etc/passwd and /etc/suoders files on the first page. :(

What is this pam?

---

### Post by jschaab on 2008-02-27
Hmm...

So could you clarify something. What is your goal in reading sudoers? Is there a reason you need to edit it? Are you using Sudo when you attempt to read it?

For example on my own system the command you indicate gives the same error:
```

jschaab@jschaab-desktop:~$ cat /etc/sudoers
cat: /etc/sudoers: Permission denied
```

However this works just fine:
```
jschaab@jschaab-desktop:~$ sudo cat /etc/sudoers
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```

is the sudo command also failing? What error do you get when you use it?

---

### Post by Front187 on 2008-02-27
> **jschaab said:**
> Hmm...

So could you clarify something. What is your goal in reading sudoers? Is there a reason you need to edit it? Are you using Sudo when you attempt to read it?

For example on my own system the command you indicate gives the same error:
```

jschaab@jschaab-desktop:~$ cat /etc/sudoers
cat: /etc/sudoers: Permission denied
```

However this works just fine:
```
jschaab@jschaab-desktop:~$ sudo cat /etc/sudoers
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```

is the sudo command also failing? What error do you get when you use it?

All this information is already in this thread.

Maybe I should update my OP. 

I cannot use the sudo command at all.  That is the only reason I tried to edit sudoers, which is no longer an issue.

---

### Post by astrotech226 on 2008-02-27
> **Front187 said:**
> 
What is this pam?

PAM is the Pluggable Authentication Module and it manages many aspects of your computer as far as security is concerned.  The configuration is kept in /etc/pam.d.  You'll see a file in there called sudo.

It's pretty basic and I doubt that it's the problem, but I'm not sure what else it could be.  I've run some tests and if I try to sudo commands as a user not in the admin group, I don't get anything in /var/log/auth.log.  I only get log entries when they are successful which isn't really going to help your problem.

---

### Post by jschaab on 2008-02-27
Sorry, I somehow missed the second page. Is the suid bit set properly for /usr/bin/sudo?

It should look like this:

```
jschaab@jschaab-desktop:~$ ls -l /usr/bin/sudo
-rwsr-xr-x 1 root root 91776 2007-06-15 07:49 /usr/bin/sudo
```

---

### Post by bodhi.zazen on 2008-02-27
> **Front187 said:**
> All this information is already in this thread.

Maybe I should update my OP. 

I cannot use the sudo command at all.  That is the only reason I tried to edit sudoers, which is no longer an issue.

I may have missed it, but can you post /etc/sudoers please ?

Also jschaab suggestion is a good one.

---

### Post by Front187 on 2008-02-27
I've updated the OP to contain all the relevant files that I can think of.

All *sudo permissions in /usr/bin
```
addam@addam-laptop:/usr/bin$ ls -l|grep sudo
lrwxrwxrwx  1 root   root          4 2008-02-19 18:23 gksudo -> gksu
lrwxrwxrwx  1 root   root          7 2008-02-09 01:13 kdesu -> kdesudo
-rwxr-xr-x  1 root   root      41840 2007-10-31 21:45 kdesudo
-rwsr-xr-x  1 root   root      91776 2007-06-15 08:49 sudo
-rwsr-xr-x  1 root   root      91776 2007-06-15 08:49 sudoedit

```

---

### Post by Front187 on 2008-02-27
Looking over the Sudo Manual, I discovered that sudo uses /var/usr/sudo to check timestamp information.

I have no such location on my computer
```
addam@addam-laptop:~$ /var/run/sudo
bash: /var/run/sudo: No such file or directory

```

Is this relevant to my problem?

---

### Post by astrotech226 on 2008-02-27
```
addam@addam-laptop:~$ /var/run/sudo
bash: /var/run/sudo: No such file or directory

```

This is bad!  You should definitely have the /var/run/sudo directory.  Inside that, there will be directories for each username that I think have run sudo.  Then there are some numbered files in there.  An example might be:

```
/var/run/sudo/<username>/1
```

So you might be on to something.  You can probably get away with creating the directory manually.  Here's what my /var/run/sudo looks like:

```
drwx------ 4 root       root         80 2008-02-26 17:46 sudo
```

I think once you create that, your sudo will work.  I think it's failing because it can't create the username directory beneath it.

---

### Post by Front187 on 2008-02-27
This is strange.

When I create the directories in rescue mode, they disappear once I boot normally.

I think these things may be stored in /var/tmp anyway.

```
addam@addam-laptop:/var/tmp$ ls -l
total 20
-rw------- 1 addam addam 12288 2008-02-25 20:28 group.swp
drwx------ 6 addam addam  4096 2008-02-23 00:56 kdecache-addam
drwx------ 4 root  root   4096 2008-02-20 19:43 kdecache-root

```

This still wouldn't explain why the directories I make in /var/run disappear.  :-\

---

### Post by bodhi.zazen on 2008-02-27
May I ask, what did you do to get into this mess in the first place ?

---

### Post by Front187 on 2008-02-27
> **bodhi.zazen said:**
> May I ask, what did you do to get into this mess in the first place ?
Haha, I very much wish I knew. :)

Is there a log that keeps track of installation dates anywhere?

---

### Post by Front187 on 2008-02-28
Bump

If we can't figure a solution out by tonight I will reinstall.

---

