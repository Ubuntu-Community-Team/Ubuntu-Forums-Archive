---
title: "Pipe conky output :?"
date: 2019-02-13
forum: General Help
---

### Post by Furycd001 on 2019-02-13
HI. I'm looking to pipe the output of my conky.conf and display it with [Genmon]("https://goodies.xfce.org/projects/panel-plugins/xfce4-genmon-plugin#screenshots"). Genmon is an xfce4-panel-plugin that can essentially run scripts or display text. I have never tried to pipe anything before & have basic conky knowledge. Duck wasn't really much help which is why I'm here. Anyway.. Help is very much appreciated....

[[ LINK TO MY CONKY.CONF ]]("https://paste.ubuntu.com/p/7xrRqYtQZG/")

---

### Post by again? on 2019-02-13
Just had a quick look and I can achieve something by sending the conky output to console.
Then saving that output to a text file and using awk to display the last line of that file.
Add to your conky config...
```
out_to_x no
out_to_console yes
```

Start conky with...
```
conky -q -c *[COLOR="#696969"]/your/path/to/conkyconfig[/COLOR]* > /tmp/conkysysinfo.txt
```

Then as genmon command use...
```
awk 'END{print}' /tmp/conkysysinfo.txt
```

Set the genmon period(secs) to your liking.

---

### Post by Furycd001 on 2019-02-13
> **guber2 said:**
> Just had a quick look and I can achieve something by sending the conky output to console.
Then saving that output to a text file and using awk to display the last line of that file.
Add to your conky config...
```
out_to_x no
out_to_console yes
```

Start conky with...
```
conky -q -c *[COLOR=#696969]/your/path/to/conkyconfig[/COLOR]* > /tmp/conkysysinfo.txt
```

Then as genmon command use...
```
awk 'END{print}' /tmp/conkysysinfo.txt
```

Set the genmon period(secs) to your liking.

Wow this is amazing. Thank you so very much. This is exactly what I was looking for and it works amazingly....

---

### Post by again? on 2019-02-13
No problem. I also use xfce but I use tint2 as my panel and a matching conky to display sysinfo.
[ATTACH=CONFIG]282505[/ATTACH]

Similarly you can use a shortened xfce4-panel with a background image to match conky.
[ATTACH=CONFIG]282507[/ATTACH] [ATTACH=CONFIG]282509[/ATTACH]
Didn't know about genmon. Have to have another look at xfce4-panel.

---

### Post by QIII on 2019-02-13
An example of a similar process I use on my conky ...

First, I have a script that creates a text file of the output of virshlist every ten seconds:

```
#!/bin/bash
while true
do
echo "Local VMs" > ~/.conky/virshlist.txt
echo " " >> ~/.conky/virshlist.txt
virsh list --all >> ~/.conky/virshlist.txt
echo " " >> ~/.conky/virshlist.txt
echo " " >> ~/.conky/virshlist.txt
echo "Remote VMs on ZACK" >> ~/.conky/virshlist.txt
echo " " >> ~/.conky/virshlist.txt
virsh -c qemu+ssh://192.168.xxx.xxx/system list --all >> ~/.conky/virshlist.txt
sleep 10
done
```

Then, in conky one of the lines is:

```
{exec cat ~/.conky/virshlist.txt | fold -w 52}
```

There is a lot more real estate available in conky than on a panel.


[ATTACH=CONFIG]282510[/ATTACH]

---

