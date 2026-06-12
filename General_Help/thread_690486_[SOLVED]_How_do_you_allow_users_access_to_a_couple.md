---
title: "[SOLVED] How do you allow users access to a couple of commands?"
date: 2008-02-07
forum: General Help
---

### Post by darkworld on 2008-02-07
I have one machine running Gusty with several family users each has their own account as a user. I recently installed some games which occassionally freeze. I want to allow other family users to play them but if I am not there and they freeze they are likely to just press the off button and may cause problems.

I want to allow them to either > shutdown -r now from a command line consol prompt using ctrl+alt+fkey

or

> /etc/init.d/gdm restart

If I give them sudoers then this gives them too much scope to screw things. What do I need to do because the commands normally need root. 

Sorry not that good at admin. Thanks in advance.

---

### Post by bodhi.zazen on 2008-02-07
Naw, that is the whole point of sudo, you have finer grain of control then su.

See these pages (I like people to understand what they are doing)

[http://www.gratisoft.us/sudo/man/sudoers.html](http://www.gratisoft.us/sudo/man/sudoers.html)

[http://www.gratisoft.us/sudo/man/sudoers.html#examples](http://www.gratisoft.us/sudo/man/sudoers.html#examples)

Please use visudo to make changes.

---

### Post by darkworld on 2008-02-08
Ok now I understand sudoers and its not what I thought it was. I sort of understand the setup but I cant get it right. Is there an idiots guide to writing the lines in visudo.

Ive tried several things in visdo and when i try to sudo in the guest account it says im not allowed. Is putting lines in visudo the only thing I have to do or do I also have to give the user the admin group?

The simplest entry I tried was this:

> Cmnd_Alias     SHUTDOWN = /usr/sbin/shutdown

guest   ALL= SHUTDOWN

---

### Post by &amp;)ky#)^ on 2008-02-08
I'm having a similar problem.  I'd like to allow a user to have full sudo access EXCEPT for maybe three files.  They aren't programs.  They are a couple of system config files and a shell script.  Would I be correct in thinking sudoers can help or does it just not work that way?

---

### Post by darkworld on 2008-02-08
well I just tried giving the user the admin group and it allows more than I specified in visudo. So no I dont give the admin group.

Ive tried several things now and I cant get them to work.

---

### Post by darkworld on 2008-02-08
> **bluej774 said:**
> I'm having a similar problem.  I'd like to allow a user to have full sudo access EXCEPT for maybe three files.  They aren't programs.  They are a couple of system config files and a shell script.  Would I be correct in thinking sudoers can help or does it just not work that way?

I think sudoers will sort your problem. The problem I have is correctly interpreting the guidelines! They are so chewy!!! probably something like this for you in visudo      ALL=(user)  ALL ! /not/these/files

---

### Post by darkworld on 2008-02-08
solved my problem. found a slightly more user friendly page. [http://www.linuxhelp.net/guides/sudo/]("http://www.linuxhelp.net/guides/sudo/")

thanks everybody.

---

### Post by &amp;)ky#)^ on 2008-02-08
Any tips on how you can allow users to access the necessary programs to install and uninstall software, i.e. Synaptic, apt-get, dpkg, but not any other root programs?  I've been trying with no success.  Too often I brick my sudoers file and have to go to recovery mode.  It's quite a pain in the butt.

---

### Post by bodhi.zazen on 2008-02-08
> **bluej774 said:**
> Any tips on how you can allow users to access the necessary programs to install and uninstall software, i.e. Synaptic, apt-get, dpkg, but not any other root programs?  I've been trying with no success.  Too often I brick my sudoers file and have to go to recovery mode.  It's quite a pain in the butt.

1. use visudo, keeps you from having these problems

man visudo

> visudo edits the sudoers file in a safe fashion, analogous to vipw(8). visudo locks the sudoers file against multiple simultaneous edits, provides basic sanity checks, and checks for parse errors.

2. Read, read, read. This is the one area where I think you need to understand what your are doing.

---

### Post by darkworld on 2008-02-09
> **bodhi.zazen said:**
> 
2. Read, read, read. This is the one area where I think you need to understand what your are doing.

Yes Im glad I did, I was looking for a quick solution but in the end the reading was worth it. I now understand sudoers which I didnt before so it was a worth while exercise, chewing through it all.

---

