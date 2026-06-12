---
title: "Mount a Truecrypt volume at login"
date: 2013-03-28
forum: General Help
---

### Post by kinu on 2013-03-28
Hi,

It took some time and internet research to me to do this, so I want to share it. I don't know if this is the right forum, so please don't hesitate to tell me or move it.

I have read [an article about encryption methods comparison]("http://www.linuxuser.co.uk/reviews/the-best-file-encryption-software-in-open-source"), so I want data security, but max speed (truecrypt, as they said). After reading the article, I want to avoid ecryptfs, so no default Ubuntu home encryption. And I have my system (Linux Mint XFCE 14) up and running, and I didn't want to re-install and learn to encrypt my home partition with LUKS (by now).

What I want to acomplish is to mount a truecrypt volume at login, using the same user password, to store my .mozilla, .config/chromium, .filezilla, .teamviewer, or maybe my Dropbox folder, and all the data I can consider private, safe with ease.

First, I have had installed Truecrypt. I did what is told [here]("http://ubuntuguide.net/install-truecrypt-in-ubuntu-12-10-12-04").

Then I created a truecrypt volume in my home folder (/home/YOURUSER), called, lets say, *mysecrets.tc*.:rolleyes:, using the same password I use to login.

Mount it with the Truecrypt GUI and copy some files here, just to test they will be there when you finish this.

Add a directory in my home folder, called *Private* or *MySecrets *...

Then I created a group called truecrypt, add my user, and allow all the people on this group to use truecrypt without admin password. I saw it in the [ArchLinux wiki]("https://wiki.archlinux.org/index.php/TrueCrypt#Method_1_.28Add_a_truecrypt_group.29"). As root, I did:
```
# groupadd truecrypt
```
Then edit the sudoers file (I don't know how to use vi, shame on me)
```
# EDITOR=nano visudo
```
Adding this
```
# Users in the truecrypt group are allowed to run TrueCrypt as root.
%truecrypt ALL=(root) NOPASSWD:/usr/bin/truecrypt
```
And then adding my user to the group
```
# gpasswd -a YOURUSER truecrypt
```

OK. So, this is what I do to mount it at login:

First, install pam_mount
```
sudo apt-get install libpam-mount
```

Second, modify* /etc/security/pam_mount.conf.xml*, adding this in the volume part (inmediatly after *<!-- pam_mount parameters: Volume-related -->*)
```
<cryptmount>truecrypt --text --protect-hidden=no --keyfiles="" %(VOLUME) %(MNTPT)</cryptmount>
<cryptumount>truecrypt -d</cryptumount>
<volume fstype="crypt" noroot="1" path="/home/YOURUSER/mysecrets.tc" mountpoint="/home/YOURUSER/MySecrets" />
```
 I want to apologize because I got this code long time ago, and I don't remember where I got it (maybe from [here]("https://wiki.archlinux.org/index.php/Talk:TrueCrypt")).

Reboot, login, and you must have your truecrypt volume mounted in *MySecrets* directory. Just jump to it and test the test files you copied before.

Then, to encrypt something (example, *.mozilla* directory) I do:
```
mv /home/YOURUSER/.mozilla /home/YOURUSER/MySecrets/.mozilla
ln -s /home/YOURUSER/MySecrets/.mozilla /home/YOURUSER/.mozilla
```

This was working for me in an old Arch install, and now in my brand new installed Ubuntu based distribution.

Regards.

---

