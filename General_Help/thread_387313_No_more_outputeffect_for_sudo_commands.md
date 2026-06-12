---
title: "No more output/effect for sudo commands ?"
date: 2007-03-18
forum: General Help
---

### Post by NicDumZ on 2007-03-18
Hello,

I'm an advancetd ubuntu-user (running edgy), and until now i've always found a workaround to my problems by myself, or searching on the internet. But this time... I'm powerless.

You've all read the title, so i'll just explain my problem with examples instead of a long text:


**$**iwconfig eth1 
[...] _Wifi config, works fine._

**$**sudo iwconfig eth1 
Password:
**$** _no output ?!_

**$**sudo iwconfig eth1 
**$** _sudo has kept my password, but no output neither. _


***now even better :***

**$**iwconfig eth1 essid whatever 
Error for wireless request "Set ESSID" (8B1A) :
SET failed on device eth1 ; Operation not permitted. _this is normal._

**$**sudo iwconfig eth1 essid=whatever _outputs nothing, which is normal._

**$**iwconfig eth1 
[...] _works well, but the essid has not changed !!!_

**$**sudo su
**$** _does not switch to a root console._


iwconfig is just an example. I tried a lot of things, apt-get, synaptic, do not work either... Anyway i can't connect to the internet without sudoing, so...
For the same reasons, i can't check the logs.
I noticed that the daemons usually starting at the start up were not started: i don't have any sound for example, but this does not surprize me.

I'm just... lost.
:confused:

---

### Post by kidders on 2007-03-19
Hi there,

I clicked on this thread when you posted it, because I was interested to see what people made of your problem. You still have no replies though. :-( I don't know if I can help you solve this, but your problem is totally crippling, so I thought I should give it a shot!

The first thing that strikes me is that the output of **sudo whoami** might be interesting. Secondly, have you altered your **/etc/sudoers**, or chosen an authentication mechanism other than Ubuntu's shadow-based default?

The most convenient way to get unrestricted access to your logs (along with the rest of your system) might be to boot from a CD and take a look around. Taking a peek inside your system logs seems, as you suggested, like the first thing to try.

---

### Post by praxis22 on 2007-03-19
Sounds to me like you've borked your sudo install, or you're doing something strange with your shell environment.

If you've changed either your shell init file or sudoers, recover from backup. You did make a backup?

---

### Post by NicDumZ on 2007-03-19
thanks both of you for your answers. 

I eventually found out what the problem was by myself, it was "just" a corrupted group file.

For those who might encounter this problem later :
- I booted in the recovery mode from grub. I was then logged-in, as root, in a text-mode.
- I gave a look to my group file, and, woops, surprise, i wasnt anymore in the "admin" group, so i quickly fixed that, and rebooting normally, everything went fine. (oh yeah, i dont have any sound now, but that doesnt matter)



Now the problem is : I've never ever modified /etc/group on that computer. The last "non-minor" changes that i did were the basics apt-get update -> apt-get upgrade. I don't understand how i got removed from the admin group. :confused:


**Edit :** My sound problem is also coming from that corrupted group file. My user got removed from the audio: x:29:... line :confused: . ???!!!

**Edit 2:** I just noticed that i also got users removed from the cdrom and plugdev groups. For some reasons, the other groups with usernames in it ( www-data & wwwadmin ) were not modified.

---

