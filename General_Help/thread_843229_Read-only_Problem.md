---
title: "Read-only Problem"
date: 2008-06-28
forum: General Help
---

### Post by RamR on 2008-06-28
I've been having several problems for that past few days that I'm beginning to suspect all might be due to my file system being messed up.  I'm unable to access Update Manager, Terminal or any files at all and when I went into the Virtual Terminal to try and reconfigure my xorg it said that it was Read-only so I couldn't create the new file.

Does anyone have any idea what to do about this read-only problem?

---

### Post by p_quarles on 2008-06-28
You need root privileges to edit the Xorg configuration file:
```
gksudo gedit /etc/X11/xorg.conf
```
Does that work? 

If not, it may be that sudo is broken, which is an issue with some Ubuntu 8.04 installations. To find out, you can post the contents of the following files here:
```
/etc/hosts
```
and
```
/etc/hostname
```

---

### Post by RamR on 2008-06-28
> **p_quarles said:**
> You need root privileges to edit the Xorg configuration file:
```
gksudo gedit /etc/X11/xorg.conf
```
Does that work? 

I was actually trying to reconfigure the xorg because I wouldn't know what how to manually edit it.  I followed these steps which lead to the read only error.

> **iaculallad said:**
> Try to reset your xorg.conf file: Press the Ctrl+Alt+F1 to enter your virtual terminal. Input your authenticated username and password.

On the terminal, issue the command below and try to answer the questions it ask. (Try using default answers/values)

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Then press Ctrl+Alt+F7 to get back to your GUI.



> **p_quarles said:**
> If not, it may be that sudo is broken, which is an issue with some Ubuntu 8.04 installations. To find out, you can post the contents of the following files here:
```
/etc/hosts
```
and
```
/etc/hostname
```

I'm not sure about how I could get the contents of those files you mention.  As I have said I can't access the Terminal or any files.  The only thing I can do is use the Virtual Terminal.

---

### Post by p_quarles on 2008-06-28
I am really not sure what you mean. "Virtual terminal" has been used to mean a number of different things, so I don't know exactly what you do or do not have access to. If you can open your file manager, though, and go to the files I mentioned, you should be able to open them. Alternately, you can run the following from a command prompt:
```
cat /etc/hostname
```
and
```
cat /etc/hosts
```

---

### Post by RamR on 2008-06-28
> **p_quarles said:**
> I am really not sure what you mean. "Virtual terminal" has been used to mean a number of different things, so I don't know exactly what you do or do not have access to. If you can open your file manager, though, and go to the files I mentioned, you should be able to open them. Alternately, you can run the following from a command prompt:
```
cat /etc/hostname
```
and
```
cat /etc/hosts
```

By Virtual Terminal I mean pressing ctrl+Alt+F1 

I went in there again and did the cat /etc/hostname and hosts and got this.

```
hostname ritchie-laptop

127.0.0.1 localhost
127.0.1.1 ritchie-laptop

```

```
#the following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6- allhosts
```

---

