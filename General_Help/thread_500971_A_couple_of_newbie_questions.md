---
title: "A couple of newbie questions"
date: 2007-07-14
forum: General Help
---

### Post by redarmy on 2007-07-14
Hallo Ubuntu users,
I just install ubuntu 6.06, and come across several questions as follows:
1. the screen resolutions of tty1-tty6 are weird. According to some posts in this forum, I tried apt-get install hwinfo, but was told that the package cannot be found. How could I make sure whether it is a problem with my computer or there is no such package any more in the depo of ubuntu.

2. the built-in media player in this version ubuntu cannot play mp3 file. Which one is recommended for an old computer? and where could I download it?

3. what's the procedure to properly install a module in ubuntu? I mean, if I find somewhere a module, and attempt to try it out with ubuntu, where should I save the *.o files and should I make some adjustion in module.conf or sth. like this?

Thanks for your time and look forwards to your reply.

redarmy

---

### Post by bodhi.zazen on 2007-07-14
> **redarmy said:**
> Hallo Ubuntu users,
I just install ubuntu 6.06, and come across several questions as follows:
1. the screen resolutions of tty1-tty6 are weird. According to some posts in this forum, I tried apt-get install hwinfo, but was told that the package cannot be found. How could I make sure whether it is a problem with my computer or there is no such package any more in the depo of ubuntu.

Enable your repositories and re-try :

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

> 2. the built-in media player in this version ubuntu cannot play mp3 file. Which one is recommended for an old computer? and where could I download it?

You need "restricted formats"

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

> 3. what's the procedure to properly install a module in ubuntu? I mean, if I find somewhere a module, and attempt to try it out with ubuntu, where should I save the *.o files and should I make some adjustion in module.conf or sth. like this?

sudo modprobe <module>

What module are you wanting to load ?

If it is what you want, add if to /etc/modules to load it at boot.

---

### Post by davidjmayo on 2007-07-14
delete

---

### Post by redarmy on 2007-07-15
thank you bodhi.zazen,

Regarding installation of modules it is a general question. Since one of the merits of linux is that users can choose to install necessary modules, I'd like to know what would be the key points or precedure if I attempt to learn to develop a module out of my interest.

Thanks again, I'll try out the recommended links

redarmy

---

### Post by bodhi.zazen on 2007-07-15
> **redarmy said:**
> thank you bodhi.zazen,

Regarding installation of modules it is a general question. Since one of the merits of linux is that users can choose to install necessary modules, I'd like to know what would be the key points or precedure if I attempt to learn to develop a module out of my interest.

Thanks again, I'll try out the recommended links

redarmy

Sure :)

Brush up on your C++ ....

Then I would direct your here :

[http://tldp.org/HOWTO/Module-HOWTO/](http://tldp.org/HOWTO/Module-HOWTO/)

[http://tldp.org/LDP/lkmpg/](http://tldp.org/LDP/lkmpg/)

[http://www.kernel.org/](http://www.kernel.org/)

---

