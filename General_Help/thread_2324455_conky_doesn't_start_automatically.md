---
title: "conky doesn't start automatically"
date: 2016-05-14
forum: General Help
---

### Post by jose_antonio4 on 2016-05-14
Hi guys!!!

I tried to start conky lua from start up applications, i work with ubuntu 16.04 and i installed conky, conky start perfectly from terminal with this command:
[B]conky -c ./.conky/conkyrc &

[/B]however when i boot the computer conky doesn't start, i set **conky -p 30 -c ~/.conky/conkyrc & **even if a set** conky [B]-c ~/.conky/conkyrc conky **[/B]doesn't start, what it's my mistake?

---

### Post by RobGoss on 2016-05-14
Hello and welcome, I also use Conky and the method I use to get it to startup automatically is to add it to your **>** **Startup Applications **choose **>** **Add** and enter the following **conky-p10 **click **save **when finished. Where -p10 means wait 10 seconds after boot to start up** Conky,** You can also use** conky --pause=10** or set the timeout to whatever you feel works for you

---

### Post by ajgreeny on 2016-05-14
Try removing the ampersand & from the command; it is needed only in some specific situations and not for the autostart commands, as far as I'm aware.

---

### Post by RobGoss on 2016-05-14
Hello Ajgreeny yes after adding the command **conky-p10 **I get this **sh "/home/username/.conky/conky-startup.sh"** as a final path seems to work well

---

### Post by jose_antonio4 on 2016-05-20
it's doesn't start actually i have this: **conky -p 10 -c ~/.conky/conkyrc**

---

### Post by RobGoss on 2016-05-20
> **jose_antonio4 said:**
> it's doesn't start actually i have this: **conky -p 10 -c ~/.conky/conkyrc**


Try adding this to the startup but add your user were you see ( username ) and see if that works  [B]sh "/home/username/.conky/conky-startup.sh"  
[/B]

---

### Post by jose_antonio4 on 2016-05-21
> **RobGoss said:**
> Try adding this to the startup but add your user were you see ( username ) and see if that works  [B]sh "/home/username/.conky/conky-startup.sh"  
[/B]

Hea!!!!
Thank's, that works :)

---

### Post by RobGoss on 2016-05-21
Great glad I could help if you don't mind can you mark this thread as solved, you can use the **Thread Tool** tab at the top of this post.

---

