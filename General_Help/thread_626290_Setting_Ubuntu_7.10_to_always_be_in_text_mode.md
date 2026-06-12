---
title: "Setting Ubuntu 7.10 to always be in text mode"
date: 2007-11-28
forum: General Help
---

### Post by sandman887 on 2007-11-28
Hello everyone,

Yesterday I set up a file server in my room, and since I am mainly going to be accessing it over the network, I wanted to set it to textmode (runlevel 3).So I vim /etc/inittab but.......it's not there!!!

So I google and search around on here, but all the results from both sources seem to only be talking about installing in text mode, or "Help! My graphics card isn't working, and I can only use text mode!". I haven't found anything about how to ---SET---- it to text mode, so it's always on text mode. I hate this upstart crap, why did the ubuntu team have to go do something wierd... What was wrong with inittab? Everyone knew how to use it. 

Sorry, didn't come here to rant, it's just that I'm totally confused about why they did it and more importantly, WHAT to do about it. I went to upstart.ubuntu.com but I didn't really figure much out from that about how to set it to text mode. I don't like the idea of having to issue a command each time to get it to text mode. It definitely seems like they have made it more difficult and harder this way. 

Also, I searched on ubuntu's site about where to give my 2 cents worth and couldn't find that, either. This is too bad. Up until this I really loved ubuntu. apt-get install is so easy, it's the easiest way to install anything I've ever come across. And there are a lot of good things about ubuntu, but this upstart is like a sore thumb.

Anyway, is there some way to set /etc/event.d/rc_local or whatever it is so that it ALWAYS runs in text mode? There has got to be some way to configure it so that X isn't running when I don't need it to.

Thanks in advance, guys.

---

### Post by zippy028 on 2007-11-29
You may want to look at this [thread]("http://ubuntuforums.org/showthread.php?t=611759")

[http://ubuntuforums.org/showthread.php?t=611759](http://ubuntuforums.org/showthread.php?t=611759)

---

