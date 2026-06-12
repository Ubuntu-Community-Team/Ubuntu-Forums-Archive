---
title: "Strange error with remote X-application (krusader)"
date: 2013-11-12
forum: General Help
---

### Post by shestero on 2013-11-12
This is not a problem rather the question.

From my desktop host system Ubuntu 12.04 I am opening remote X-applications on ancient EEEBuntu system (based on Ubuntu 8 or 9).
I use ssh -X to reach the remote shell, then I can easy run them usually through gnome-terminal.

I just discovered that if I run a guest gnome-terminal I cannot run remote krusader from it:
shestero@shestero-laptop:~$ krusader: symbol lookup error: /usr/lib/libQtSql.so.4: undefined symbol: _ZN14QObjectPrivate15checkWindowRoleEv

The same error appears if I try to run my remote krusader from the remote child gnome-terminal.
Yet if I run a remote xterm from gnome-terminal I can run the remote krusader from the last.

I don't understand how the way I run the application do this matter?

---

### Post by TheFu on 2013-11-12
Just a guess, but Gnome-terminal is a GTK tool and might have conflicts with the Qt tool that krusader wants.

You could just remotely run krusader without the terminals .... 

**ssh -X user@server  krusader**

xterms use ... let me check ... Xt, Xm, Xaw, and Xlib libraries.
Can't do the same for g-t;  purged gnome-terminal just after install.

---

### Post by shestero on 2013-11-14
Yes I can run it.
But I don't understand why the conflict (if it is) occurs when I run programs remotely, but not occurs when I run it locally.
On the EEE locally I can run the krusader both from gnome-terminal and xterm and in any way there is no problem was observed.

Today I eventually found that my own Qt application can run remotely launched from xterm, but cannot from gnome-terminal with error:
symbol lookup error: /usr/lib/libQtXmlPatterns.so.4: undefined symbol: _ZN14QObjectPrivate15checkWindowRoleEv

I may guess that the reason is that in such case either host X-system tried to call some new window-method, that isn't implemented in old Qt4 or that remote application somehow tried to use local libraries(?)

I want to understand better the nature of this phenomena!

---

### Post by TheFu on 2013-11-14
X/Windows is a client/server architecture.  The clients (running on the remote machine) make calls to the server (running on the local machine) to request resources. Usually there isn't too much of an issue, but it seems in this case there is.

[Understand more about X/Windows.]("https://en.wikipedia.org/wiki/X_Window_System")

How are you running the terminal ... local then ssh -X or remote?

Are you a C/C++ programmer? The undefined symbol is a C++ entry point that is expected inside the listed library.  I would guess that gnome-term and the app are using different versions of the QtXmlPatterns library. It is just a guess, but there seems to be either a conflict or a missing dependency. Since it works with an xterm, I'm thinking this is a conflict.

**$ locate libQtXmlPatterns** might help to find multiple versions on the system. Then you could setup a specific LD_LIBRARY_PATH for the Qt app and it will find only the correct library.

The output from **file /path/to/gnime-terminal** and **file /path/to/that/other/program** might be helpful along with a **strings** run on each too.  If the programs haven't been stripped, you could get the symbols out.

Anyway, I don't really know the answer, but these things should allow you to find the conflict and come up with a way to resolve it.

---

### Post by shestero on 2013-11-26
I well acquainted with XWindows and using it since 1995. I thought I understand how it works before this case.

Only in the former times I used display option/variable to use remote application, not ssh tunnel.
As I told, I run ssh -X locally and then gnome-terminal remotely (it's seen by different font) and xterm remotely.

Yes, I'm C++ programmer and I'm very intrigue how the terminal window from which you start the executable may affects which dynamic library are to be loaded.

Remote system has one lib:
/usr/lib/libQtXmlPatterns.so.4.5.0
The remote system and consequently all remote applications are 32-bit:
$ file db-client
db-client: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, not stripped


Local system is 64-bit and it have two libs:
/usr/lib/i386-linux-gnu/libQtXmlPatterns.so.4.8.1
/usr/lib/x86_64-linux-gnu/libQtXmlPatterns.so.4.8.1
That's ok because i386 llibrary are needed for some my applications.
Both local xterm and gnome-terminal are from standard system packages and are 64-bit:
shestero@fitpc3-shestero:~$ file /usr/bin/gnome-terminal
/usr/bin/gnome-terminal: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.24, BuildID[sha1]=0xafb29c1579fcb4fa94d567b04584e25d8c646632, stripped
shestero@fitpc3-shestero:~$ file /usr/bin/xterm
/usr/bin/xterm: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.24, BuildID[sha1]=0x95045ca56a80fe324a459e1bd27c6ab522797df3, stripped

Local Qt-libraries have no [COLOR=#000000]checkWindowRoleEv:[/COLOR]
(local) objdump -T  `ls -1 /usr/lib/x86_64-linux-gnu/libQt*.so.4.8.1`|grep checkWindowRole
(no result)
(remote) objdump -T  `ls -1 /usr/lib/libQtCore.so.4.5.0`|grep checkWindowRole00159930 g    DF .text	00000005  Base        _ZN14QObjectPrivate15checkWindowRoleEv

PS NB I mentioned that local and remote applications interferer some way: e.g. if I have local thunderbird window open I cannot invoke remote one. Also if I have already open OpenOffice Writer on remote desktop (locally) I cannot invoke this application from remote desktop. This is very unusable. :-(

---

