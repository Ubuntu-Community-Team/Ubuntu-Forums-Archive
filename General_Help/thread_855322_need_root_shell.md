---
title: "need root shell"
date: 2008-07-10
forum: General Help
---

### Post by vcnz on 2008-07-10
Hi,
I've installed the ubuntu ver. 8.04 in my dual boot configuration an my notebook.

It work wonderfull and next step will be to remove definitively Vista!

I'm not an expert user and sorry if my question is stupid.

Just I'trying to install http srv from source code and I need to make somethings from root user.

I didn't set any password for root during the process installation.
How can I do to open a root shall (id must be = root)

Thanks
vcnz

---

### Post by tamoneya on 2008-07-10
in ubuntu you dont open a root shell instead you precede commands that need root permissions with sudo.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by llama320 on 2008-07-10
if you're on the command line, use
```
sudo [command]
```
to run the command as root. If you want to "login" as root, from the command line:
```
sudo -s
```

In any event, it'll prompt you for a password. It will probably be the same password as you use to login. That's the default at least. So try that. Note that when you type the password, no text will show up. Don't worry, that's a just a security feature..type your password as you normally would and you should get root access.

Another thing, if you want to use apps with a gui, you can Alt+F2 (to bring up "Run Application" dialog) and type
```
gksu [command]
```
then type your password. This will give you root privileges in a graphical app.

Good Luck

---

### Post by vcnz on 2008-07-10
Ok thank you. 
I need root privileges during compiling...I'll try to run makefile using sudo

---

### Post by Pablo89 on 2008-07-10
Running makefile by sudo is a good idea. But there is also `sudo -i` command, which puts you into the root shell.

---

