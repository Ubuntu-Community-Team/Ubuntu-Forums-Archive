---
title: "sudo su --&gt; &quot;Sorry, try again.&quot;"
date: 2017-06-02
forum: General Help
---

### Post by david144 on 2017-06-02
Hi I'm running 16.04.2 LTS, uname -r shows 4.4.0-78-generic, and I don't know why but when I try to run: ```
sudo su
``` it prompts me three times for my password the first two times saying _*Sorry, try again.*_ the third says _*sudo: 3 incorrect password attempts*_

I've booted from live cd and reset my root password, verified I was in the sudo group, even added myself directly to the sudoers file.

I've purged and reinstalled sudo and ubuntu-minimal

From root I've changed my user password

At this point I'm stuck and haven't found anything else in my searches to resolve this issue. I can re-install from scratch but was looking to see if there was some other simple fix first.

The hard drive was full at one point but I cleaned up space, removed all the old images and headers, apt-get update && apt-get upgrade work correctly, and I've even run a reinstall_all.sh.

I'm not sure what my /etc/pam.d files should all look like, if anyone has a list of files and their contents that I could compare against I would appreciate it :D

Thanks everyone for any assistance you can provide.

---

### Post by QIII on 2017-06-02
What do you mean when you say that you are entering your root password?

---

### Post by TheFu on 2017-06-02
Does **sudo -i** work? 
Or **sudo -s**?

---

### Post by david144 on 2017-06-03
> **QIII said:**
> What do you mean when you say that you are entering your root password?

"[COLOR=#000000]booted from live cd and reset my root password"

boot from live cd
mount -o rw /dev/sda1 /mnt
chroot /mnt
passwd
set the password

"[/COLOR][COLOR=#000000]From root I've changed my user password"

after rebooting from the livecd back to the hard drive, I logged in as root and set my password
passwd <username>

[/COLOR]

> **TheFu said:**
> Does **sudo -i** work? 
Or **sudo -s**?

nope, both just continue to prompt for password

---

### Post by QIII on 2017-06-03
It is not advisable to use a root account.  I would disable it ASAP.

When you use 

```
sudo su
```

are you entering YOUR user's password or the password you set up for root?

---

### Post by leunam12 on 2017-06-03
It is not advised to log in as root. If you still want to do it and you understand and accept the risks, you must be aware that your sudo password and your root password are not the same. You have to use sudo and setup a root password first:```
username@adsfPC-2:~$ sudo passwd root
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully

```then, all you have to do is type su and press enter and type your root password. Again, not advisable, very easy to make fatal mistakes even if you are an advanced user. Backup your whole system before attempting to do anything.

---

### Post by david144 on 2017-06-04
> **QIII said:**
> **It is not advisable to use a root account.  I would disable it ASAP.**

When you use 

```
sudo su
```

are you entering YOUR user's password or the password you set up for root?

I realize that, and hence why I'm trying to figure out what is wrong with my sudo. When I 'su root' I'm typing in the root password

When I 'sudo -i' or 'sudo su' I am using my user password and it keeps prompting and fails (and I have tried the root password,  no success)


When I 'sudo su' I get this in my auth.log:
```
Jun  4 06:30:26 server1 sudo: PAM (sudo) illegal module type: gJun  4 06:30:26 server1 sudo: PAM (sudo) no control flag supplied
Jun  4 06:30:26 server1 sudo: PAM (sudo) no module name supplied
Jun  4 06:31:50 server1 sudo: pam_unix(sudo:auth): auth could not identify password for [***<username>***]
Jun  4 06:31:50 server1 sudo:   ***<username>*** : 1 incorrect password attempt ; TTY=pts/1 ; PWD=/home/***<username>*** ; USER=root ; COMMAND=/bin/su
```

I canceled out after 1 attempt just to get the log entries but it fails 3 times normally before quitting

> **leunam12 said:**
> It is not advised to log in as root. If you still want to do it and you understand and accept the risks, you must be aware that your sudo password and your root password are not the same. You have to use sudo and setup a root password first:```
username@adsfPC-2:~$ sudo passwd root
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully

```then, all you have to do is type su and press enter and type your root password. Again, not advisable, very easy to make fatal mistakes even if you are an advanced user. Backup your whole system before attempting to do anything.

I don't want to su to root, I want to use sudo, but sudo is broken.

Hopefully my replies above will now serve to explain what is happening, I should have included auth.log from the begining sorry about that.

Now given I know my root password and I can su root successfully, the problem seems to be with pam but I don't know what I should be looking at to troubleshoot it.

---

### Post by oldos2er on 2017-06-04
Very strange. I googled "server1 sudo: PAM (sudo) illegal module type: gJun  4 06:30:26 server1 sudo: PAM (sudo) no control flag supplied" but google has nothing for it.

Can you login as root (just for now) and try reinstalling sudo? ```
apt install --reinstall sudo
``` Whether or not this will help, I can't say for sure.

---

### Post by TheFu on 2017-06-04
Did sudo ever work?
Has the sudoers file (s) been modified?  Can you restore from a backup?
Can you post the non-comment parts of the sudoers file and 'id' output,  please?

Is there a reason that PAM would have been touched?  Doing any LDAP or SSO or ... ?

---

### Post by david144 on 2017-06-04
> **oldos2er said:**
> Very strange. I googled "server1 sudo: PAM (sudo) illegal module type: gJun  4 06:30:26 server1 sudo: PAM (sudo) no control flag supplied" but google has nothing for it.

Can you login as root (just for now) and try reinstalling sudo? ```
apt install --reinstall sudo
``` Whether or not this will help, I can't say for sure.

Yep tried that already:

> **david144 said:**
> 
I've purged and reinstalled sudo and ubuntu-minimal

---

### Post by oldos2er on 2017-06-04
Maybe TheFu is on the right track.

---

### Post by david144 on 2017-06-04
> **TheFu said:**
> Did sudo ever work?
Has the sudoers file (s) been modified?  Can you restore from a backup?
Can you post the non-comment parts of the sudoers file and 'id' output,  please?

Is there a reason that PAM would have been touched?  Doing any LDAP or SSO or ... ?

sudoers:
```
Defaults        env_reset
Defaults        mail_badpass
Defaults        secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin"
root    ALL=(ALL:ALL) ALL
%admin ALL=(ALL) ALL
%sudo   ALL=(ALL:ALL) ALL
```

id output for my user:
```
uid=1001(***<username>***) gid=1001(***<username>***) groups=1001(***<username>***),27(sudo),33(www-data),1002(wwwsamba)
```

I've tried adding myself directly to the sudoers file with no success so I removed it since that doesn't seem to be the issue.

Sudo worked when I built the system, and did the last do-release-upgrade, but then somewhere along the line my drive filled up and even after purging and cleaning up the old images and headers to restore space the sudo didn't recover

---

### Post by TheFu on 2017-06-04
Thanks for the info.

You posted this:
```
Defaults        env_resetDefaults        mail_badpass
```

Is that accurate or did the file get corrupted?  Should be:

```
Defaults        env_reset
Defaults        mail_badpass
``` though I've not used mail_badpass.
No #includedir /etc/sudoers.d?   that isn't a comment.  Bad updates inside that directory will break sudo. I've caused it a few times myself and had to hack into a box 4 times (i couldn't have messed up the tiny change! ;) ) right before teaching a Linux admin class.

Still just guessing ... 

Do the `hostname` cmd, hostname file and /etc/hosts all agree on the hostname?  I've seen where sudo got tied to the hostname and wouldn't work if things changed halfway.

Also rm ~/.sudo_as_admin_successful

do-release-upgrade?  I don't do that on desktops.  Too many issues, IMHO.

---

### Post by david144 on 2017-06-04
> **TheFu said:**
> Thanks for the info.

You posted this:
```
Defaults        env_resetDefaults        mail_badpass
```


Woops I got a little delete happy in my notepad paste from my cat results


> **TheFu said:**
> No #includedir /etc/sudoers.d?   that isn't a comment.  Bad updates inside that directory will break sudo. I've caused it a few times myself and had to hack into a box 4 times (i couldn't have messed up the tiny change! ;) ) right before teaching a Linux admin class.
oh yep that's in there at the end of the file, sorry I saw it and thought comment not reading the line right above it

> **TheFu said:**
> Still just guessing ... 

Do the `hostname` cmd, hostname file and /etc/hosts all agree on the hostname?  I've seen where sudo got tied to the hostname and wouldn't work if things changed halfway.

Also rm ~/.sudo_as_admin_successful

do-release-upgrade?  I don't do that on desktops.  Too many issues, IMHO.

my hosts has both the fqdn and the hostname on the loopback IP, and the command and file all match, good thing to check I welcome guesses at this point ;-)

It's a ubuntu-minimal server build, but yea I hear you about the do-release-upgrade. Typically I wouldn't deal with upgrading and just download a new ISO and do a fresh rebuild and move my content over, but this is my girlfriend's web-server on my home esxi environment so I don't usually get involved with it unless she has problems managing it.

Any thoughts on the pam errors in the auth.log?

Thanks

---

### Post by david144 on 2017-06-04
Got it! :) > PAM (sudo) illegal module type: [SIZE=3]_**[COLOR=#FF0000]g[/COLOR]**_[/SIZE]Jun  4 06:30:26 server1 sudo: PAM (sudo) no control flag supplied


"grep g /etc/pam.d/*"  yielded:


./common-session-noninteractive:g

first line of the file somehow have a g in it LOL

fixed and restarted sudo and I'm back in business!

Thanks all for helping look at the problem

---

