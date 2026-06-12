---
title: "how do i block facebook?"
date: 2013-02-05
forum: General Help
---

### Post by alving on 2013-02-05
hi all

im running a HP media centre M1195C with Ubuntu 12.04LTS.
myself and a couple others in the house use the computer for gaming.
(WoW and Diablo3)

i do not use Facebook and never will.
the teenagers here do use it and most of them dont know how to close it or cant be bothered to close it when they are done.
i seriously interferes with the gaming when they leave it open.

how do i block the whole website temporarily?
or set it up with a password so my friends can use it if needed.

i dont want to block it permanent, because they might actually grow a brain and figure out how to close a program when they are done with it.
(but, then again, im still waiting for these same teenagers to turn off the lights...)

any suggestions will be greatly appreciated

thanks
allyn

---

### Post by furything on 2013-02-05
Some routers can block sites. Log onto to your router and have an explore

or this way
[http://www.addictivetips.com/ubuntu-linux-tips/how-to-block-unwanted-website-in-ubuntu-linux/](http://www.addictivetips.com/ubuntu-linux-tips/how-to-block-unwanted-website-in-ubuntu-linux/)

You could do it through iptables - try using gufw if you want to change iptables

Of course you also have to remember to set it back to allow them access

---

### Post by unixpcguy on 2013-02-05
You could block the site from your browser or multiple browsers you have; just remember to password protect it.

---

### Post by furything on 2013-02-06
Problem with multiple browsers is multiple browsers :P.

---

### Post by Sylos on 2013-02-06
You could do it via firewall or something similar like Peerguardian that just uses iplists.

Cheers

---

### Post by c2tarun on 2013-02-06
> **alving said:**
> hi all

im running a HP media centre M1195C with Ubuntu 12.04LTS.
myself and a couple others in the house use the computer for gaming.
(WoW and Diablo3)

i do not use Facebook and never will.
the teenagers here do use it and most of them dont know how to close it or cant be bothered to close it when they are done.
i seriously interferes with the gaming when they leave it open.

how do i block the whole website temporarily?
or set it up with a password so my friends can use it if needed.

i dont want to block it permanent, because they might actually grow a brain and figure out how to close a program when they are done with it.
(but, then again, im still waiting for these same teenagers to turn off the lights...)

any suggestions will be greatly appreciated

thanks
allyn

you can open /etc/hosts and enter:

127.0.0.1   [www.facebook.com](www.facebook.com)

Now when anyone will try to open facebook it won't open, you can unblock it just by commenting the line. You need sudo privileges to edit hosts file, so keep your password safe and no-one will ever be able to block it ;)

Oopps... sorry I didn't noticed that furything already mentioned this solution.

---

### Post by mastablasta on 2013-02-06
create a new separate user for others. there is also a guest user avalable for guests on computer (that should remove all traces of them after they log out).
 
so you would be user *ally*n and they would have user *kids* for example to browse facebook and such. then you can set up that after certian time of innactivity the user automaticly logs out.

---

### Post by rnerwein on 2013-02-06
> **mastablasta said:**
> create a new separate user for others. there is also a guest user avalable for guests on computer (that should remove all traces of them after they log out).
 
so you would be user *ally*n and they would have user *kids* for example to browse facebook and such. then you can set up that after certian time of innactivity the user automaticly logs out.
hi
nice answer. the manual is huge. but on the way - what's the real solution - to tell "read the manual - 1000ts of lines" shouldn't be the way. i was looking for similar think and i couldn't found it. for windows (it's only for my children) there is absolutely no problem to solve it via a GIU.
if i am wrong in ubuntu - please tell me.
cheers

---

### Post by PowerBarry43 on 2013-02-06
Hi

You could investigate using a proxy

[http://ubuntuforums.org/showthread.php?t=878376](http://ubuntuforums.org/showthread.php?t=878376)

otherwise I'm on board with just editing the host file. maybe you could write a launcher and/or a bash script to turn on and off the block.

maybe something like an "on" script that asks for credentials then finds the line # 127.0.0.1 [www.facebook.com](www.facebook.com) and replaces it with the same line with no # and an off script that does the reverse. then they could be on the desktop or under a menu and you could block and unblock just with clicks!

Hope this helps!

Barry

---

### Post by Lars Noodén on 2013-02-06
There is a tutorial at HowToForge about [how to block Facebook at the firewall](http://www.howtoforge.com/blocking-facebook-web-trackers-at-the-firewall-for-extra-privacy).  That firewall can be either your router, if it supports it, or your desktop.

Note that the whois search will produce a lot of output:
```

 /usr/bin/whois -h whois.radb.net '!gAS32934' | tr ' ' '\n' 

```

However, some of those networks can be conflated.  Either way works, though.

An added side benefit is that with the blocking, Facebooks plentiful trackers can't follow your movements around the web.

---

