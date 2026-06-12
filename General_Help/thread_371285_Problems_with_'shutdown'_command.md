---
title: "Problems with 'shutdown' command"
date: 2007-02-26
forum: General Help
---

### Post by andrew.46 on 2007-02-26
Hi,

 I have been experimenting (=playing) with the shutdown command in Xubuntu 6.10 ie using a terminal to shut the computer down rather than the GUI. I have been using:

```
sudo shutdown -h now
```

and:

```
sudo shutdown -h -r now
```

 But I notice that often this appears to damage the various items in the panels of the GUI when I log back on. For example the XFCE Menu will be completely missing or the Mail Watcher will not function. Both can easily be restored.

 Am I doing something incorrectly? I am only up to page 12 of 'Essential Commands: The Linux Pocket Guide' by Daniel Barrett so I am sure there is a world more of damage that I can inflict on my machine :confused: 

                         Andrew

---

### Post by kpkeerthi on 2007-02-26
Just wondering why -h was specified along with -r (You either want to **h**alt or **r**eboot. right?). If I have to reboot my box I would just do sudo shutdown -r now. I'm not trying to say that using -h -r togther would have damaged your panels/menus but I never use -h and -r together and my panels are intact.

---

### Post by amphet on 2007-02-26
I have the same problem but it's because I can't get my machine to shutdown correctly I've given up.

---

### Post by majoridiot on 2007-02-27
try:

```
sudo shutdown -h now
```

i've never experienced any issues this way.

alternatively:

```
sudo shutdown -h -P now
```

(-P should empasize you want the halt action to be power down, 
in case there's any question)

---

### Post by andrew.46 on 2007-02-27
Hi,

 Thanks for your reply:

> **kpkeerthi said:**
> Just wondering why -h was specified along with -r (You either want to **h**alt or **r**eboot. right?). If I have to reboot my box I would just do sudo shutdown -r now. I'm not trying to say that using -h -r togther would have damaged your panels/menus but I never use -h and -r together and my panels are intact.

 You are quite right of course, I am not sure what I was thinking :-) I have a suspicion that there is a small gremlin in my system that is somehow set off by the shutdown command. I could either spend quite some time ferreting it out or I couls leave it until April when I will do a clean install of Feisty. This might be easier :-)

                            Andrew

---

