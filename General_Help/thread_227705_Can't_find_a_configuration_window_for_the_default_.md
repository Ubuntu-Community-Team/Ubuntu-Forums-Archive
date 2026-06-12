---
title: "Can't find a configuration window for the default torrent client in Dapper"
date: 2006-08-02
forum: General Help
---

### Post by zugu on 2006-08-02
How do I change the ports the default BitTottent client is listening to? Many trackers ban port numbers < 10000, and I need the client to do something similar to BitTornado (that is, randomly choosing ports between 10000 and 60000).

---

### Post by easyease on 2006-08-02
hmmm dunno mate but i use azureus and it works great. even uses UPnP.

---

### Post by zugu on 2006-08-02
Thank you for the answer, but I'm not looking for alternatives, I just think that something that comes with Ubuntu (the bittorrent client) might lack an important feature (changing the default ports).

It's something that almost all respectable bittorent clients do nowadays. Changing/randomizing ports is essential, as more and more ISPs block bittorent traffic.

If I can't find what I'm looking for (a way to change the ports in the client) I think it is normal to fill in a bug report.

---

### Post by it.henrik on 2006-08-02
With Azureus you can use connection encryption. It makes it harder for ISP to filer BT traffic.

---

### Post by easyease on 2006-08-02
yes i do understand that ubuntu's default applications arent the most fully featured of their genre sometimes, i think thats more of an ethical matter than caused by neglect.

---

### Post by cantormath on 2006-08-02
Azureus makes what you are try to do easy.
if you are just having trouble installing it, try  installing to with automatix.
[http://ubuntuforums.org/showthread.php?t=190025](http://ubuntuforums.org/showthread.php?t=190025)

---

### Post by easyease on 2006-08-02
we can all say we use azureus but zugu seems determined not to....
 not sure why.

---

### Post by zugu on 2006-08-04
I prefer not to use Azureus because I find it bloated. Not to mention I can't even begin to understand why Mozilla Browser is a dependency of Azureus. Plus I have to install Java and other things.

ANyway, nevermind, someone on IRC told me how to solve my problem. I'll post here the solution, maybe someone else will be interested in it:

alacarte menu editor > internet > right click on bittorrent, then in the Command dialog, edit it so it becomes: ```
gnome-btdownload --minport 10000 --maxport 15000 %U
```

The client will change ports randomly for each torrent.

---

### Post by mrcanard on 2007-10-13
> **zugu said:**
>  

ANyway, nevermind, someone on IRC told me how to solve my problem. I'll post here the solution, maybe someone else will be interested in it:

 
 

Thanks, That's what I was looking for!

---

