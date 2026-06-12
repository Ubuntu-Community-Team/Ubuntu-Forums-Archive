---
title: "About Networking Ports"
date: 2008-04-21
forum: General Help
---

### Post by fxguenea on 2008-04-21
Hi, i've been downloading some stuff via torrents and i noticed that whatever my connection speed was, downloads keep slow... (i say speed connection, because it was upgraded from 600 kps to 2mbps). A friend came out with enabling ports and configuring some of the router's firewall might be the solution .. Do you guys know how to do that???

Most of thanks!

PD: When i create a script, like

sudo gedit /.../New_Script

How do i run it... like in a executable way??? 

thanks again.

---

### Post by amingv on 2008-04-21
When downloading[ torrents]("http://en.wikipedia.org/wiki/BitTorrent_%28protocol%29"), the speed depends not only on your connection, but on the number of peers that are seeding the file and their upload speed, in short; the more people seeding it, the faster it'll go. I don't believe opening ports will do any better.

> **fxguenea said:**
> 
PD: When i create a script, like

sudo gedit /.../New_Script

How do i run it... like in a executable way??? 

thanks again.

First you need to place a [shebang]("http://en.wikipedia.org/wiki/Shebang_%28Unix%29") on top of the script and then give it execute permission. A very simple example:

[PHP]#!/bin/bash
#   That's the shebang, it must be the first line of the script.

echo "This script runs on it's own"[/PHP]

Then, to give it executable permission:
```
chmod a+x myscript.sh
```

and to run:
```
./myscript.sh
```

---

### Post by DBrocks on 2008-04-21
Sometimes, you dont have to chmod the thing, or add the shebang (although it's a good precaution, if your distributing your script to your friends.) You can just write the script with a ".sh" extention, then run the following command:
```
 
sh ThisIsYourScript

```
I do this for my system, but if you are distributing your script, definately add the shebang, and the chmod.
 
Peace!

---

### Post by Vermind on 2008-04-21
Question 1: This is largely dependent on Your network configuration. Do You have a router with a firewall? Or do You firewall with Your Ubuntu box? Do You use wondershaper or some other way of throttling Your network speed down? Have You limited Your torrent program download speed?

Question 2: Running a script is usually done by first making it executable, i.e. right-click the script in nautilus and "allow executing as program" or giving the execute rights in the terminal:```
chmod 750 newscript
```. To run a script, either click it with nautilus and choose "run in terminal" or "run", or do something similar to one of these:
```
cd the/path/to/my/script
./newscript
```
```
cd the/path/to/my/script
sh newscript
```
```
the/path/to/my/script/newscript
```
```
sh the/path/to/my/script/newscript
```
```
/home/me/the/path/to/my/script/newscript
```
```
sh /home/me/the/path/to/my/script/newscript
```

---

