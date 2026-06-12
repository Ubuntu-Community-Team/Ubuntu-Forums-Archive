---
title: "Trying to install rabbitmq on my kubuntu 20 I got issues with EOF command and deb"
date: 2022-12-25
forum: General Help
---

### Post by nilovsergey on 2022-12-25
I try to install rabbitmq on my ubuntu 20 by docs
[https://www.rabbitmq.com/install-debian.html#apt-cloudsmith](https://www.rabbitmq.com/install-debian.html#apt-cloudsmith)
but running commands one by one on command with  <<EOF at the end of line I got on my screen :
[https://prnt.sc/x3E4TXPdwqsZ](https://prnt.sc/x3E4TXPdwqsZ)
I can not enter next commands and last comman was not completed...
1) I am not sure have I to waite this command to be completed ?
2) I tried to run next commands from the list of commands , but I got :
```
master@master-at-home:~/Downloads$ sudo -s
[sudo] password for master: 
root@master-at-home:/home/master/Downloads# deb [signed-by=/usr/share/keyrings/net.launchpad.ppa.rabbitmq.erlang.gpg] http://ppa.launchpad.net/rabbitmq/rabbitmq-erlang/ubuntu bionic main
Command 'deb' not found, did you mean:
  command 'den' from snap den (1.2.0-0)
  command 'dub' from snap dub (1.19.0)
  command 'dub' from deb dub (1.19.0-1build2.1)
  command 'dex' from deb dex (0.8.0-2)
  command 'debi' from deb devscripts (2.20.2ubuntu2)
  command 'dep' from deb go-dep (0.5.4-3ubuntu0.1)
  command 'debc' from deb devscripts (2.20.2ubuntu2)
  command 'dab' from deb bsdgames (2.17-28build1)
  command 'edb' from deb edb-debugger (1.0.0-1build3)
  command 'derb' from deb icu-devtools (66.1-2ubuntu2.1)
  command 'deb3' from deb quilt (0.65-3)
See 'snap info <snapname>' for additional versions.
root@master-at-home:/home/master/Downloads# deb-src [signed-by=/usr/share/keyrings/net.launchpad.ppa.rabbitmq.erlang.gpg] http://ppa.launchpad.net/rabbitmq/rabbitmq-erlang/ubuntu bionic main
deb-src: command not found

```

I am not sure which package have I to install to run &#8220;deb&#8221; and "deb-src" commands?
Searching for decision I found gdebi command mentioned : But installing it I have the same errors...

```

 dpkg -s   gdebi
Package: gdebi
Status: install ok installed
Priority: optional
Section: admin
Installed-Size: 169
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Version: 0.9.5.7+nmu3
Depends: python3:any (>= 3.3~), gdebi-core (= 0.9.5.7+nmu3), gir1.2-gtk-3.0, gir1.2-vte-2.91, python3-gi, policykit-1, gnome-icon-theme
Recommends: libgtk2-perl, shared-mime-info, lintian
Description: simple tool to view and install deb files - GNOME GUI
 gdebi lets you install local deb packages resolving and installing
 its dependencies. apt does the same, but only for remote (http, ftp)
 located packages.
 .
 The package is also scanned via lintian before the install and its
 possible to inspect the control and data members of the packages.
 .
 This package contains the graphical user interface.
Original-Maintainer: Ubuntu Developers <ubuntu-dev-team@lists.alioth.debian.org>

```

```
uname -a
Linux master-at-home 5.15.0-53-generic #59~20.04.1-Ubuntu SMP Thu Oct 20 15:10:22 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux
lsb_release -d; uname -r; uname -i
Description:    Ubuntu 20.04.5 LTS
5.15.0-53-generic
x86_64

```
Thanks!

---

### Post by guiverc on 2022-12-25
*deb* and *deb-src* are **not** commands, but parameters for your sources files.

Kubuntu is a desktop release thus its releases are all *year.month* in format (eg. 20.04 & 20.10), with Ubuntu reserving the *year* format for *snap* only products of Ubuntu (eg. Ubuntu Core 20).  Kubuntu or desktop systems are *deb* based, so 20 cannot use *deb* or *deb-src* inputs anyway.

Your final command shows you're running 20.04 and not 20 anyway, so please be precise with details (*20 & 20.04 are different Ubuntu products*).

I suggest you re-read the instructions, you were (*on quick scan*) to enter those *deb* lines as text input into a prior `tee` command which you don't appear to have run in your provided paste.  That's why BASH tried to treat them as commands (BASH *wasn't supposed to receive them*).

---

### Post by Impavidus on 2022-12-25
The deb "command" you typed isn't a command. It's a line of text to be saved in /etc/apt/sources.list.d/rabbitmq.list. The sudo tee command above it would create that file and write standard input to it, the <<EOF and the EOF a few lines below would arrange for the intervening lines to be passed on to tee. It's just one of the many ways how you can pass text from the command line to tee, and using tee is just one of the many ways how you can write something to a root-owned file. By hitting ctrl-c you aborted the text input before entering the lines below, so that the shell interpreted those lines as separate commands.

You can also create the file in a text editor, copy the text into it and save it.

---

### Post by deadflowr on 2022-12-25
Just run
```
sudo add-apt-repository ppa:rabbitmq/rabbitmq-erlang
sudo apt update
```
Then you should be able to install whatever packages you were trying to install from the added repository.

No need to over-complicate things.

---

