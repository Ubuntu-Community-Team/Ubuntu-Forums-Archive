---
title: "Ubuntu 19.04 Sudo Issues"
date: 2019-06-04
forum: General Help
---

### Post by kiloblaster on 2019-06-04
Hello and thank you for your time! 

About a month ago I installed Ubuntu 19.04 on my PC. I use the terminal quite a bit and wanted to start installing things through that.  Since by default Ubuntu doesn't set a root password, I went to use the SUDO command. 

I get this error message: 

sudo 
[INDENT]Command 'sudo' not found, but can be installed with:

sudo apt install sudo       # version 1.8.27-1ubuntu1, or
sudo apt install sudo-ldap  # version 1.8.27-1ubuntu1
[/INDENT]

This is quite entertaining because without that I can't install things. Oddly enough, I can install apps through the software store. 

Current version of Ubuntu: 
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 19.04
Release:	19.04
Codename:	disco

Any ideas?

---

### Post by Rubi1200 on 2019-06-04
Hi and welcome to the forums :-)

When you installed 19.04 you created a username and password. That password is the root password, so to speak, meaning when you run a command requiring elevated privileges you enter the password you created and use to login.

For example, if I want to check the layout of my disks:

```
sudo fdisk -l
```

You will be prompted to enter the password (note that it will not echo on the screen but just type and then Enter).

Or, this:

```
sudo apt update
```

Please try this and report back if there are still problems.

---

### Post by deadflowr on 2019-06-05
Did you ever run sudo before now?

---

### Post by yancek on 2019-06-05
>  I went to use the SUDO command. 

A point of clarification, there is no "SUDO" command, it is ALWAYS ALL lower case letters:  sudo
Not sure if this was your problem but based on your post, I wondered.

---

### Post by kiloblaster on 2019-06-05
Thanks for the information! When I run sudo apt update I get the message below. I am logged into the original username and password I created during setup as well.  
sudo 
[INDENT]Command 'sudo' not found, but can be installed with:

sudo apt install sudo       # version 1.8.27-1ubuntu1, or
sudo apt install sudo-ldap  # version 1.8.27-1ubuntu1
[/INDENT]

> **yancek said:**
> A point of clarification, there is no "SUDO" command, it is ALWAYS ALL lower case letters:  sudo
Not sure if this was your problem but based on your post, I wondered.


Yeah, all lower case.

> **Rubi1200 said:**
> Hi and welcome to the forums :-)

When you installed 19.04 you created a username and password. That password is the root password, so to speak, meaning when you run a command requiring elevated privileges you enter the password you created and use to login.

For example, if I want to check the layout of my disks:

```
sudo fdisk -l
```

You will be prompted to enter the password (note that it will not echo on the screen but just type and then Enter).

Or, this:

```
sudo apt update
```

Please try this and report back if there are still problems.

Thanks for the information! When I run sudo apt update I get the message  below. I am logged into the original username and password I created  during setup as well.  
sudo 
[INDENT]Command 'sudo' not found, but can be installed with:

sudo apt install sudo       # version 1.8.27-1ubuntu1, or
sudo apt install sudo-ldap  # version 1.8.27-1ubuntu1
[/INDENT]

> **deadflowr said:**
> Did you ever run sudo before now?

This is the first time after the installation. Everything else I used the store.

---

### Post by deadflowr on 2019-06-05
Hmm, odd.
What you can try is to install the package management utility synaptic and install sudo from there.
Since as you posted you have no problem installing software from the Software store.

Not sure where it went wrong.
Might be interesting to see the packaging log history at
/var/log/apt/history.log (and maybe any history.log.gz archives if any exist.)
Not that it will give any sort of clear answer as it would be one thought among many as to what's happeing.

Since you can install I assume your user is in the admin group sudo and that sudo exists as a group.
(On Ubuntu the admin user group is sudo)
Easy to find out by running the command
```
id
```
which will show all the groups the user is currently in or belongs to.
See if sudo is listed.

Sorry for rambling mess.

---

### Post by kiloblaster on 2019-06-05
> **deadflowr said:**
> Hmm, odd.
What you can try is to install the package management utility synaptic and install sudo from there.
Since as you posted you have no problem installing software from the Software store.

Not sure where it went wrong.
Might be interesting to see the packaging log history at
/var/log/apt/history.log (and maybe any history.log.gz archives if any exist.)
Not that it will give any sort of clear answer as it would be one thought among many as to what's happeing.

Since you can install I assume your user is in the admin group sudo and that sudo exists as a group.
(On Ubuntu the admin user group is sudo)
Easy to find out by running the command
```
id
```
which will show all the groups the user is currently in or belongs to.
See if sudo is listed.

Sorry for rambling mess.

No problem at all, I just appreciate the help and yes, it's very strange.  Normally I'm a RedHat / CentOS user and this was quite the interesting problem.  I will give that a shot tonight, thanks again for the quick reply!

---

### Post by Rubi1200 on 2019-06-05
Let's also see the output from these two commands please:

```
compgen -u
```

and

```
compgen -g
```

Thanks.

---

### Post by kpatz on 2019-06-05
If you have a dual boot setup so Grub gives a menu before you boot, you can select recovery mode from the menu.  If you don't get a menu on boot, holding shift key (on BIOS systems) or hitting Esc at the start of the boot (UEFI) should get you the grub menu.  (Note, I've tried to do this unsuccessfully on my 19.04 VM).

Select "Advanced Options for Ubuntu" from the grub menu.  From there, select "Ubuntu,with Linux (whatever kernel version you have), (recovery mode)"

You'll boot into a menu.   Select "Network" to enable networking, so you can get to the internet, then select "root" to get a root shell.  Hit Enter to continue.

From this root shell, you can **apt install sudo** to get sudo back.

Ctrl-D when finished, and you can resume normal boot from there.  It's possible the GUI won't load properly (screen resolution etc.) when booting this way, if this happens, just reboot again.  Alternatively, you could have issued a **shutdown -r now **command from the root shell.

---

### Post by kiloblaster on 2019-06-05
> **kpatz said:**
> If you have a dual boot setup so Grub gives a menu before you boot, you can select recovery mode from the menu.  If you don't get a menu on boot, holding shift key (on BIOS systems) or hitting Esc at the start of the boot (UEFI) should get you the grub menu.  (Note, I've tried to do this unsuccessfully on my 19.04 VM).

Once you boot into recovery mode, you should get a root shell.  From there, you can "apt install sudo" to get sudo back.

Fantastic, I'll give this a shot as well. I am using grub with a dual boot for Windows 10. 

Thank you!

---

### Post by kpatz on 2019-06-05
I just updated my post with more details on what to expect when you select advanced mode and how to get to a root prompt with the network enabled.

---

### Post by deadflowr on 2019-06-05
From recovery mode before selecting root shell select the enable networking option first.
this will do two things.
1)obviously, it sets networking so you can fetch online internet packages.
2)more, importantly it resets the file system to read/write.
Recovery mode runs by default in read-only so in order to install anything you must reset it.
Enable networking does this automatically so no need to tinker any command lines.

But +1 to this method to install/reinstall sudo.
Fairly quick and easy.

Edit: 
> I just updated my post with more details on what to expect when you select advanced mode and how to get to a root prompt with the network enabled.

I see that too now.
Good post update.

I guess I can say ninja'd by kpatz.

---

### Post by Rubi1200 on 2019-06-05
I would be curious to try and figure out why sudo is not installed in the first place but I see the general consensus is in favour of just reinstalling.

What does this show?

```
ls -l /usr/bin/sudo
```

Plus output from commands in my last post?

---

### Post by CatKiller on 2019-06-05
> **Rubi1200 said:**
> I would be curious to try and figure out why sudo is not installed in the first place but I see the general consensus is in favour of just reinstalling.

What does this show?

```
ls -l /usr/bin/sudo
```

Plus output from commands in my last post?

Another option for a cause is that their PATH doesn't include /usr/bin for some reason.

---

### Post by kpatz on 2019-06-05
> **CatKiller said:**
> Another option for a cause is that their PATH doesn't include /usr/bin for some reason.On my 19.04 install sudo is in both /bin and /usr/bin.

Also, the shell help feature is smart enough to detect this and will give a different error message if you leave /bin or /usr/bin out of the PATH.  It will tell you what locations sudo is in, if it's there at all.

Besides, if /bin and /usr/bin are omitted from the PATH, most other commands won't work without fully qualifying their path (like ls or grep), not just sudo.

I think the OP accidentally uninstalled sudo while messing with apt or synaptic.

---

### Post by CatKiller on 2019-06-05
> **kpatz said:**
> I think the OP accidentally uninstalled sudo while messing with apt or synaptic.

I agree that that's the most likely from the information we have so far. Thinking of as many possible causes as you can for a particular behaviour is good practise, that's all.

---

### Post by kiloblaster on 2019-06-05
> **Rubi1200 said:**
> I would be curious to try and figure out why sudo is not installed in the first place but I see the general consensus is in favour of just reinstalling.

What does this show?

```
ls -l /usr/bin/sudo
```

Plus output from commands in my last post?

ls -l /usr/bin/sudo
ls: cannot access '/usr/bin/sudo': No such file or directory

---

### Post by kiloblaster on 2019-06-05
> **kpatz said:**
> On my 19.04 install sudo is in both /bin and /usr/bin.

Also, the shell help feature is smart enough to detect this and will give a different error message if you leave /bin or /usr/bin out of the PATH.  It will tell you what locations sudo is in, if it's there at all.

Besides, if /bin and /usr/bin are omitted from the PATH, most other commands won't work without fully qualifying their path (like ls or grep), not just sudo.

I think the OP accidentally uninstalled sudo while messing with apt or synaptic.

No, this is a fresh install.  Why would I accidentally remove it?  Also, I don't have synaptic installed.

---

### Post by kiloblaster on 2019-06-05
> **kpatz said:**
> I just updated my post with more details on what to expect when you select advanced mode and how to get to a root prompt with the network enabled.

Excellent, thanks. 

I followed the steps and I got into recovery mode.  The odd thing is, its saying that sudo is already installed so apt install sudo did not work with root.

---

### Post by kiloblaster on 2019-06-05
> **kpatz said:**
> On my 19.04 install sudo is in both /bin and /usr/bin.

Also, the shell help feature is smart enough to detect this and will give a different error message if you leave /bin or /usr/bin out of the PATH.  It will tell you what locations sudo is in, if it's there at all.

Besides, if /bin and /usr/bin are omitted from the PATH, most other commands won't work without fully qualifying their path (like ls or grep), not just sudo.

I think the OP accidentally uninstalled sudo while messing with apt or synaptic.

from the bin folder:

ls | grep sudo[INDENT]cvtsudoers
sudoedit
sudoreplay
[/INDENT]

From the /usr/bin
ls | grep sudo

[INDENT]cvtsudoers
sudoedit
sudoreplay
[/INDENT]

And the information from the id

id=1000(kiloblaster) gid=1000(kiloblaster) groups=1000(kiloblaster),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),118(lpadmin),129(sambashare)

Which shows sudo.

---

### Post by kiloblaster on 2019-06-05
> **Rubi1200 said:**
> Let's also see the output from these two commands please:

```
compgen -u
```

and

```
compgen -g
```

Thanks.

compgen -u
```
root
daemon
bin
sys
sync
games
man
lp
mail
news
uucp
proxy
www-data
backup
list
irc
gnats
nobody
systemd-timesync
systemd-network
systemd-resolve
messagebus
syslog
_apt
uuidd
avahi-autoipd
usbmux
rtkit
dnsmasq
cups-pk-helper
speech-dispatcher
kernoops
avahi
saned
nm-openvpn
whoopsie
colord
hplip
geoclue
pulse
gnome-initial-setup
gdm
kiloblaster
nvidia-persistenced
systemd-coredump
[/INDENT]

compgen -g
[INDENT]root
daemon
bin
sys
adm
tty
disk
lp
mail
news
uucp
man
proxy
kmem
dialout
fax
voice
cdrom
floppy
tape
sudo
audio
dip
www-data
backup
operator
list
irc
src
gnats
shadow
utmp
video
sasl
plugdev
staff
games
users
nogroup
systemd-journal
systemd-timesync
systemd-network
systemd-resolve
crontab
messagebus
input
kvm
syslog
bluetooth
ssl-cert
netdev
uuidd
mlocate
avahi-autoipd
rtkit
ssh
lpadmin
scanner
avahi
saned
nm-openvpn
whoopsie
colord
geoclue
pulse
pulse-access
gdm
kiloblaster
sambashare
nvidia-persistenced
systemd-coredump


```

---

### Post by wildmanne39 on 2019-06-05
Hello kiloblaster, in the future instead of creating several posts in a row just include the information all in one post.


Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

Thanks!

---

### Post by kiloblaster on 2019-06-05
> **wildmanne39 said:**
> Hello kiloblaster, in the future instead of creating several posts in a row just include the information all in one post.


Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

Thanks!

Will do, thanks.

---

### Post by deadflowr on 2019-06-06
> **kiloblaster said:**
> Excellent, thanks. 

I followed the steps and I got into recovery mode.  The odd thing is, its saying that sudo is already installed so apt install sudo did not work with root.

in that case run
```
apt install --reinstall sudo
```
that will reinstall it even if already installed.
Run it again from the recovery mode.

---

### Post by drv9977 on 2019-06-06
the root password is the same one you created while installing the ubuntu.

---

### Post by kiloblaster on 2019-06-06
> **deadflowr said:**
> in that case run
```
apt install --reinstall sudo
```
that will reinstall it even if already installed.
Run it again from the recovery mode.

Thank you, I'll give that a shot. : )

---

### Post by kiloblaster on 2019-06-06
> **deadflowr said:**
> in that case run
```
apt install --reinstall sudo
```
that will reinstall it even if already installed.
Run it again from the recovery mode.

Worked great, thanks a lot!  You can close this topic.

---

### Post by Rubi1200 on 2019-06-06
I suppose we will never know what exactly happened that sudo was messed up but at least now you have a functioning box.

Please mark Solved using the Thread Tools at the top of the first post.

Thanks.

---

