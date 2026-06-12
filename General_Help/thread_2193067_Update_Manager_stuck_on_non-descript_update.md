---
title: "Update Manager stuck on non-descript update"
date: 2013-12-11
forum: General Help
---

### Post by pl3m on 2013-12-11
Hi,

Ubuntu 12.04 LTS. My Update manager reports that I have an update available. However: there is no description of the update whatsoever.
The updates list is empty. It mentiones that "there is 1 update available 228kB will be downloaded" and then the description of the update is completely empty aswell..

Has anyone encountered this? How to get rid of it? 
Looks a bit scary; is someone trying to install/update something sneaky?? or is this just crummy software?

regards,

Peter

---

### Post by monkeybrain20122 on 2013-12-11
Type 

```
sudo apt-get upgrade

```
and see what it is

I use synaptic as my gui for package management. 

either 
```
sudo apt-get install synaptic
```

or install it with the Software Center
The update-manager is pretty dumb. You can disable it by go to Settings and set "automatic check for update" to never

---

### Post by pl3m on 2013-12-12
Ok,

Well that's a workaround. I've allready got Synaptic. I was just very curious to find out what the reported update is. apt-get and tghe software center were not reporting anything.

Just now (10 sec ago)  found out what it is: I had to downgrade libpixman. It seems the upgrade manager cannot stomach this. Used synaptic to straighten it out and now the upgrade manager is fine again.

Thanks

---

