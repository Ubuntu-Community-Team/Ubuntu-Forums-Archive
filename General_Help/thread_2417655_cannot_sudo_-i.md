---
title: "cannot sudo -i"
date: 2019-04-25
forum: General Help
---

### Post by weccles on 2019-04-25
Hi...Using Ubuntu 16.04.  When I try to sudo -i, I get sorry, try again twice and I can never sudo -i. Any thoughts as to what may cause that type of response to the request?

---

### Post by deadflowr on 2019-04-25
What password are you trying a root password or your user's password?
How does  running a simple sudo command run like
```
sudo apt update
```
is it the same response?

---

### Post by #&amp;thj^% on 2019-04-25
****By default Ubuntu does not set up a root password during installation and therefore you don&#8217;t get the facility to log in as root. However, this does not mean that the root account doesn&#8217;t exist in Ubuntu or that it can&#8217;t be completely accessed.

Before we get you into trouble here dose:
```
sudo -s
```
If that works, then you end the root session with:
```
logout
```
And if not logged in as a root shell use.
```
exit
```
If you still can't get to a root status use:
```
sudo passwd root
```
To set the root environment.
NOW BE-CAREFUL, you can harm your system, and it's security. (Use sparingly)

---

### Post by The Cog on 2019-04-25
sudo -s and sudo -i do pretty-much the same thing. sudo -i is probably safer.
Don't do sudo passwd root - although if you can't do sudo -i then sudo passwd root won't work either.

You say you get sorry, try again a few times but you don't say you actually enter a password before getting the sorrry messages. You are entering a password aren't you? If not then there is somethiing happening that is very different to what we are assuming, and we need to know that or we will keep barking up the wrong tree. **Edit**. I see you answered this question while I was typing.

The password that sudo asks for is your own password, not root's password (by default root doesn't have a usable password - you have to log in as someone else then use sudo). Normally, only the user created by the installer is allowed to use sudo - other users don't belong to the right group. Are you using the first account created, or a different account? Please can you run the command **id** which will display the groups you belong to, and post that for us?

---

### Post by weccles on 2019-04-25
I was asked to look at this system because the admin is having issues&#8230;.
Seems not matter what command I put in with sudo, I get the following:
Sorry, try again.
Sorry, try again.
sudo: 3 incorrect password attempts

---

### Post by weccles on 2019-04-25
I understand that sudo does not have a password....and I am logged in as a sudoer user.
I am NOT asked to enter a password at any point when I use sudo at this point.

---

### Post by The Cog on 2019-04-25
Ooh. That sounds very odd. Just to make sure I understand, you say you type "sudo -i", then press Enter once, and you get: 
```
Sorry, try again.
Sorry, try again.
sudo: 3 incorrect password attempts 
```
without any further typing by yourself. Right?

If this is the case, then I really don't know what is happening. All I can think is to try these three commands to see if sudo is what you think it is. Below are the 3 commands and the responses I get on my PC:```
steve@StevesPC:~$ **which sudo**
/usr/bin/sudo
steve@StevesPC:~$ **file /usr/bin/sudo**
/usr/bin/sudo: setuid ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, BuildID[sha1]=5cb84745ebe2d236fe5138b0cbeff4061bff4689, for GNU/Linux 3.2.0, stripped
steve@StevesPC:~$ **alias | grep sudo**
steve@StevesPC:~$ 

```

---

### Post by weccles on 2019-04-25
$which sudo
/usr/bin/sudo
$file /usr/bin/sudo
/usr/bin/sudo: setuid ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/l, for GNU/Linux 2.6.32, BuildID[sha1]=3e4fbfd5a73126630bcc22d5dee68c32e2813566,stripped
$alias | grep sudo
$

---

### Post by weccles on 2019-04-25
I agree...it is strange, but yes, I press enter once and immediately get the 3 responses

---

### Post by TheFu on 2019-04-25
Sounds like the sudoers file or one of the other config files for sudoers.d/ have been corrupted.  I locked myself out of sudo once due to an incorrect sudoers.d/some-file change.  I'd hack in using a boot flash drive, modify the file back to the original and all was fine.  

How good are the system backups?  Does anyone know when the problem started? Can the current files be compared to the day prior files?

sudo -i gets root's environment.
sudo -s keeps the environment for the current userid.

These can be VERY IMPORTANT differences.

-i is like su -
and 
-s is like su.

---

### Post by weccles on 2019-04-25
Backups are non-existent I just found out....so....I will check the file(s) out of curiosity on another system and just see that differences are.

---

### Post by ajgreeny on 2019-04-25
I do not know whether or not this might help but a few weeks ago in early March another user was having a similar problem using a sudo commands to add a new user. Sudo was not working for any command.

The problem turned out to be incorrect permissions for the /etc/sudoers file which meant that no sudo command worked for him.  Booting to a recovery shell and running a chmod command to edit the permissions to what they must be for successful use of sudo** (ownership as root and permissions -rw-r--r--)** solved the problem that time; have a read through [https://ubuntuforums.org/showthread.php?t=2413956](https://ubuntuforums.org/showthread.php?t=2413956) and follow my suggestions there to see if perhaps this is the same for you.

---

### Post by weccles on 2019-04-25
I checked the sudoers file against a system that has no issues and they are the same.
I verified the user is in the sudo group.
Is there another place where sudo permissions may get blocked?

---

### Post by Rubi1200 on 2019-04-25
Just throwing this out there and of course The Cog, TheFu, and ajgreeny (and others) should also comment before you do anything but perhaps there is something missing or corrupted with the PAM configuration:
[https://support.oneidentity.com/es-es/kb/63263/sudo-is-rejecting-passwords-without-user-intervention-sudo-not-working-](https://support.oneidentity.com/es-es/kb/63263/sudo-is-rejecting-passwords-without-user-intervention-sudo-not-working-)

---

### Post by weccles on 2019-04-25
I checked the /etc/sudoers and it was not 644....I changed it to 644, but to no avail....still the same issue.

---

### Post by weccles on 2019-04-26
In looking at the thread from Rubi1200....I do not have an /opt/quest directory.

---

### Post by weccles on 2019-04-26
Perhaps there are missing pam files?

---

### Post by Rubi1200 on 2019-04-26
The link was just meant as a suggestion not that you actually have the particular program installed.

What I was suggesting is that the PAM configuration for sudo might be messed up but to be honest I do not know where you need to start looking to compare if that is the problem and was hoping that the others would jump in and comment.

Sorry if that was not clear.

---

### Post by TheFu on 2019-04-26
> **weccles said:**
> I checked the /etc/sudoers and it was not 644....I changed it to 644, but to no avail....still the same issue.

My sudoers are 440 root:root.
I can see that being important.  Don't want the world seeing those settings.  Let me see what the manpages says. The sudoers manpage is a work of art.  sudo can do 10,000 more things than just run a single command as root. That is the most common use, but it really is a full featured "role-based" solution.

In theory, there are specific errors that are documented in the manpage.
```
   Error log entries
     If an error occurs, sudoers will log a message and, in most cases, send a
     message to the administrator via email.  Possible errors include:

     parse error in /etc/sudoers near line N
       sudoers encountered an error when parsing the specified file.  In some
       cases, the actual error may be one line above or below the line number
       listed, depending on the type of error.

     problem with defaults entries
       The sudoers file contains one or more unknown Defaults settings.  This
       does not prevent sudo from running, but the sudoers file should be
       checked using visudo.

     timestamp owner (username): No such user
       The time stamp directory owner, as specified by the timestampowner set&#8208;
       ting, could not be found in the password database.
....
   Notes on logging via syslog
     By default, sudoers logs messages via syslog(3).  The date, hostname, and
     progname fields are added by the syslog daemon, not sudoers itself.  As
     such, they may vary in format on different systems.
...
FILES
     /etc/sudo.conf            Sudo front end configuration

     /etc/sudoers              List of who can run what
```


Professional organizations have versioned backups.  I assume that by now you've hacked into the machine and set the root password for use while working the sudo issue.  Please setup daily, automatice, versioned, backups ASAP.  With those, this would be a minor issue, solved in 10 minutes.

---

### Post by weccles on 2019-04-26
Set sudoers to 440....already root:root.

---

### Post by #&amp;thj^% on 2019-04-26
This just is the strangest post I've seen in a while, but check this also:
```
**stat /etc/sudoers**
  File: /etc/sudoers
  Size: 3174      	Blocks: 8          IO Block: 4096   regular file
Device: 804h/2052d	Inode: 2364788     Links: 1
Access: (0440/-r--r-----)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2019-04-26 07:xx:34.xxxxxxxx9 -0600
Modify: 2019-01-13 05:40:xx.xxxxxxxx0 -0700
Change: 2019-01-20 06:06:38.xxxxxxxx3 -0700
 Birth: 2017-01-20 06:06:38.008164189 -0700
```
and:
```
**stat -c "%a %n" /etc/sudoers**
440 /etc/sudoers

```

---

### Post by Rubi1200 on 2019-04-26
From the manpages:

> The sudoers file should always be edited by the visudo command which locks the file and does grammatical checking. It is imperative that sudoers be free of syntax errors since sudo will not run with a syntactically incorrect sudoers file.

Have you checked not just permissions but also that all the syntax is correct?

[https://linux.die.net/man/5/sudoers](https://linux.die.net/man/5/sudoers)

There is also an archive of I think support type questions, might be worth searching to see if something comes up:
[https://www.sudo.ws/pipermail/sudo-users/](https://www.sudo.ws/pipermail/sudo-users/)

---

### Post by weccles on 2019-04-26
#stat /etc/sudoers
  File: '/etc/sudoers'
  Size: 755    Blocks: 8    IO Blocks: 4096    regular file
Device: 802h/2050d    Inode: 12979538    Links: 1
Access: (0440/-r--r-----)    Uid: (  0/  root)    Gid: (  0/  root)
Access:  2019-04-26  11:43:13.961943053 -0400
Modify:  2017-05-29  06:19:46.000000000 -0400
Change: 2019-04-26  11:41:56.637944267 -0400
  Birth:  -

#stat -c "%a %n" /etc/sudoers
440 /etc/sudoers

#cat /etc/sudoers
----the only things not commented out are.....
Defauts   env_reset
Defaults  mail_badpass
Defaults  secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin"
root   ALL=(ALL:ALL)  ALL
%admin  ALL=(ALL)  ALL
%sudo  ALL=(ALL:ALL)  ALL

---

### Post by #&amp;thj^% on 2019-04-26
Well this is my last effort here but can you show:
```
[root@arch me]**[COLOR="#FF0000"]# sudo -l -U me [/COLOR]**
User me may run the following commands on arch:
    (ALL) ALL

```
Be sure to to change the user name to your login name ie: **sudo -l -U [B][COLOR="#FF0000"]me[/COLOR]**[/B] where **"me"** is my user.
Also wouldn't hurt to check:
```
me on Fri Apr 26 at 07:36 PM in ~ branch: (HEAD) 
>> **getent group wheel**
wheel:x:998:me

```

---

### Post by TheFu on 2019-04-26
wheel isn't used in my ubuntu systems.  That's a Solaris/BSD group for sudo.

In Ubuntu, _admin_ and _sudo_ groups are the default groups that get sudo access.

---

### Post by ajgreeny on 2019-04-27
Let's try again with the possibility of a permissions problem.

Perhaps the **/usr/lib/sudo/sudoers.so** file, (not your actual **/etc.sudoers**) has incorrect permissions, so please show us what output you get from command
```
ls -l /usr/lib/sudo/sudoers.so
```

It should be very similar to
```
-rw-r--r-- 1 root root 354592 Jan 18  2018 /usr/lib/sudo/sudoers.so
```

with root ownership and permissions -rw-r--r--, ie, writable by the owner (root) alone.
If it is wrongly owned or has the incorrect permissions you will probably have to boot into recovery mode from grub and make changes from that.

One step at a time, but we can hopefully figure this out!

---

### Post by TheFu on 2019-04-27
Would posting
```

sudo find / -iname \*sudo\* -ls -mount
``` 
be helpful?

This will show only local files/directories with sudo in their names with the permissions.  The dates wouldn't be important, so removing those via vim block actions would clean things up.

Helpful?

---

### Post by weccles on 2019-04-29
#ls &#8211;l /usr/lib/sudo/sudoers.so
-rw-r&#8212;r&#8212;1 root root 316768 Jul 4 2017 /usr/lib/sudo/sudoers.so

sudo find / -iname \*sudo\* -ls -mount
This command returns 113 files/links.
Looks like they all have at least 644 permissions set.

---

### Post by TheFu on 2019-04-29
```
-r--r-----   1 root     root          765 Feb 28 15:16 /etc/sudoers
```
All the others on my box appear to be libraries, language files, and package related, so 644 seems reasonable.  If the sudoers file isn't like above, I would definitely change that.  Also, sudoers checks the hostname to the hostname it thinks it should be.  If that has been changed, it needs to be changed consistently.  The sudoers file supports having different settings based on the current hostname.  I've deployed the same sudoers on over 3000 systems, each with different settings based on the system roll and local users.

---

### Post by weccles on 2019-04-29
I changed /etc/sudoers to 440

The hostname has not changed since the server was created

---

### Post by ajgreeny on 2019-04-29
Can we quickly check the groups to which you as user belong with command **groups**.

Run this from your own user terminal, ie the user that at present can not use **sudo** for anything.

---

### Post by TheFu on 2019-04-29
At this point, I'd boot a live-install-ubuntu with the same release.  Go into rescue mode, have it setup a chroot, purge the sudo package and reinstall it.  That should correct any pesky /etc/ config issues for it.

But it could easily be a bad ~root/.file issue.  If the ~root/.profile or ~root/.bashrc are messed up, sudo -i won't work.

---

### Post by #&amp;thj^% on 2019-04-30
> **TheFu said:**
> wheel isn't used in my ubuntu systems.  That's a Solaris/BSD group for sudo.

In Ubuntu, _admin_ and _sudo_ groups are the default groups that get sudo access.

Debian's su does support the wheel group, it's just not enabled by default. And I don't think it's wise to show how to enable it here. (Thats why I was checking, since we still have an unknown system problem)
Many Unix systems have wheel. 
> (This section is by Richard Stallman.)

Sometimes a few of the users try to hold total power over all the rest. For example, in 1984, a few users at the MIT AI lab decided to seize power by changing the operator password on the Twenex system and keeping it secret from everyone else. (I was able to thwart this coup and give power back to the users by patching the kernel, but I wouldn't know how to do that in Unix.)

However, occasionally the rulers do tell someone. Under the usual `su' mechanism, once someone learns the root password who sympathizes with the ordinary users, he or she can tell the rest. The "wheel group" feature would make this impossible, and thus cement the power of the rulers.

I'm on the side of the masses, not that of the rulers. If you are used to supporting the bosses and sysadmins in whatever they do, you might find this idea strange at first.

---

### Post by weccles on 2019-05-01
benw$ groups
benw  sudo  libvirtd  git

---

### Post by rsteinmetz70112 on 2019-05-01
Is there a root password?
If so you could su to get into a root shell.
also have you tried a different user?

---

### Post by weccles on 2019-05-02
There is no root password.
To get to a root shell, I am able to use ctl + alt + F2....to get back to user...ctl + alt + F7
There is only one user on the system currently.

---

### Post by #&amp;thj^% on 2019-05-02
Have you tried TheFu's suggestion in post #32 yet?

---

### Post by weccles on 2019-05-03
can sudo be reinstalled instead of purged and installed?

---

### Post by weccles on 2019-05-03
apt-get reinstall sudo
This is a key server that is having a problem.

---

