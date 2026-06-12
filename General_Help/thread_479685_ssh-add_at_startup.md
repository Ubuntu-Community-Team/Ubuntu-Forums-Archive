---
title: "ssh-add at startup"
date: 2007-06-20
forum: General Help
---

### Post by uric on 2007-06-20
Hi,

I am trying to get ssh-add to work on startup, I have kubuntu, feisty.
I followed this guide [https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

> 
KDE users can also make use of ssh-add:

Open a Konsole session:

      Click on *Kmenu*
      Choose *System*
      Choose *Konsole Terminal Program*

At the command prompt, type:

user@user-computer:~$ ln -s /usr/bin/ssh-add .kde/Autostart

Logout of your KDE session and log back in. A menu will pop up at startup asking for your SSH passphrase.


I have done this, and the link is in the Autostart folder, but I dont get any menu to pop up when I login. What am I doing wrong? plz help.

---

### Post by mitch.c on 2007-06-21
Do one of these three files exist:
```
~/.ssh/id_rsa, ~/.ssh/id_dsa or ~/.ssh/identity
```
In other words, is your secret key where ssh-add expects it to be? If not, then you'll need to pass the filename to ssh-add, which in this case means you'll probably want to create a small shell script and add it to your Autostart directory:
```
#!/bin/bash
/usr/bin/ssh-add /path/to/secret_key
```
You should also check permissions on your secret key... ssh-add ignores secret keys that are readable by anyone other than you, so you may need to do:
```
$ chmod 600 secret_key
```
Hope that helps.

[URL="http://ubuntuforums.org/showthread.php?t=377083"][COLOR="Red"]
UAResolved[/COLOR][/URL]

---

### Post by uric on 2007-06-21
Thank you for your reply,

The path is ~/.ssh/id_dsa. If i run the link in ~/.kde/Autostart/ssh-add from terminal I get.

```
x@core:~/.kde/Autostart$ ./ssh-add
Enter passphrase for /home/x/.ssh/id_dsa:
Identity added: /home/x/.ssh/id_dsa (/home/x/.ssh/id_dsa)
```

So that works, but nothing about entering passphrase when I log in.

 I use the ~/.kde/Autostart with link to yakuake, and it starts up fine.

and permissions is.
```
x@core:~/.ssh$ ls -l
total 16
-rwx------ 1 x x 1203 2007-06-19 22:51 authorized_keys
-rw------- 1 x x  744 2007-06-17 18:11 id_dsa
-rw------- 1 x x  596 2007-06-18 12:34 id_dsa.pub
-rwx------ 1 x x 3806 2007-06-21 16:15 known_hosts
```

---

### Post by mitch.c on 2007-06-21
Hmm. I just tried it with a shell script (my key is on a removable drive) ~/.kde/Autostart
```
#!/bin/bash
/usr/bin/ssh-add /media/USB_DRIVE/.ssh/id_rsa
```
I was prompted for my passphrase as soon as the desktop was built.

What happens if you F2 and then type ssh-add... do you get a GUI prompt for password? You may need to delete keys from the agent first:
```
$ ssh-add -D
```
Try restarting X?

---

### Post by uric on 2007-06-22
First I tried making a script ".kde/Autostart/ssh-add.sh"

```
[#!/bin/bash

/usr/bin/ssh-add /home/x/.ssh/id_dsa
```

That didnt make any difference.

I have tried restarting X, and reboot.

There is no gui if i run ssh-add with F2. Do I need to install a gui for ssh-add?

I tried installing ssh-askpass, it didnt work very well. I guess I could use it, but there seems to be some issues, cause it pops up two windows and one is empty, and it keep popping up infront of the other box where the passphrase should go.

Is there a better gui?


Thanks for helping.

---

### Post by mitch.c on 2007-06-22
I looked to see what package I have installed, it looks like ssh-askpass-gnome. That makes sense, since the dialog box that pops up is gtk style. I guess if you don't mind a gnome app running you could try it.

---

