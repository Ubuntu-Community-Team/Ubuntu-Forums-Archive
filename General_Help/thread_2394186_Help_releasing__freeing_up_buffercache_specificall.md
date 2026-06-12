---
title: "Help releasing / freeing up buffer/cache specifically used by Gnome session"
date: 2018-06-13
forum: General Help
---

### Post by sp40140 on 2018-06-13
There is a well documented problem of huge memory leak in Gnome Session.
Some of the leaks have been fixed in Gnome but haven't been pushed down to Ubuntu yet.
So, I am having to keep rebooting my machine to free up ram or system freezes up.

Now. until the fixes are pushed, I would like to set up a script (or something like it) to manually release the buffer / cache. Especially used / marked by Gnome session (as there are other valid programs using buffer / cache as well).

I tried (over ssh):
```

gnome-session --replace

```
did not work. I don;t get any error but I don't see any change in RAM usage (free command used). 

Help please.

Some links to the leak problem:
[https://feaneron.com/2018/04/20/the-...l-memory-leak/]("https://feaneron.com/2018/04/20/the-infamous-gnome-shell-memory-leak/")
[https://bugs.launchpad.net/ubuntu/+s...l/+bug/1672297]("https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1672297")

PS: Running 18.04.I already have an old thread (from 17.10) but that was specifically for leak and I am leaving it alone.

---

### Post by TheFu on 2018-06-14
GUI stuff can't be done over a remote session due to the way that X/Windows clients and servers work.
Also, does gnome-session stop, close, then restart the X session?  I'd think that a logout and login would be necessary.

p.s. - I don't use gnome.

---

### Post by logix2 on 2018-06-14
I believe TheFu is right, a complete session restart is required, so you'll either have to logout / login, or restart GDM ("systemctl restart gdm.service").

---

### Post by sp40140 on 2018-06-14
Can I use "DISPLAY" variable" and "nohup" in some combination to accomplish this over ssh?

I will try to restart the gdm service and see if that frees up the ram.

---

### Post by TheFu on 2018-06-14
no. You can kill the x/windows process, but that will term-close all running X-apps tied to the X/server.  xorg is the process on 16.04 and it runs as root.

---

### Post by sp40140 on 2018-06-14
Restarting GDM didn't return any error. But no impact on ram / cache / buffer.

OK. I know this could be dangerous, but is there anyway / command / process by which I can directly clean up the cache?

I tried xfce, but don't like it much. Still running on my laptops but I rather not use it on server.
Other than switching to something other than gnome, do I have any options?

---

### Post by TheFu on 2018-06-14
Any options?
* reboot
* don't run any GUI on a server

---

### Post by sp40140 on 2018-06-23
@TheFu and other experts.
So, I switched to "cinnamon" instead of Gnome. And my buffer/cache still kept getting filled up not freeing automatically. Since Cinnamon is derivative of Gnome, I then installed xfce4. Still same symptoms.
I started looking at different places.
What I realize (currently) is that when I access/copy files from that computer (as I use it as server) the buffer keeps getting used but never frees up even after files are done copying. The method used doesn't make difference. I used samba and ssh (scp). Both eat up ram and don't release it back.
After looking around. I found these two commands to free up buffer. I am not sure how risky these are. 
Could you add your thoughts?
```
 [COLOR=#242729][FONT=Consolas]echo 3 > /proc/sys/vm/drop_caches[/FONT][/COLOR]
``` 
AND
```
sudo sysctl vm.drop_caches=1
```
Both of these commands free up the buffer/cache.
Now, someone also mentioned the 
```
fincore 
``` command from "linux-ftools" to see what is in the cache, but looks like it's not available in repos.

All I am looking for is ram managed well so that it doesn't crash my machine.

---

### Post by sp40140 on 2018-06-27
Bump

---

