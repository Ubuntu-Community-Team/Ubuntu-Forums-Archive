---
title: "Has my system been compromised? Help!"
date: 2006-10-25
forum: General Help
---

### Post by DeathOnJuice on 2006-10-25
Hey, everyone. I just read about a bug in the NVidia drivers that can allow someone root access. While reading about this, I read about some bug crashing the X server. When I have gone a certain site in the past on several occasions, my X server has restarted. Does this show that my system has been exploited? In my xorg.conf, I am using the nvidia driver. I just changed RenderAccel to False to fix the bug, but how do I know if I've already been compromised?

How do I know if I've been hacked? What can I do to fix it? Is it safe to burn my files onto a CD, or could they be infected with something?

Thanks so much!

---

### Post by woedend on 2006-10-25
chances are your xserver is just crashing.  ESPECIALLY if you are using xgl/compiz/beryl/whatever.
run rkhunter to tell if you have a rootkit.  otherwise, i honestly believe you are safe.

---

### Post by DeathOnJuice on 2006-10-26
Actually, this happens less when I am in XGL. It's only a particular site, which fits the bill for the NVidia security hole. Does anyone know if the X server crashing and the hole are related? I saw them both in the same topic.

Whew, I think I'm safe. I read the Rapid7 security advisory, and it said that the X server could be crashed with a long text string in an input field. The site I went to is an archive of user-created levels for a game that are represented by long amounts of text in an input field. Therefore, unless by some freak chance the level code managed to install a rootkit, I think I'm fine. :D 

Thanks so much! I'm really paranoid about this stuff. By the way, in case anyone really wants to reassure me that it's OK: the site is numa.notdot.net

---

### Post by DeathOnJuice on 2006-10-26
By the way, I just ran rkhunter and got this output (it's not done yet):

* Filesystem checks
   Checking /dev for suspicious files...                      [ OK ]
   Scanning for hidden files...                               [ Warning! ]
---------------
 /dev/.static
/dev/.udev
/dev/.initramfs
/dev/.initramfs-tools /etc/.pwd.lock
/etc/.java
---------------
Please inspect:  /dev/.static (directory)  /dev/.udev (directory)  /dev/.initramfs (directory)  /etc/.java (directory)


Is this normal?

---

### Post by DeathOnJuice on 2006-10-26
Bump.

---

### Post by dbott67 on 2006-10-26
I've got the same directories, so I wouldn't worry.

Are you behind a firewall... like a NAT router (Linksys, D-Link, Netgear, etc)?  If so, I'm guessing all is well.

-Dave

---

### Post by DeathOnJuice on 2006-10-26
Yeah, I'm behind a router. I was worried about the NVidia security exploit, which can be bad with or without a router, but I found that I haven't been compromised. However, the bug I had was related to the exploit.

All is good.

---

### Post by glotz on 2006-10-26
Looks like the /etc/.Java is a known false positive [http://www.rootkit.nl/articles/rootkit_hunter_howto_false_positives.html](http://www.rootkit.nl/articles/rootkit_hunter_howto_false_positives.html)

---

### Post by skymt on 2006-10-26
The /dev warnings are also common false positives with rootkit finders like rkhunter. Don't worry, you're safe.

---

### Post by DeathOnJuice on 2006-10-26
Thank you so much, everyone! I love the Ubuntu community :) .

---

### Post by matthewstory on 2006-10-27
if you're really concerned about this kind of stuff install tripwire:

aptitude intall tripwire

and also snort:

aptitude install snort

With some tweaking and a visit to the daily logs they produce, you should be able to sleep better at night.

---

