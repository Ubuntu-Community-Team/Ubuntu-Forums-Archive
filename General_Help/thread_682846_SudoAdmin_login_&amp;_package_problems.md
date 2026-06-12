---
title: "Sudo/Admin login &amp; package problems"
date: 2008-01-30
forum: General Help
---

### Post by myke on 2008-01-30
As I mentioned on another post, I can no longer launch any program that requires a password whether it be user settings, synatic, even the updater.   Even if I set root to be allowed to login to the gui on it's own as a user, none of the files will launch.  The password prompt never comes up in my normal id and whether as that or logged in as root, each of these type of packages just has the icon spin and spin without actually opening and eventually they quit.

Prior to trying a clean install, I decided to run the live CD (Ubuntu not Kubuntu at the moment).  

So here's a question:   Is there any file I can copy from the live cd over to my portable drive which is being read fine with read and write capability (surprising as I don't think  ntfs-3g is on it) that I might have corrupted or otherwise messed up in some way that might be causing the problem??

AS of now, all of my normal programs run fine but I can't update anything, add any new packages, access any system settings, etc.  Basically anything requiring a password.

And yes, I do have myself and have had for a while in the admin and sudo groups and everything worked fine for a while.  I think I actually messed it up trying to fix another completely different problem.  

Trying to avoid a reinstall (AGAIN!).

myke

---

### Post by OffAxis on 2008-01-30
> each of these type of packages just has the icon spin and spin without actually opening and eventually they quit.


What happens when you try to launch something from the command prompt?
```
sudo apt-get update
```
or
```
sudo nautilus

```
it should kick out an error message to the console.

What does your sudoers file look like (you'll probably have to boot to a live disc for this one)?
```
less /etc/sudoers

```


Does dmesg```

dmesg grep | tail

```
or syslog

```
less /var/log/syslog

```
yield anything interesting?

---

### Post by myke on 2008-01-30
When I try to type anything from the terminal with a sudo command, it simply never brings up the text editor .... it's version of the spinning icon I suppose.   However, on my windows side where I'm at now, I can access and look at any of those files you mentioned (due to a nifty program called 'ext2IFS')  so I'll see what they say.

> # /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Defaults

Defaults	!lecture,tty_tickets,!fqdn

# Uncomment to allow members of group sudo to not need a password
#%sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

I'm going to have to boot back with the live cd to see what I can get out of the syslog file.  I can put the current one in here for you if it'll help but it's really long when I bring it up as a text file in XP.

---

### Post by myke on 2008-01-30
Ok from the terminal running this causes this output:

> sudo: /etc/sudoers is mode 0774, should be 0440

Do I need to chmod the permissions?  And if so how do I do that?   Command line functions are not my specialty.  OR since that may have to be done via command line, how else can it be changed if sudo isn't working??


Running less /var/log/syslog under the terminal does give this output:

> Jan 30 15:49:14 David syslogd 1.4.1#21ubuntu3: restart.
Jan 30 15:49:14 David anacron[5646]: Job `cron.daily' terminated
Jan 30 15:49:14 David anacron[5646]: Normal exit (1 job run)
/var/log/syslog (END)


Your other suggestion produces:

> myke@David:~$ dmesg grep | tail
[   33.444000] Bluetooth: L2CAP ver 2.8
[   33.444000] Bluetooth: L2CAP socket layer initialized
[   33.568000] Bluetooth: RFCOMM socket layer initialized
[   33.568000] Bluetooth: RFCOMM TTY layer initialized
[   33.568000] Bluetooth: RFCOMM ver 1.8
[   38.384000] NET: Registered protocol family 17
[   41.924000] NET: Registered protocol family 10
[   41.924000] lo: Disabled Privacy Extensions
[   52.372000] ath0: no IPv6 routers present
[   52.516000] eth0: no IPv6 routers present

Does any of this give an idea why I might not be able to launch the updater or synaptic or any systems settings panel requiring a password??   If so, is there any way I can fix whatever mess I created??

Right now the updater says there are 11 updates available but when I click the icon it just spins and spins ... and stops!

---

### Post by OffAxis on 2008-01-31
I would definitely change your permissions on the sudoers file.

(you'll probably have to boot to a LiveCD command prompt for this - if you're at the **root **command prompt ignore the sudo)
```
sudo chmod 0440 /etc/sudoers

```

chmod = change file permissions
0440 = read, read, nothing
(ignoring the opening 0) the octal notation is broken down into** User Group Other**. So User gets set to 4 (read only), Group to 4 (read only), and Other to 0 (nothing).

Once set, you can check it with 
```
ls -l /etc/sudoers
```

it should return 
```
-r--r----- 1 root root 496 2008-01-27 15:13 /etc/sudoers
```

Notice the **user=root** and **group =root**. If those are anything else, you'll need to change them
```
sudo chwon root:root /etc/sudoers
```
chown = change ownership
root:root = user:group

That's it for that.
reboot.
...
Is sudo still a problem?

---

