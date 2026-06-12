---
title: "Rootkits"
date: 2007-10-08
forum: General Help
---

### Post by Gremlinzzz on 2007-10-08
This is one way to check your system for rootkits first install.
sudo apt-get install chkrootkit
then when you want to check for rootkits do this command in terminal.
sudo chkrootkit
The reason i posted this info.
[http://www.addict3d.org/news/214295/eBay:%20'Phishers%20Getting%20Better%20Organised,%20Using%20Linux](http://www.addict3d.org/news/214295/eBay:%20'Phishers%20Getting%20Better%20Organised,%20Using%20Linux)'

---

### Post by xpod on 2007-10-08
As talked about [here](http://www.uluga.ubuntuforums.org/showthread.php?t=567050&highlight=botnets)??

I run that rootkit checker once a month or something ......just to see,but it never finds zilch.:)
As far as i understand it all boills down to keeping your system & it`s software updated with the latest security patches as well as taking the appropriate measures if you are going to be running all kinds of servers/services....and of course using a bit of common sense online.

---

### Post by por100pre1 on 2007-10-08
Rkhunter is good too:

```
sudo aptitude install rkhunter
```

To use it:

```
sudo rkhunter --update && sudo rkhunter -c -sk
```

---

### Post by Gremlinzzz on 2007-10-08
A good tutorial on security.
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)
and a good beginners site 
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by Gremlinzzz on 2007-10-08
If this info about how to check for rootkits helped you bump it. so others can benefit from the info.
just type bump

---

### Post by Old *ix Geek on 2007-10-08
> **xpod said:**
> I run that rootkit checker once a month or something ......just to see,but it never finds zilch.:)I run it even less often than that--but I get exactly the same results: ZILCH! :mrgreen:

---

### Post by bodhi.zazen on 2007-10-09
> **Gremlinzzz said:**
> If this info about how to check for rootkits helped you bump it. so others can benefit from the info.
just type bump

Please don't do this. Please teach people to use the search function instead.

Also, if you intend to write a "how-to" please see this forum :

 [http://ubuntuforums.org/forumdisplay.php?f=100](http://ubuntuforums.org/forumdisplay.php?f=100)

And this sticky :

[http://ubuntuforums.org/showthread.php?t=316820](http://ubuntuforums.org/showthread.php?t=316820)

If anyone is interested see also 

[[color=black]Ubuntu Security[/color]](http://ubuntuforums.org/showthread.php?t=510812)

(The psychocats page has already been posted)

---

