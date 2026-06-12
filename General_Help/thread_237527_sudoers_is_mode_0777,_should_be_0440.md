---
title: "sudoers is mode 0777, should be 0440"
date: 2006-08-16
forum: General Help
---

### Post by PaulFXH on 2006-08-16
I know this message is something to do with permissions but, I believe, I have set myself the maximum of permissions using:

```
sudo -s -H
```
and
```
sudo chmod -R 777 /......./
```

What I had tried before I got this message was:

```
sudo mount -a
```

Because of this, when I subsequently try to use the dpkg-reconfigure command, I'm told that this command is not found. However, I believe it is not broken as it works fine in others contexts.

Please help me extricate myself from this dilemma

---

### Post by Ramses de Norre on 2006-08-16
```
sudo chmod 0440 /etc/sudoers
```
And did you make everything 777 on your system?? Because that will mess up a lot..

---

### Post by PaulFXH on 2006-08-16
Thanks for the reply.
Well, if running the command
```
sudo chmod -R 777 /......./
```
makes everything 777, then yes I did.

Can ou please explain what you mean by > that will mess up a lot..
Are you referring to the possibility of future errors or to damage already done.
Please note that I have been using Ubuntu for less than a month and am still on a very steep part of the learning curve.

Thanks

---

### Post by PaulFXH on 2006-08-16
I tried the command you suggested:
```
sudo chmod 0440 /etc/sudoers
```

but it does not eliminate the message I get after running 
```
sudo mount -a
```

In other words, I just can't get away from this message:
```
sudoers is mode 0777, should be 0440
```

Perhaps this is one of the things that's "messed up".

Please let me know what you think

---

### Post by cptnapalm on 2006-08-16
Well, the numbers basically break down as follows:
Owner can execute, read and write anything.
Group can execute, read and write anything.
ANYONE can execute, read and write anything.

If I'm not mistaken, anyone who blinks at the computer has root powers.  Plus the vast multitude of text files, which are not executables, your machine now thinks are executables and will try to run them like programs.  This would include photographs, configuration files, etc.

I think you may have hosed your installation.

Fear Root.

---

### Post by PaulFXH on 2006-08-16
Thanks for your reply.
Well, I guess without errors we would never learn.
Looks like I'm going to have to re-install Ubuntu.
However, I'm still a little puzzled as to how this problem arose. I'd really like to know how to avoid it next time.

---

### Post by peabody on 2006-08-16
> **PaulFXH said:**
> Thanks for your reply.
Well, I guess without errors we would never learn.
Looks like I'm going to have to re-install Ubuntu.
However, I'm still a little puzzled as to how this problem arose. I'd really like to know how to avoid it next time.

Use ls with the -l option to look at filesystem permissions.  ls -l /etc/sudoers would tell you the permissions.  use "ls -ld" to look at directory permissions.

There's two possible reasons it isn't working.  One of the them is probably due to the fact that you screwed the permissions on sudoers so sudo can't work period, meaning "sudo chmod 0440 /etc/sudoers" won't have any effect.   This is kind of a chicken and egg problem since the root user is disabled by default in Ubuntu, so once you break sudoers, you've no way to obtain root privileges.  The only way to fix this is to boot into the rescue system and fix it from the shell there.  This is why it's very, very, VERY important that "visudo" be the only utility that's used to edit the sudoers file.  It scans the file before saving to make sure that there aren't any errors that would prevent sudo from working and it also employs file locking while editing it.

Another reason you keep getting that message might due to /etc being writable by everyone.  Lot's of people don't know this, but if a directory is writable by everyone, anyone can delete anything from the directory regardless of the file permissions on the file in question, which of course would include /etc/sudoers.  The work around for this (if you simply must have a directory world writable) is to set the sticky bit on the directory (1755, though this is something you should never have to do, and shouldn't do, for /etc.  The permissions for /etc should be 755).

Learning the hard way is always the best.  Hopefully however you'll never have to learn "sudo rm -fr /" the hard way ;).  Cheers.

---

### Post by PaulFXH on 2006-08-16
Thanks for the explanation.
I've actually re-installed Ubuntu and everything's back to normal (at least it looks normal enough up to now).

---

### Post by mlind on 2006-08-16
> **PaulFXH said:**
> I know this message is something to do with permissions but, I believe, I have set myself the maximum of permissions using:

```
sudo -s -H
```
and
```
sudo chmod -R 777 /......./
```

What I had tried before I got this message was:

```
sudo mount -a
```

Because of this, when I subsequently try to use the dpkg-reconfigure command, I'm told that this command is not found. However, I believe it is not broken as it works fine in others contexts.

Please help me extricate myself from this dilemma

What was the reasoning behind this decision? You shouldn't (ever) need to manually change permissions outside of your $HOME folder without _very_ good reason..

---

### Post by PaulFXH on 2006-08-17
> What was the reasoning behind this decision?

I'm not sure there WAS any reasoning, just frustration at seeing the "permission denied" message.
Note, however, that the partition where I have Ubuntu is lightly loaded and used for "amusement" only. So, if I need to reinstall, it's not a tragedy.
Nevertheless, it does appear that my knowledge of the whole permission thing is lacking. I would appreciate hearing from anybody useful links to get up to speed on this.

---

### Post by Subbu.exe on 2006-08-17
> **PaulFXH said:**
> Thanks for the explanation.
I've actually re-installed Ubuntu and everything's back to normal (at least it looks normal enough up to now).

Well.. Thats was a Bad Idea..
I Usually boot up in Rescue Mode (thru GRUB)
Press Control+D, that gives me ROOT Access

I Then Run **chmod 440 /etc/sudoers**

NOW Everything is back to normal

---

### Post by PaulFXH on 2006-08-17
Let's look on the bright side........I'm sure to mess up again when I can try out your suggestion:D 

BTW, why can I not just run the ```
chmod 440 /etc/sudoers

``` command by using ```
sudo -s -H
``` in a terminal rather than going through recovery mode?

---

### Post by mlind on 2006-08-17
> **PaulFXH said:**
> Let's look on the bright side........I'm sure to mess up again when I can try out your suggestion:D 

BTW, why can I not just run the ```
chmod 440 /etc/sudoers

``` command by using ```
sudo -s -H
``` in a terminal rather than going through recovery mode?

If /etc/sudoers is messed up, sudoing doesn't work and normal users cannot aquire temporary root privileges.

---

### Post by Martin Olof Andersson on 2007-03-11
I did that mistake as well, to change the right to 777 instead of 440. Some may think **WHY** on earth did you do that... it was simply because I needed to add a line to "sudoers" it and found erroneous instructions on the Internet.

Luckily the solution of getting back 440 rights bac to "sudoers" is very, very simple. 
1. Reboot the PC
2. In grub, select Recuvery Mode
3. You will get a black command line window and you will have root rights
4.  type **chmod 0440 /etc/sudores**

This worked nicely for me. No need to do any reinstall. Hope it can be helpful to someone else too.

---

### Post by Ramses de Norre on 2007-03-11
To correct the erroneous info, you should only modify your sudoers file with the **visudo** command, it will use the editor which is defined by the EDITOR environment variable.
So if you want to use gedit you can do this: ```
export EDITOR=gedit && sudo visudo
```
You can set gedit (or any other editor) as the default with ```
sudo update-alternatives --config editor
```

---

### Post by bonfire89 on 2008-06-25
I eventually solved this by using the live cd and mounting the install I was trying to fix

---

