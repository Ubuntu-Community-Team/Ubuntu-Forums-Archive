---
title: "Separate sessions and XORG.conf's"
date: 2007-10-08
forum: General Help
---

### Post by chunkified on 2007-10-08
Hello,

I'm using Ubuntu 7.10 and I need to know whether it's possible and how to create 2 sessions that each use their own xorg.conf.

I want one to use Compositing and one that has Compositing disabled so that I can use Maya?
I know i'll have to restart X server which isn't a problem but is there any way this is possible either with multiple sessions or users?

Some extremely detailed help would be lovely as i'm pretty much a linux n00b, any help would be greatly appreciated hehe..!

Thanks :popcorn:

---

### Post by chunkified on 2007-10-08
anyone?? *mini bump*

---

### Post by distroman on 2007-10-09
Because you're using ati/xgl?
It's quit some time since I used xgl so I can't be of much help.
I am not recommending (might be outdated) that guide but maybe a place to start if your looking to create a separate x session.
[http://ubuntuforums.org/showthread.php?t=174233](http://ubuntuforums.org/showthread.php?t=174233)

---

### Post by bodhi.zazen on 2007-10-09
> **chunkified said:**
> Hello,

I'm using Ubuntu 7.10 and I need to know whether it's possible and how to create 2 sessions that each use their own xorg.conf.

I want one to use Compositing and one that has Compositing disabled so that I can use Maya?
I know i'll have to restart X server which isn't a problem but is there any way this is possible either with multiple sessions or users?

Some extremely detailed help would be lovely as i'm pretty much a linux n00b, any help would be greatly appreciated hehe..!

Thanks :popcorn:

Actually is is not hard to do this.

See this thread : [http://ubuntuforums.org/showthread.php?t=271674](http://ubuntuforums.org/showthread.php?t=271674)

You will need to launch your X sessions from the command line, usually with GDM disabled ...

---

### Post by chunkified on 2007-10-09
thanks for your quick replies!
in 7.10 i didn't have to instal XGL or modify my xorg.conf to get Compiz Fusion working. I think the Ubuntu team got that sorted for ATI people so that it was more "out of the box". Not sure whether it's XGL or just new drivers...
--
haven't tried the script yet but looks awesome. how would I modify it so that I can use a separate xorg or with compositing off...?

---

### Post by bodhi.zazen on 2007-10-09
It should work with: ```
startx -config <xorg.config_file> -- :1
```

---

### Post by chunkified on 2007-10-09
i've followed the tutorial.
when i do:

```
bash virtualX
```
then
```
startx -config xorg_maya.conf -- :1
```

the screen goes black for 3 seconds then comes back to my current X server session.

if i do: 

```
bash virtualX
```
then
```
startx -- :1
```

i get taken to a new X server but it's a white and black dotted screen with a black X cursor.

:(

any light you could shed on this would be fantastic!! :D

---

### Post by bodhi.zazen on 2007-10-09
> **chunkified said:**
> i've followed the tutorial.
when i do:

```
bash virtualX
```
then
```
startx -config xorg_maya.conf -- :1
```

the screen goes black for 3 seconds then comes back to my current X server session.

Try launching from the console (Ctrl-Alt-F1, log in)

You may need to kill GDM

sudo /etc/init.d/gdm stop # This will terminate your current X session.

> if i do: 

```
bash virtualX
```
then
```
startx -- :1
```

i get taken to a new X server but it's a white and black dotted screen with a black X cursor.

:(

any light you could shed on this would be fantastic!! :D

Yep, That sounds like X. Try starting gnome :

```
/usr/bin/startx /usr/bin/gnome-session -- :1
```

---

