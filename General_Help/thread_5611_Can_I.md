---
title: "Can I??????????"
date: 2004-11-20
forum: General Help
---

### Post by Dave Sheffield on 2004-11-20
I have a 5 computer network at home. Some wired, some wireless. I am also, according to my wife, a hopeless experimenter......I have set up a server using win 2k but now would like to use linux....Ubuntu in particular.

What I would like to be able to do is stream audio to the other computers, use it as a print server....2 printers....have private folders for everyone else to save to. All the other computers are Win XP or Win 2K.....

Is this indeed possible?

I am waiting for the Ubuntu cd to finish installing as I speak

I appreciate any help/advice or am I wasting my time?

Thx

---

### Post by Rancoras on 2004-11-20
Read up on samba, it will take care of both of those tasks.  Webmin is a great tool for configuring samba.

---

### Post by costoa on 2004-11-20
[QUOTE=Dave Sheffield]I have a 5 computer network at home. Some wired, some wireless. I am also, according to my wife, a hopeless experimenter......I have set up a server using win 2k but now would like to use linux....Ubuntu in particular.

What I would like to be able to do is stream audio to the other computers, use it as a print server....2 printers....have private folders for everyone else to save to. All the other computers are Win XP or Win 2K.....

Is this indeed possible?

I am waiting for the Ubuntu cd to finish installing as I speak

I appreciate any help/advice or am I wasting my time?

Thx[/QUOTE]

**File Sharing:** I second Rancoras' recommendation about reading up samba. Check out [Chapter 2. No Frills Samba Servers](http://samba.mirror.bit.nl/samba/docs/man/Samba-Guide/simple.html) .
**Print server:** Easily done with cups. 
**Audio streaming**:  I've heard icecast is pretty good but haven't used it. 

This is clearly not a waste of time. The machine specs are fine for a light file and printer server. Icecast might be too much for the machine. Maybe someone here running it can comment.

It sounds like a fun project. I'd install Ubuntu, play with it for atleast a week or two and then try setting up the samba server. After that read up on cups and set up. Luckly it can be configured via a web browser.

One small piece of advice: if you're using a MS Windows and an Ubuntu machine (or any type of multiple machines) near each other think about getting a cheap ($50USD) KVM. Being able to double tap the control key to switch between the two is great.

Good luck and ask lots of questions. =)

---

### Post by ynef on 2004-11-21
[QUOTE=costoa]One small piece of advice: if you're using a MS Windows and an Ubuntu machine (or any type of multiple machines) near each other think about getting a cheap ($50USD) KVM. Being able to double tap the control key to switch between the two is great.[/QUOTE]
 Or you just use Synergy: [http://synergy2.sourceforge.net/](http://synergy2.sourceforge.net/) It allows you to copy+paste between the machines and it's FREE.

---

