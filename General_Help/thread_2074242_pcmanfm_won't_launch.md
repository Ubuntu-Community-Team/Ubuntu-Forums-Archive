---
title: "pcmanfm won't launch"
date: 2012-10-21
forum: General Help
---

### Post by singedwings on 2012-10-21
I am probably not the first person with this problem, I have hunted around for a solution but had no luck finding an answer. I am using lubuntu 12.10 fully updated.

pcmanfm will not launch from the shortcut in the menu.```
pcmanfm %U
```entered in a terminal also does nothing.```
pcmanfm /home/username
```works. All help greatly appreciated.

---

### Post by Rex Bouwense on 2012-10-21
Can you launch it using:
  ```
 pcmanfm --desktop --profile=LXDE
```

---

### Post by singedwings on 2012-10-22
No that does nothing either.

---

### Post by vasa1 on 2012-10-22
> **singedwings said:**
> I am probably not the first person with this problem, I have hunted around for a solution but had no luck finding an answer. I am using lubuntu 12.10 fully updated.

pcmanfm will not launch from the shortcut in the menu.```
pcmanfm %U
```entered in a terminal also does nothing.```
pcmanfm /home/username
```works. All help greatly appreciated.

I haven't seen other reports of such problems but you could try asking here: [https://lists.ubuntu.com/archives/lubuntu-users/](https://lists.ubuntu.com/archives/lubuntu-users/)

Also, where do you see
```
pcmanfm %U ?
```Most of the pcmanfm entries I have are plain "pcmanfm" and somewhere I came across "pcmanfm %s", IIRC.

BTW, is yours an upgrade from 12.04 or a clean install (though it shouldn't theoretically make any difference)?

---

### Post by singedwings on 2012-10-22
I got 'pcmanfm %U' from both the command in the properties of its menu shortcut and from scanning this post [http://www.pclinuxos.com/forum/index.php?topic=108963.0]("http://www.pclinuxos.com/forum/index.php?topic=108963.0")

'pcmanfm %s' returns 'no such file or directory'

I have 4 computers displaying this problem. 3 are Acer Revos, 2 were upgraded and 1 was a fresh install. Lastly I have an Acer Aspire laptop that was a fresh install.

---

### Post by Qaddosh on 2012-10-25
I have been experiencing the same problem. I upgraded from Lubuntu 12.04 to 12.10 and now a simple 'pcmanfm' does not work and neither does 'pcmanfm %U', or 'pcmanfm %s'. I had to change my pcmanfm shortcuts to specify my home directory as in 'pcmanfm /home/username'. It did not seem to start doing it immediately after upgrading, but sometime later in the same day. It's possible that I simply did not notice it until later.

---

### Post by vasa1 on 2012-10-25
> **Qaddosh said:**
> I have been experiencing the same problem. I upgraded from Lubuntu 12.04 to 12.10 and now a simple 'pcmanfm' does not work and neither does 'pcmanfm %U', or 'pcmanfm %s'...
Are you entering "pcmanfm" in a terminal? I think that is different from OP's question.

---

### Post by Qaddosh on 2012-10-26
It happens whether it is launched from a shortcut that provides a simple 'pcmanfm %U' which is what the shortcut originally was, however, to workaround this issue, I've had to change the shortcut to 'pcmanfm /home/username'. I am experiencing the same issue as the OP.

---

### Post by singedwings on 2012-11-13
Sorry all I totally forgot about this post. I have solved this problem (Lubuntu Users did not respond with any suggestions). To fix enable this ppa ```
ppa:lubuntu-dev/lubuntu-daily
```The updates fix whatever the problem was:P

---

### Post by vasa1 on 2012-11-13
> **singedwings said:**
> Sorry all I totally forgot about this post. I have solved this problem (Lubuntu Users did not respond with any suggestions). To fix enable this ppa ```
ppa:lubuntu-dev/lubuntu-daily
```The updates fix whatever the problem was:P

Why did you decide to install that ppa? What was the thinking behind the decision?

---

### Post by Guilden_NL on 2012-11-16
Same problem for all of my systems.

Actually, this isn't solved, you just found a work around.

I'd like to know why this is happening and why it wasn't reported in beta testing.

---

### Post by singedwings on 2012-11-16
Well the main reason that I tried this one was that I noticed an upstream release of pcmanfm and hoped that the problem was ironed out in it. 

In my experience quite a lot of problems get fixed just by the fact that there are updates. Standard Ubuntu repositories can lag a bit behind releases, especially projects with lots of activity. Be aware that there is an element of risk involved with this as the standard repositories will probably be more stable!

Sorry Vasa1 just noticed your number of posts, I am not trying to teach you how to suck eggs. :)

---

### Post by singedwings on 2012-11-16
Guilden_NL would you explain your reasoning for 'this isn't solved, you just found a work around'.

Whilst I had been using```
pcmanfm/home/username
```to launch pcmanfm from the terminal whilst I had this problem. I did not change any of my shortcuts. 

Surely that means that the only way the problem was fixed was by the change to a newer version? There is of course a chance that something else was causing the problem originally and the updates of it solved the issue. The problem was definately fixed by adding the ppa. I did no other thing at the same time and checked the issue was still there before updating.

---

### Post by vasa1 on 2012-11-16
> **singedwings said:**
> ...
Surely that means that the only way the problem was fixed was by the change to a newer version? ...
It's a pity you didn't get a response via the mailing list. I think that was an aberration. I've seen most posts there get answers. Even the dev of the file manager responds.
Why don't you give the list one more chance and post your solution there?

---

### Post by temporos on 2013-05-08
> **singedwings said:**
> To fix enable this ppa ```
ppa:lubuntu-dev/lubuntu-daily
```The updates fix whatever the problem was:P
Am I correct in assuming that I can install this PPA by executing the following?
```
sudo add-apt-repository ppa:lubuntu-dev/lubuntu-daily
```
Also, how safe is this PPA? PPAs are personal archives, aren't they? So, they aren't official, moderated, monitored, or updated regularly. Once I add the repository, is pcmanfm updated automatically, or do I need to link it somehow?

---

### Post by singedwings on 2013-05-28
The ppa repositories vary in their update frequency and quality depending on the work of the assembler and the status/stability of the packages provided. Generally the further upstream the ppa is based on the more unstable it is likely to be. But the ppa listings are the easiest way to get access to the latest features/fixes that may not drop into the main repos for sometime if at all. I have always been a tinkerer and come from many years playing games on windows, where using betas has generally been benifical. I use plenty off ppa's. Watch out for ones that do not play well with each other, say if they have similar packages! 

Yes you have the correct line to add the ppa. All you need to do then is```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade
```

---

