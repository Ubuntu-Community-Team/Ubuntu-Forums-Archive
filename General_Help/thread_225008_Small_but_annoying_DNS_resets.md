---
title: "Small but annoying DNS resets"
date: 2006-07-28
forum: General Help
---

### Post by Rhemat on 2006-07-28
Heya

  Just want to state, that this problem is not important, but, if I can get info on fixing, that'd be peachy.
  My DNS settings in the network admin application keep reseting anywhere from 30 minutes to 1 hour of network inactivity.
  I have managed to memorize the proper DNS urls/sites/?, and it only takes a minute, but this seems unnecessary, and I never had to reset it at my last place.
  Hopefully, when I upgrade to 6.06, this and a few other bugs I noticed will go away.
  Thank you for your time.

-Brad

---

### Post by diepruis on 2006-07-29
You could try this fix:

First, set your DNS to the desired values, then:

```

cd /etc
sudo chattr +i resolv.conf

```

This will make the config file for the DNS settings immutable (it cannot be changed). If you want to change your settings you will have to do the following:

```

cd /etc
sudo chattr -i resolv.conf

```

Hope this solves the problem, it can be **really** annoying.

---

### Post by ponderazz on 2006-08-23
Linux newbie here...
I've been having exactly the same problem. The DNS setting periodically resets itself every time I log in, and even while I'm busy surfing the 'net.

I'm trying out this fix on Dapper Drake, June release, and it seems to be working for the moment :D 

I'd also like to note that Drake Dapper's network tool asks for the admin password only ONCE after I log in, but not for any subsequent changes that I make to the network setting... :idea:

---

### Post by diepruis on 2006-08-24
> **ponderazz said:**
> Linux newbie here...
I've been having exactly the same problem. The DNS setting periodically resets itself every time I log in, and even while I'm busy surfing the 'net.

I'm trying out this fix on Dapper Drake, June release, and it seems to be working for the moment :D 

Good, let me know how it pans out, k?

> **ponderazz said:**
>  I'd also like to note that Drake Dapper's network tool asks for the admin password only ONCE after I log in, but not for any subsequent changes that I make to the network setting... :idea:

Ubuntu only asks you for your password if you haven't taken any actions as root for 15 minutes (I think). It could also be that it asks every 15 minutes, eh, you get the picture.

---

### Post by HolyJoe on 2006-08-30
very nice!

thank you.

---

### Post by kopilo on 2006-09-01
Thank you very much! Thus far it seems to be working very well. [img]http://ubuntuforums.org/images/smilies/eusa_clap.gif[/img]

---

### Post by Lunchmeat on 2006-09-04
I had the same problem... Setting my router to not reasign dns servers automatically when the dhcp server renewed itself solved it nicely too.

---

### Post by Fraoch on 2006-09-06
Hmm, I'm having the same issue, but when I type

```
sudo chattr +i resolv.conf
```

I get

```
chattr: Inappropriate ioctl for device while reading flags in resolv.conf
```

Any advice?  Thanks.

---

### Post by yarox on 2007-03-10
First, edit **resolv.conf** and set your DNS to the desired values  and then, you have to modify **/etc/dhcp3/dhclient.conf**, look for the section that begins with **request** and eliminate the **domain-name-servers** option. This make that you won't send a DNS request, so your resolv.conf will keep intact.

Sorry for my crappy english :)

---

### Post by strabes on 2007-03-10
This problem seems to be fixed in feisty.

---

### Post by Fraoch on 2007-04-08
> **yarox said:**
> First, edit **resolv.conf** and set your DNS to the desired values  and then, you have to modify **/etc/dhcp3/dhclient.conf**, look for the section that begins with **request** and eliminate the **domain-name-servers** option. This make that you won't send a DNS request, so your resolv.conf will keep intact.

Sorry for my crappy english :)

Still doesn't work for me.:(

---

### Post by Fraoch on 2007-05-18
BTW this issue went away with Feisty!  Yay!:)

---

