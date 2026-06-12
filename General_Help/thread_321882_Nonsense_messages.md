---
title: "Nonsense messages"
date: 2006-12-19
forum: General Help
---

### Post by peterthewolf on 2006-12-19
peter@mymedia:~$ gksudo gedit /etc/apt/sources.list

After issuing the above command which was in an ubuntu howto I get this message

(gedit:4606): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

After this message gedit does what I want

So why the message? Please no Geek answers just a GOOD explanation in English of what this is meant to tell anybody.

---

### Post by bodhi.zazen on 2006-12-19
> **peterthewolf said:**
> peter@mymedia:~$ gksudo gedit /etc/apt/sources.list

After issuing the above command which was in an ubuntu howto I get this message

(gedit:4606): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

After this message gedit does what I want

So why the message? Please no Geek answers just a GOOD explanation in English of what this is meant to tell anybody.

Aww, you take all the fun out of just being a geek :(

OK then, have it your way ...

It's a known bug.

---

### Post by bapoumba on 2006-12-19
You do not have to worry, this is a warning, and a bug ;)
[https://launchpad.net/distros/ubuntu/+source/gksu/+bug/23917]("https://launchpad.net/distros/ubuntu/+source/gksu/+bug/23917")

I cannot find the bug saying it is actually gone upstream to GNOME. I'll look more precisely.

---

### Post by bulldog on 2006-12-19
It tells you,your install is gonna blow up soon :D 

Seriously,this is a little bug which means no harm.
You can use gedit and you'll see this messages more often.
Don't you worry about it,it's a filed bug and it's declared not to be important enough to repair.

---

### Post by peterthewolf on 2006-12-19
Ah it like all the mythtv howtos that do not work

---

### Post by hikaricore on 2006-12-19
> **peterthewolf said:**
> Ah it like all the mythtv howtos that do not work

:confused:  whatever you say man ](*,)

---

### Post by majoridiot on 2006-12-19
> **peterthewolf said:**
> Ah it like all the mythtv howtos that do not work

if you can't make these how-to's work, then it's operator error for certain.

[https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

:-k

---

### Post by peterthewolf on 2006-12-31
Well Majoridiot when I try that Howto everything works until Mythtv is scanning for channels, it has recognized the tv card, and then says the signal strength is very good but it cannot find any channels. Before you ask it is looking at the right xmitter. If I then quit the howto and use Kaffeine to view TV everything works fine.

---

### Post by majoridiot on 2007-01-01
> **peterthewolf said:**
> Well Majoridiot when I try that Howto everything works until Mythtv is scanning for channels, it has recognized the tv card, and then says the signal strength is very good but it cannot find any channels. Before you ask it is looking at the right xmitter. If I then quit the howto and use Kaffeine to view TV everything works fine.

did you complete ALL of the steps in mythtv-setup without skipping any?  it sounds like you 
skipped a few steps and forgot to set up channel listings, tuners or bind tuners to the 
channels.  it's critical to check every setting and screen the first time through mythtv-setup.

it's a fairly common source of setup failures.  i was guilty of it myself the first few times 
through.  it's really not a well documented topic on any distro.

---

