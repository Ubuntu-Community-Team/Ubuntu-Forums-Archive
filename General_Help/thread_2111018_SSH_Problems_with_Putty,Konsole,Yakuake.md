---
title: "SSH Problems with Putty,Konsole,Yakuake"
date: 2013-01-31
forum: General Help
---

### Post by Xplorer4x4 on 2013-01-31
I am setting up a VPS and have the options Ubuntu 10.04 LTS 64bit Lucid or Ubuntu 11.10 64bit Oneric. I decided to go with Lucid since it was LTS(although I originally had installed Oneric as I read the support till dates wrong at a glance). Anyways, I find logging in as root is the only way to have a fully functional terminal. For example, I installed bash-completition, and now the tab key does auto complete as I am used to in (Kubuntu) Precise/Quantal. If I log in to a user account, tab simply inserts a tab. If I am logged in as root, I can hit the up key on the keyboard to cycle through previous commands. As a User it just prints want I believe is machine code like "$ ^[[A^[[A^[[B^[[B^[[D" This happens weather I use  Putty,Konsole,or Yakuake(default). Since the problem happens on both Lucid and Oneric I assume the problem is on my end.

---

### Post by SeijiSensei on 2013-01-31
It sounds like there are some weird settings in your home directory.

Try creating a new, non-administrative user either with the graphical tool or by running adduser at the prompt.  Log into that account.  Do you still have the same problems?

---

### Post by Xplorer4x4 on 2013-01-31
Thanks, that helped me identify the problem. I am trying to set up a VPS but automate the set up through a bash script. I know adduser is the proper way, and useradd is not, but I thought it would be sufficient in this case. So that brings me to the next question..how do i properly add a user and their password via a bash script?

---

### Post by steeldriver on 2013-01-31
if you used 'useradd' maybe your login shell is set to /bin/sh not /bin/bash? that will likely have given you a dash shell - you can probably fix that part of it with

```
usermod -s /bin/bash *username*
```I think

---

### Post by SeijiSensei on 2013-01-31
Run "man adduser" for details.  Using the man command is always the first step toward knowledge.

---

### Post by Xplorer4x4 on 2013-01-31
> **steeldriver said:**
> if you used 'useradd' maybe your login shell is set to /bin/sh not /bin/bash? that will likely have given you a dash shell - you can probably fix that part of it with

```
usermod -s /bin/bash *username*
```I think

Thanks, that fixed it!

> **SeijiSensei said:**
> Run "man adduser" for details.  Using the man command is always the first step toward knowledge.
Here we go...

Man pages are only as useful as the time and effort put in to them, and the users ability to understand them. Google tends offer a far better explanation of the command and the options in terms of what the average user can understand.In this case I will need to use "--shell SHELL" which is described as "Use SHELL as the user's login shell, rather than the default specified by the configuration file." On my initial reading of this, for some reason it did not process that it was speaking of the different shell environments. However, googleing for a tutorial on adduser would probably return a more descriptive defection of "--shell." I goggled something to the extent of "automaticly add user in bash script" and came up with a number of options but this seemed to be the most practical. 

Also in this case, I tried 
```
useradd -m -p -s /bash/shell username
```
When I issue this or 
```
useradd -m -p -s --shell /bash/shell username
```
It spits out the help dialog.

Edit, over looked the -p option:
```
useradd -D -s /bin/bash -m -p setapassword username
```

---

