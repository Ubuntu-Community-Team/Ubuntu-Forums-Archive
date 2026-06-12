---
title: "Is my computer infected"
date: 2013-11-24
forum: General Help
---

### Post by aoniumo on 2013-11-24
When I was browsing the net, I found that I could not access any websites

Then I checked system monitor and it says my computer is uploading at >125 kbps.  I have nothing open using network except Firefox!!!

Is there away to find out what applications/resources are using the network?[ATTACH=CONFIG]248051[/ATTACH]

---

### Post by sudodus on 2013-11-24
Could it be that you have downloaded something via a torrent, and now you are sharing it?

You can read  this link about [Basic Security]("https://wiki.ubuntu.com/BasicSecurity")

But I am no security expert. [COLOR=#ff0000]Let's wait for someone who knows more about it to give advice![/COLOR]

---

### Post by aoniumo on 2013-11-24
Nope torrent is off.  has been since I started my computer

---

### Post by grahammechanical on 2013-11-24
My guess is that the machine is sending and that is what is stopping you from accessing other sites. System Monitor has a Processes tab. That will you what processes are running. You can also the command top in a terminal and see what is using up resources. do you have a Ubuntu One storage account? Is it syncing?

Regards.

---

### Post by The Cog on 2013-11-24
This command will list the current connections and the id/name of the process that owns them.
```
sudo netstat -ntup
```
That would be a start. If you want, you could then kill the process and see if that stops the traffic.

---

### Post by aoniumo on 2013-11-24
> **The Cog said:**
> This command will list the current connections and the id/name of the process that owns them.
```
sudo netstat -ntup
```
That would be a start. If you want, you could then kill the process and see if that stops the traffic.

Thanks.

---

### Post by leeper69 on 2013-11-24
Hi you can also use system monitor to list and disable runing processes just click on the processes tab scrool to the process you want to kill hilight it and use the right mouse button to get the dropdown menu with the choise kill.
I find that netstat -punt works the same as aoniumo,s code and it a lot easeyer for me to remember.

---

