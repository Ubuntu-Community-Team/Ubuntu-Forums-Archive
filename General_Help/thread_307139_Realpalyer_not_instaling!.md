---
title: "Realpalyer not instaling!"
date: 2006-11-26
forum: General Help
---

### Post by Bengaul on 2006-11-26
Hi there,

I am trying to install real player, and am following this guide:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Player_.28RealPlayer_10.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Player_.28RealPlayer_10.29)

However when I try I get this in the terminal:

ben@bigben:~$ sudo apt-get install realplay
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package realplay

I enabled the PLF repo as per the guide. Does anyone know if it has moved?

Many thanks.

---

### Post by junglepeanut on 2006-11-26
I think you can get realplayer from ubuntus commercial repository i.e.

 deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

---

### Post by junglepeanut on 2006-11-26
I suggested that as my connection to plf has been down for quite some time.

Also you could just do the second method on the page 
> Alternative Source

    * Download Realplayer's Official Linux Version 

Then add execute permissions to the installer and execute it.

```
chmod +x RealPlayer10GOLD.bin
sudo ./RealPlayer10GOLD.bin
```


---

### Post by Bengaul on 2006-11-26
Thanks, I do have this in the repos:

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

As I have edgy.

Can I still get it from the dapper repo?

---

### Post by junglepeanut on 2006-11-26
Should be fine, it is just a binary if I recall. Anyone can correct me if they want but I am pretty sure you will be fine. 

If you still cautious just get the file from real themselves as posted above and follow the commands.

I am using fiesty and have debian, edgy, dapper and feisty repos. (for the things I can only get in certain places like commercial canonical)

My realplayer for feisty and edgy was retrieved that way.

---

