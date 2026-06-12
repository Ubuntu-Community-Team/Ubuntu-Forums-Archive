---
title: "How to load Realtime-lsm??"
date: 2005-04-28
forum: General Help
---

### Post by otherside on 2005-04-28
I need the realtime-lsm module for some audio work that i am doing...to insure low-latency with the kernel.  I installed the binary package from the Synaptic Universe repo.  I can see the kernel try to load it on boot but it says "loading Realtime Linux Security Module---not found."  Synaptic shows it installed...do I need to do something else?

---

### Post by October on 2005-05-15
Did you ever figure out what the problem is?  I am getting the same thing...

---

### Post by 23meg on 2005-05-16
try adding "modprobe realtime gid=29" to a startup script, and let me know if it works for you.

---

### Post by renick on 2005-08-22
[QUOTE=otherside]I need the realtime-lsm module for some audio work that i am doing...to insure low-latency with the kernel.  I installed the binary package from the Synaptic Universe repo.  I can see the kernel try to load it on boot but it says "loading Realtime Linux Security Module---not found."  Synaptic shows it installed...do I need to do something else?[/QUOTE]
 Look in /usr/share/docs/realtime-lsm-source. It explains the process. In short, you have to build the module and then load it. n00b and all, I'm a bit stuck in building it. I'll reply again should I figure it out.

---

### Post by renick on 2005-08-22
[QUOTE=renick]Look in /usr/share/docs/realtime-lsm-source. It explains the process. In short, you have to build the module and then load it. n00b and all, I'm a bit stuck in building it. I'll reply again should I figure it out.[/QUOTE]
 After you've built it, it creates a deb in /usr/src/. You have to use dpkg -i to install this module. Then, according to:

[http://www.joq.us/realtime/README](http://www.joq.us/realtime/README)

you have to do this:

# modprobe realtime gid=29

However, when I do that, I get this error:

FATAL: Error inserting realtime (/lib/modules/2.6.10-5-386/kernel/security/realt ime.ko): Operation not permitted

Any ideas why? How can I fix this?

---

### Post by renick on 2005-08-22
[QUOTE=renick]After you've built it, it creates a deb in /usr/src/. You have to use dpkg -i to install this module. Then, according to:

[http://www.joq.us/realtime/README](http://www.joq.us/realtime/README)

you have to do this:

# modprobe realtime gid=29

However, when I do that, I get this error:

FATAL: Error inserting realtime (/lib/modules/2.6.10-5-386/kernel/security/realt ime.ko): Operation not permitted

Any ideas why? How can I fix this?[/QUOTE]
 If done as root, I get this error:

FATAL: Error inserting realtime (/lib/modules/2.6.10-5-386/kernel/security/realt ime.ko): Invalid argument

Advice?

---

### Post by renick on 2005-08-22
Ugh. After this work, and now I read this:

"Note: the realtime-lsm is officially deprecated. rtlimits takes its place. See the rtlimits page."

[http://tapas.affenbande.org/?page_id=21](http://tapas.affenbande.org/?page_id=21)

Now, to find out about a 2.6.12 kernel...

---

### Post by 23meg on 2005-08-22
maybe you have to enable the module at startup. did you try adding the gid=29 line to your startup script rather than applying it later on?

---

### Post by renick on 2005-08-22
Thanks, but I think that now I've got to quit messing with this route and go for the newer method, i.e. the 2.6.12 kernel, with the PAM changes described here:

[http://tapas.affenbande.org/?page_id=22](http://tapas.affenbande.org/?page_id=22)

---

### Post by 23meg on 2005-08-22
cool, keep us posted on how you fare with hoary + 2.6.12 + JACK. i'll look into getting JACK to work in realtime mode with 2.6.12 myself as soon as i have some time on my hands.

---

### Post by nbd on 2007-09-23
The easiest way to build/install realtime-lsm is using module-assistant.

simply run 'sudo module-assistant' (and apt-get it first if you don't have it)

Then follow the steps:

UPDATE
PREPARE
SELECT (browse down for realtime-lsm and check it, then OK)
BUILD (asks if you want to install it)

and you're done!

Realtime-lsm works 100% in feisty, but with gutsy I get the same error:
FATAL: Error inserting realtime (/lib/modules/2.6.22-12-rt/kernel/security/realtime.ko): Invalid argument

---

### Post by dunder on 2007-09-24
found solution - do as root:

/etc/init.d/apparmor stop
rmmod aparmor
rmmod commoncap
modprobe realtime

and it works :D
You can also remove it pernamently (so realtime can be in /etc/modules and started at boot) by apt-get remove apparmor - it will be removed from initramfs.

---

### Post by surfdoc on 2007-12-19
typo above

apparmor not aparmor

---

### Post by dweezil on 2008-02-06
Trying to do approximatively the same stuff I follow the info given on this page [http://freebob.sourceforge.net/index.php/Realtime_scheduling_for_non-root_users](http://freebob.sourceforge.net/index.php/Realtime_scheduling_for_non-root_users)
adding these lines to /etc/security/limits.conf:

@audio   -  rtprio     99
@audio   -  memlock    512000
@audio   -  nice      -19

This approach doesn't use realtime-lsm but do pretty much the same and so far it solve all the rt problem I had (mainly enabling RT and memlock for non-root user) whithout need of unloading any other module
for info i'm running a 2.6.22-14-rt  kernel on Gusty

---

### Post by knife_party on 2008-04-28
hey, how can i edit the lists.conf? Everytime i wanna save the changes i've made, there's an error mesaagaes that says i can't save. I've used su, but it doesn't help. Any suggestions?

thanks in advance

---

