---
title: "Gnome terminal"
date: 2019-07-04
forum: General Help
---

### Post by valeriekai on 2019-07-04
Hi.

I have ubuntu 18.04 and gnome 3.28.4 on my computer.

I need to launch Gnome terminal from shell script, connect to target device with ssh, run gdbserver and keep it open.

At this moment the best solution looks like this"

ip=$1
password=$2
execution_file=$3
[COLOR=#0000ff][B]gnome-terminal -- bash -c "sshpass -p $password ssh root@$ip; /usr/bin/gdbserver host:777 /usr/bin/$execution_file; exec bash"
[/B][/COLOR]
The first command run fine, but the second command don't. It doesn't matter what is the second command,
 I tried put thei "[COLOR=#0000ff]**echo something**[/COLOR]", but it is also dosnt't work

Please, help me to find solution for the problem.

Thanks in advance

Valerie

---

### Post by TheFu on 2019-07-05
Can't help with anything, except with the suggestion to use ssh-keys, not passwords.  Also, I'd use ~/.ssh/config to configure the userid and IP/hostname with an alias.

I don't use gnome terminal. Sorry.

---

### Post by valeriekai on 2019-07-07
Hi
Yes, I already tried SSH keys and it solved my problem.

Thanks a lot

---

### Post by HermanAB on 2019-07-07
You forgot to put a ; between the two commands.

---

