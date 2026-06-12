---
title: "Run programs as Root, User or User with Sudo privileges?"
date: 2016-02-25
forum: General Help
---

### Post by jay116 on 2016-02-25
I know this is a basic question but I'm having a hard time finding any discussion of this in a google search. I've used Linux off and on for years, but never as my main desktop. I remember something from a while back stating you shouldn't run programs accessible from the internet as root. That you should have a user with lower privileges run it. I've never found a good walk though on how to accomplish this if it truly is a good practice. Should I install the software and assign run privileges to new user say "programxUser". Any information or just a point in the right direction would be great.

Thank you,

Jay

---

### Post by ian-weisser on 2016-02-25
If your application is hijacked by a malicious person or bot at the other end of the connection, how much of your system do you want them to have access to?

If you want your entire system to be compromised, run the application as root.
If you want your entire /home/YOU directory to be compromised, including your shell access, email cache, browser history, favorite website passwords, contact database, and personal files, then run the application as yourself.
If you want merely your server's /var/APPLICATION_DATA directory to be compromised, create a 'system user' (see man adduser) without shell, and with strict limits on what it can run and access. Let that system user run your application.

Best practice is for server applications to run as a system user. You communicate with the server application using a separate client application, The client run on your screen, using your login, and communicates with the server using sockets or dbus.

---

### Post by jay116 on 2016-02-25
Thanks for the help. I understand the user permission part but how to I assign a user as the person running the application? For instance when I have a program that I want to start when the server starts. Maybe im missing something. If I install a program while logged into the user account will that program always run under that user? I guess I'm looking for more details.

---

### Post by SeijiSensei on 2016-02-25
You can't really do this unless you are coding the software yourself.  Programs like Apache that run as an ordinary user are first launched with root privileges, then they spawn additional "child" processes with fewer privileges.  For instance, here's what the Apache web server looks like on my CentOS 6 server:
```

root     11690  0.0  0.9 270984 18768 ?        Ss   Feb25   0:01 /usr/sbin/httpd
apache   15366  0.0  0.4 271116  9680 ?        S    01:19   0:00 /usr/sbin/httpd
apache   15368  0.0  0.4 271116  9108 ?        S    01:19   0:00 /usr/sbin/httpd
apache   15369  0.0  0.4 271116  9108 ?        S    01:20   0:00 /usr/sbin/httpd
apache   15554  0.0  0.3 270984  7796 ?        S    01:26   0:00 /usr/sbin/httpd

```
(On Ubuntu, you'll see /usr/sbin/apache2 as the executable and "www-data" as the user rather than "httpd" and "apache" which are the RedHat/CentOS defaults.  The principle is the same though.)

Here you see a process with root privileges, often called a "stub," that launches multiple "children" that are running as user "apache."  This is a feature built into the program code, not something imposed from outside.  Only the children are listening on port 80; the stub is insulated from external access.

It is possible to run programs in a "chrooted" environment where the program sees only a limited directory tree.  From the perspective of a chrooted program, the top of the directory structure starts at some arbitrary directory rather than / itself.  This means that you have to replicate the entire environment under the chroot directory with, e.g., /path/to/chroot/lib and /path/to/chroot/bin, etc., since the program cannot see the actual /lib and /bin directories.  You need not include every piece of software in the actual /lib directory, just the libraries the chrooted program uses. This is, frankly, a pain in the neck.

So tell us, what specific program are you concerned about?  That would help a lot to understanding what you need to accomplish.  These days most Internet-facing server daemons are designed to run as an unprivileged user or, in some cases like BIND9, in a chrooted environment.

---

### Post by jay116 on 2016-02-25
thank you for the detail. I'm really coming from the point of view of all security independent of the program. I'm a windows user, aka "LazyUser", and wanted a better understanding of the proper way to setup things. I only have a couple programs that run, teamspeak, crashplan, ssh. In the below example they create a teamspeak user and group and then setup the user with nologin status. I'm trying to understand the reasoning for this if the TS server runs under root why make the group/user?

---

### Post by ian-weisser on 2016-02-25
> **jay116 said:**
> how to I assign a user as the person running the application? For instance when I have a program that I want to start when the server starts. Maybe im missing something. If I install a program while logged into the user account will that program always run under that user? I guess I'm looking for more details.

You, the user, cannot directly do anything as another user. That would be a rather big security hole.

There are four fairly simple ways to (indirectly) start an application as a different user...assuming the application is set up for it.

One is the classic method described by SeijiSensei - start as root, which spawns a child of the appropriate user.

Two is to tell init 'start this service'. Init, which runs as root, will start the service for you. This is also how you start services at boot. The user is speicifed in init's settings for that application.

Three is to start the service using a dbus message to the service. dbus will start the service if it's not already running, and then pass it the message. This is handy for occasional services that terminate when they complete their task (non-deamons).

Four is to use the shell and manually type 'sudo' and your admin password.

---

### Post by jay116 on 2016-02-26
Thank you for the help. You've pointed me in the right direction.

---

