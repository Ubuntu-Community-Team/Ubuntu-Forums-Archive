---
title: "Eclipse3.2 Radrails ruby does not apear in preferences"
date: 2007-10-05
forum: General Help
---

### Post by daicoden on 2007-10-05
Hi, 
I've been trying for a while to get eclipse working with radrails.  I finally got it to work but had to do a few workarounds so I thought I would put this here since I did not find the solution on any forums.  Maybe there is an easier way?  Anyway here it is for those of you who are also stuck.
```

sudo apt-get install eclipse

```
eclipse for some reason installs java 1.4 even if you already have 1.5 which causes problems

If you don't have it...
```

sudo apt-get install sun-java5-jre

```

now heres the weird part I had to do extra...
go into /usr/lib/jvm/
```

sudo rm java-gcj -r
sudo ln -s java-1.5.0-sun-1.5.x.x/ java-gcj

```

Now if you already installed radrails with their documentation rails and ruby should pop up in the window -> preferences menu.  Otherwise follow the instructions here.

[http://www.aptana.com/docs/index.php/Integrating_RadRails_with_Aptana](http://www.aptana.com/docs/index.php/Integrating_RadRails_with_Aptana)

I found all sorts of people saying you need java1.5 but no way to get eclipse to drop 1.4 no idea why!

---

