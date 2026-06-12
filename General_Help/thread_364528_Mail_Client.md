---
title: "Mail Client"
date: 2007-02-18
forum: General Help
---

### Post by Orfeus on 2007-02-18
Does anyone know any good mail client which can access hotmail (http) and imap?

---

### Post by teaker1s on 2007-02-18
thunderbird is good, but hotmail unless you are a long term valued customer or pay for it then email client access is blocked

---

### Post by Orfeus on 2007-02-18
i m using it for years and everyone knows this as my mail. I couldn't  find any client for it but i was hoping that u might know something...

---

### Post by bollix47 on 2007-02-18
I use Thunderbird for hotmail, yahoo, my isp's account.  You will need the webmail and hotmail extensions.

You can download Mozilla Thunderbird using Synaptic.

You can find more info about the extensions [_here_]("http://forums.mozillazine.org/viewtopic.php?t=439333").

---

### Post by Orfeus on 2007-02-18
the page is not working but i found the extension somewhere else

i still cannot get it work.

is there a step by step guide?

---

### Post by bollix47 on 2007-02-18
The instructions for your server settings in thunderbird and for the webmail setup are [_here_]("http://webmail.mozdev.org/").

The only things I had to change in linux were the ports.

I used:

POP - 1025
SMTP - 1026
IMAP - 1027

They need to be changed in both the webmail preferences and in Thunderbird under ... edit - account - settings - server settings

---

### Post by Orfeus on 2007-03-03
i tried it but it says something about negative vibes...

---

### Post by bollix47 on 2007-03-03
Make sure you have the latest versions.

Go into tools - extensions - 

Click on find updates.

webmail - 1.0.15
hotmail - 1.0.20

You can get more info in [_their forum_]("http://forums.mozillazine.org/viewtopic.php?t=439333").

---

### Post by CocoAUS on 2007-03-03
You can also try FreePOPs ( [http://www.freepops.org/en/](http://www.freepops.org/en/) ) if you can't get the Thunderbird extension working.

---

### Post by Orfeus on 2007-03-03
> **bollix47 said:**
> Make sure you have the latest versions.

Go into tools - extensions - 

Click on find updates.

webmail - 1.0.15
hotmail - 1.0.20

You can get more info in [_their forum_]("http://forums.mozillazine.org/viewtopic.php?t=439333").

this are the versions i got

---

### Post by kobewan on 2007-03-09
> **Orfeus said:**
> i tried it but it says something about negative vibes...

Yeah, this happened to me for a long time as well. It happens because Thunderbird tries to download the whole inbox and times out (the default timeout is 60 seconds I think). You could try to change the default timeout to longer, depending on your connection. However, what I did was goto Account Settings and select "Fetch headers only". This was just to build an initial cache of my old email (most of which I don't really need). After it downloaded my inbox, I unchecked the box.

---

