---
title: "Pulling user data from the server"
date: 2008-01-29
forum: General Help
---

### Post by jrothwell97 on 2008-01-29
In many Windows environments, there is a feature (I think from the magic of Domain Services) by which a user's home folder is stored on the server. He logs in at a client, and the user settings are pulled from the server into the RAM immediately, and files in his home folder are pulled over the network when needed. Dumb clients are rarely used: the machines are capable of booting under their own steam if not connected to a network, and the data wizardry seems to be completely in the hands of the OS.

I may sound incredibly dense here, but is there a way to replicate this behaviour in Gutsy? As I understand it, the user data never touches the client's hard drive (except in the swapfile).

This is how I imagine it would be possible *in theory*:

[LIST=1]
[*]Use normal GNOME login shell.
[*]Check password against the *server*'s /etc/passwd file. If correct, proceed, else delay for ten seconds and then return to the login shell.
[*]Mount the user's home directory on the server under the client FS's /home/username.
[*]Run login processes.
[*]Operate as normal, running client apps from the server and 'system' processes (i.e. the shell, the kernel, init, the daemons, et al) from the HDD.
[*]When the user logs out, after the logout has completed, unmount his home directory, flush the swap and return to the login shell.
[/LIST]

Something I am concerned about is whether or not this would be possible without a lot of source fiddling and compiling from source. Is there a simple tool (even TUI will do, GUI will be even better) that allows this, with the minimum of fuss and hassle during set-up time? (If there isn't one already, I'm sure many admins would like to see one in Hardy, or perhaps 8.10.)

Thank you very much in advance.

---

### Post by dabang on 2008-01-29
If I understand correctly, you'd like to have a client/server relationship, where home dirs are located on the server and then mounted on the client? And user authentication against the server? If correct, I guess this would become a rather large howto, but maybe I can get you on the right track. Of course this is possible with any unix system. You basically need two things: LDAP and NFS. Your server would run both services. The home dirs would be NFS shares on the server which are then mounted by the client (-> client needs automount, look for /etc/auto.master).
All information about users, their home dir location etc are stored in LDAP. This isn't a trivial task, but php scripts like [phpLDAPadmin]("http://phpldapadmin.sourceforge.net/") could be of help. On the client side you need to configure the ldap client (-> /etc/ldap.conf) and the authentication methods (/etc/nsswitch.conf). I'm not quite sure, which packages you'd exactly need with gutsy. To make it short: it's possible, works great, but it's not set up in 5 minutes and you need to do some reading...
Maybe this helps as a start [http://www.debuntu.org/ldap-server-and-linux-ldap-clients](http://www.debuntu.org/ldap-server-and-linux-ldap-clients)

Good luck!

---

### Post by jrothwell97 on 2008-01-30
That helps an awful lot. Thank you.

---

### Post by jrothwell97 on 2008-01-30
I might end up using NIS: can anyone offer me any advice on this?

---

