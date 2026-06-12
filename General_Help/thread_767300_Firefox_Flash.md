---
title: "Firefox Flash"
date: 2008-04-25
forum: General Help
---

### Post by crazymanjared on 2008-04-25
I accidentally installed the wrong plugin when it said i needed flash, i installed something that DOES work with flash, but every single thing i that uses flash has a big "play" button over it...its really annoying and i was hoping someone could help me figure out how to get rid of that plugin. I already checked plugins/add-ons in firefox, nothin there.

---

### Post by ubuntu-freak on 2008-04-25
> **crazymanjared said:**
> I accidentally installed the wrong plugin when it said i needed flash, i installed something that DOES work with flash, but every single thing i that uses flash has a big "play" button over it...its really annoying and i was hoping someone could help me figure out how to get rid of that plugin. I already checked plugins/add-ons in firefox, nothin there.

 
Did you install Gnash by mistake? See part 1 of my [how-to](http://ubuntuforums.org/showthread.php?t=766683) and try the purge/install command for Adobe Flash. Check out the other sections also.
 
Nathan

---

### Post by crazymanjared on 2008-04-25
Well I guess I'm a complete idiot, but i have no idea which plugin i installed instead of flash player. I  followed your purge guide thing but that didn't help it. I can take a screen shot if you think that will help.

---

### Post by rfruth on 2008-04-25
I get the big play button as well - not sure how to "fix" this :confused:

---

### Post by crazymanjared on 2008-04-25
Heres the screen shots of my add-ons tab, and the big play buttons.

---

### Post by Islington on 2008-04-25
Guys make sure that you remove swfdec-mozilla in synaptic or by doing 

```
sudo apt-get purge swfdec-mozilla 
```

---

### Post by crazymanjared on 2008-04-25
> **Islington said:**
> Guys make sure that you remove swfdec-mozilla in synaptic or by doing 

```
sudo apt-get purge swfdec-mozilla 
```

THank you sooooo  much, you have no idea how happy you've made me, no i have everything i want working in linux, working.

---

### Post by ZooLA_IL on 2008-04-25
Yep. It works for me as well. thank you.:guitar:

---

### Post by Ctroncoa on 2008-04-25
> **Islington said:**
> Guys make sure that you remove swfdec-mozilla in synaptic or by doing 

```
sudo apt-get purge swfdec-mozilla 
```

WOW that worked!! THANKS!, anyway, why does one have to remove swfdec??, if someone could explain that would be great.

---

### Post by tango_ninja on 2008-04-25
if you installed it via firefox you should be able to type
```
about:plugins
```
into the address bar and see a shot of all plugins currently installed (more detailed than going through the menu).

---

### Post by Islington on 2008-04-26
> **Ctroncoa said:**
> WOW that worked!! THANKS!, anyway, why does one have to remove swfdec??, if someone could explain that would be great.

Well I dont know about anyone else, but it was the first option that firefox offered, so I went ahead and installed it, about 30 seconds after I realized something was wrong. :/

---

### Post by rfruth on 2008-04-26
Yes the default is "wrong" but sudo apt-get purge swfdec-mozilla worked great, thanks !

---

