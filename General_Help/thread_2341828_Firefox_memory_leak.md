---
title: "Firefox memory leak"
date: 2016-11-01
forum: General Help
---

### Post by Firubat on 2016-11-01
I think I have some kind of memory leak on firefox.  It is usually above 1.2GB and now reached 2GB of RAM (out of 3GB), with not so many tabs. I have the Tab-memory-usage addon, and summing up all the tabs I get 550MB. I also have the addon-memory addon, which says the total addon memory usage is 100MB. All together there's still about 1.3GB RAM unaccounted for!
Next I did the following experiment: I closed all tabs but a blank one. This reduced memory usage to a bit more than 1GB. I entered [FONT=courier new]about:memory[/FONT] and pressed the [FONT=courier new]Minimize memory usage[/FONT] button but that didn't change alot.
Then I started loading the system by opening multiple programs, to see if the memory gets freed. When the RAM reached it's limit (with firefox still taking ~1GB) the system started swapping, reducing firefox to ~500MB. But the memory wasn't really free - just swapped, and the total RAM usage was nearing 100%. Then I closed everything but firefox, and indeed the swap didn't change. Only when I closed firefox, the memory in both RAM and swap was released.

What can I do to stop this from happening?

I have Xubuntu 16.04.1 installed, currently using the MATE-desktop environment (although the problem was present also on the default Xubuntu environment).
Dell Inspiron N4030 3GB RAM

---

### Post by &amp;KyT$0P# on 2016-11-01
Does the memory leak occur in [Safe Mode]("http://kb.mozillazine.org/Safe_Mode")?
Does it occur in a new [profile]("http://kb.mozillazine.org/Profile")?

---

### Post by Firubat on 2016-11-02
I tried safe-mode now, it reached 1.2GB on itself on natural browsing, and then I artificially upped it to 2GB by opening many youtube tabs (don't know if it has the same effect). Then I closed all tabs again and this time it reduced to ~500MB. When I just start firefox with no tabs it takes 220 MB.

---

### Post by Pablo_San_Martn on 2016-11-02
What about disabling memory cache in about:config or setting a limit to it by creating an integer entry ([COLOR=#ff6600]browser.cache.memory.capacity[/COLOR])?

---

### Post by Firubat on 2016-11-02
Oh I saw this suggestion about "[COLOR=#ff6600]browser.cache.memory.capacity[/COLOR]" elsewhere, but I didn't realize I need to create it myself - I thought that if it doesn't appear it just means I'm reading an out-dated guide :P. What value would you suggest (I have 3GB RAM)?

There is a "[COLOR=#ff6600]browser.cache.**disk**.capacity[/COLOR]" entry set to 358400, does it matter?

---

### Post by bearlake on 2016-11-02
> **Firubat said:**
> Oh I saw this suggestion about "[COLOR=#ff6600]browser.cache.memory.capacity[/COLOR]" elsewhere, but I didn't realize I need to create it myself - I thought that if it doesn't appear it just means I'm reading an out-dated guide :P. What value would you suggest (I have 3GB RAM)?

There is a "[COLOR=#ff6600]browser.cache.**disk**.capacity[/COLOR]" entry set to 358400, does it matter?

Why not set it here in FireFox.

---

### Post by Pablo_San_Martn on 2016-11-02
> **Firubat said:**
>  What value would you suggest (I have 3GB RAM)?

It really depends on your usage - how much memory would you like Firefox to use? Up to a GB in total? You can check current usage at the address about:cache. If you don't want to use the memory cache at all, you should set [COLOR=#ff6600]browser.cache.memory.enable[/COLOR] to "false".

> **Firubat said:**
>  There is a "[COLOR=#ff6600]browser.cache.**disk**.capacity[/COLOR]" entry set to 358400, does it matter?

That refers to your hard disk or solid state drive, not RAM. It's slower to access, but won't eat up your memory. You can leave it as is or give it more space, say 512000.

---

### Post by Pablo_San_Martn on 2016-11-02
> **bearlake said:**
> Why not set it here in FireFox.

Isn't that just for the disk cache, though?

---

### Post by Firubat on 2016-11-02
When I go to [FONT=courier new]about:cache[/FONT], it says under "Memory": [FONT=courier new]Maximum storage size:     27648 KiB[/FONT]
This is pretty low, so I don't think that's where the problem is...

---

### Post by &amp;KyT$0P# on 2016-11-02
> **Firubat said:**
>  I artificially upped it to 2GB by opening many youtube tabs (don't know if it has the same effect).
Not really surprising given that Youtube has a lot of active content.

> Then I closed all tabs again and this time it reduced to ~500MB. When I just start firefox with no tabs it takes 220 MB. 
RAM usage that much lower in Safe Mode *usually* means one or more of your extensions are the problem.  Use [Standard diagnostic]("http://kb.mozillazine.org/Standard_diagnostic_-_Firefox#Extension_issues") to figure out which.

Please let us know the results.

---

### Post by bearlake on 2016-11-02
> **Pablo_San_Martn said:**
> Isn't that just for the disk cache, though?

Yes your correct.

---

### Post by Firubat on 2016-11-04
> **halogen2 said:**
> RAM usage that much lower in Safe Mode *usually* means one or more of your extensions are the problem.  Use [Standard diagnostic]("http://kb.mozillazine.org/Standard_diagnostic_-_Firefox#Extension_issues") to figure out which.

Please let us know the results.


I did some experimentation. I noticed that sometimes, when I close all tabs but a blank one, first there is a drastic drop in RAM usage, but then it starts to slowly rise back up again (with no action on my side). After a long attempt to pin-point the problem, I realized it was not an extension, but a script running through Greasemonkey - [TeX for Gmail]("http://alexeev.org/gmailtex.html").
I'm not sure this is the only problem, as I think a part of the problem might arise only after a longer time of browsing than just opening many tabs and closing them. I disabled the script and will see if things are well.

BTW - is it reasonable to have 400-500MB RAM usage after closing all tabs but a blank one? The only addons I use are adblock plus, about:addons-memory, Tab memory usage and Ubuntu modifications.
And one last thing - is the Ubuntu modifications addon necessary? What does it do?

---

### Post by Firubat on 2016-11-09
Another piece of info: when I disable "Ubuntu modifications", it seems that the RAM usage splits differently between Firefox and "web content" (see screenshot) - usually Firefox takes most of the RAM while the web content uses about 150MB, but now the web content takes 1.2GB and firefox ~500MB.

[ATTACH=CONFIG]272048[/ATTACH]

---

