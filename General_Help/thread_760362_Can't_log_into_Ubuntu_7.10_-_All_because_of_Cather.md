---
title: "Can't log into Ubuntu 7.10 - All because of Catherine Zeta-Jones"
date: 2008-04-20
forum: General Help
---

### Post by curme on 2008-04-20
It all started when I wanted to watch a dvd I got from Netfilcks. Totem and VLC wouldn't play it. I googled and someone side I needed more codecs. So I download some codecs from Synaptic. Several hours later (I'm on dial-up) after the codes are downloaded, I still can't watch "No Reservations" with Catherine Zeta-Jones, so I reboot, to see if that would work.

I thine got the message, "Your Session only lasted less than 10 seconds... try a 'failsafe' session". I boot into my "failsafe gnome" session, and got some info from ubuntu forums on how to fix my problem. I reboot into recovery, type in some sudo commands, reboot. Now I can't even get into a 'failsafe sessions'. I get the smae error message, and then a new one talking about my home folder: "failed to create file /tmp/gconf-test-locking-file-GK7G97... Permission denied (errno=13)

All I wanted to do was watch a movie!  :cry:

---

### Post by joeabiraad on 2008-04-20
try starting your pc with a live CD and then check where the prb is. 

for example check if your home permissions are ok

---

### Post by sailor2001 on 2008-04-20
i agree: Catherine Zeta-Jones is your problem.......lol

---

### Post by curme on 2008-04-20
> **joeabiraad said:**
> try starting your pc with a live CD and then check where the prb is. 

for example check if your home permissions are ok

What's a prb? I googled it but all I came up with was people using it in place of "problem". :)

How do I check and fix my permissions?

---

### Post by sailor2001 on 2008-04-20
you have a parental control or blacklist ?

---

### Post by curme on 2008-04-20
I actually fixed one problem by:


sudo chmod 777 /tmp
chmod 600 .Xauthority
sudo /etc/init.d/gdm restart


Now I only get the message that my "session lasted less than 10 seconds", but at least I can log into gnomefailstart now! biggrin.gif

I just need to figure out the "Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of disk space. Try logging in with one of the failsafe sessions to see if you can fix this problem." (I have plenty of diskspace).

And then, when everything is fixed, I have to figure how to watch dvds! 

> you have a parental control or blacklist ?

Since I don't know, I'm going to assume no.

---

### Post by curme on 2008-04-21
Hopefully I can get this fixed before Hardy Heron drops. I can log into Gnomefailsafe, here is my error message when I try to log in regularly. I get the "Less than 10 seconds blah blah" but the actual xsessions error file says:

```

/etc/gdm/PreSession/Default:62:Syntax error: end of file unexpected (excepting "fi") gdm [6050]: ERROR: session-child-run: Execution of Presession Script returned 70. Aborting. aborting...

```

Aha! It was excepting 'fi'! :-k

Wha...?

---

