---
title: "Administrative Privileges"
date: 2007-01-04
forum: General Help
---

### Post by eskimokisz on 2007-01-04
Hey,

So I just installed Ubuntu alongside XP. Boot up, sign in, everything seems fine. However, when I try to access anything that needs admistrative capabilities (installing software packages, updating, etc.), the "Enter password" dialog appears. I type in my password, and the dialog briefly disappears or reappears. Occasionally it just disappears entirely, but isn't replaced by anything else. What's going on here?

---

### Post by ndube on 2007-01-04
> **eskimokisz said:**
> Hey,

So I just installed Ubuntu alongside XP. Boot up, sign in, everything seems fine. However, when I try to access anything that needs admistrative capabilities (installing software packages, updating, etc.), the "Enter password" dialog appears. I type in my password, and the dialog briefly disappears or reappears. Occasionally it just disappears entirely, but isn't replaced by anything else. What's going on here?

Try updating via the command line.

sudo apt-get update
sudo apt-get upgrade

Then reboot and see if there is any change.

---

### Post by eskimokisz on 2007-01-04
Hey... thanks for the quick reply. sudo apt-get-update works fine, but when I try to upgrade i get the following: 

"Errors were encountered while processing: /var/cache/apt/archives/gdm_2.14.10-0ubuntu1.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)"

What's up with that?

---

### Post by lucky_chouhan on 2007-01-05
Just start as recovery mode and go to settings -> system and users -> select user and click properties and check the box (admin actions or privilageous for this user) save and reboot.

:)

---

### Post by eskimokisz on 2007-01-05
Yeah... I'm in recovery mode (or at least I think I am: I was asked for a root pw, got a terminal prompt, logged back out of the terminal, and the gui loaded. There's no visible difference in the GUI - did I do something wrong?) The point is, can't get into anything under the administration menu, including users and groups. After the first time I'm asked for the pw, it just ignores anything I select that might require it.

---

### Post by Dr0n3 on 2007-01-05
> **eskimokisz said:**
> Yeah... I'm in recovery mode (or at least I think I am: I was asked for a root pw, got a terminal prompt, logged back out of the terminal, and the gui loaded. There's no visible difference in the GUI - did I do something wrong?) The point is, can't get into anything under the administration menu, including users and groups. After the first time I'm asked for the pw, it just ignores anything I select that might require it.

Make sure your user account (I'm talking about non root) has sudo rights. From what I've read you're able to login with root and user account. So I assume that you've got working passwords for both accounts. Do the following

1. on the desktop press alt-f2
2. type **gksu users-admin**
3. enter the root password
4. check the user rights for your account
5. make sure your user has admin rights

That should do it since you're able to initiate a root session in a terminal. So you have to know the password.

---

