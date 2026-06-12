---
title: "Help me! Cannot sudo in graphical environment anymore."
date: 2008-01-23
forum: General Help
---

### Post by ThorX89 on 2008-01-23
Hi. I have a serious problem right now. I cannot sudo nor gksudo in ubuntu's GUI anymore, but I can do it in terminal, though. (the one I get from pressing ctrl+alt+f1 - gnome-terminal doesn't accept my password either :-( ) Anyone know how to solve this. I cannot even update my system like this.

---

### Post by mali2297 on 2008-01-23
Type
```

whoami

```
in gnome-terminal and in the virtual console. 

Are you the same?

---

### Post by dannyboy79 on 2008-01-23
it sounds to me like you may have messed up your sudoers file.

load up in recovery mode and put in this command

sudo usermod -G admin <username>
<username> being the one that you're having problems with.

---

### Post by capink on 2008-01-23
> **dannyboy79 said:**
> 

sudo usermod -G admin <username>
<username> being the one that you're having problems with.

This has to be modified into:

```
sudo usermod [COLOR="Red"]-a[/COLOR] -G admin <username>
```

Otherwise the user is removed from all the groups he was subscribed to except the admin group and his own account group.

Or to avoid the complexity of the usermod command, one can simply use:

```
sudo adduser <username> <groupname>
```

---

### Post by dannyboy79 on 2008-01-23
> **capink said:**
> This has to be modified into:

```
sudo usermod [COLOR="Red"]-a[/COLOR] -G admin <username>
```

Otherwise the user is removed from all the groups he was subscribed to except the admin group and his own account group.

Or to avoid the complexity of the usermod command, one can simply use:

```
sudo adduser <username> <groupname>
```

very true, thank you for corrected me.

---

### Post by ThorX89 on 2008-01-23
Sry guys, it didn't work. Any other ideas? And BTW I discovered another interesting fact here - I can su to other users (I have 2 other users who are not allowed to sudo) in gnome-terminal but I can't get back to my original one (the one that can, supposedly, sudo). The funny thing is that everything works  fine when in CLI and that my password does work for logging into the GUI but not anymore from that point forward. Thanks for trying to help me BTW. ;-)

---

### Post by ThorX89 on 2008-01-23
yep

---

### Post by torea on 2008-01-23
I had the same or similar problem : sudo doesn't accept my password in terminal or GUI applications but su command accept it.
capink solution just worked for me but had to be used as:
```

su
usermod -a -G admin <username>

```

---

### Post by dannyboy79 on 2008-01-23
> **torea said:**
> I had the same or similar problem : sudo doesn't accept my password in terminal or GUI applications but su command accept it.
capink solution just worked for me but had to be used as:
```

su
usermod -a -G admin <username>

```

when you're in recovery mode you shouldn't need to su first, that's the point of recovery mode, you can edit anything. maybe the OP missed that fact that I said he needed to be booted into recovery mode. which also means that you shouldn't have to use sudo as I first suggested.

---

### Post by torea on 2008-01-23
sorry.. I didn't see your line about loading the recovery mode!

---

### Post by ThorX89 on 2008-01-24
I discovered my password was somewhat longer than it is standard so I shortened it in console and now it works again. I only wonder why it used to work all the time up until recently.

---

