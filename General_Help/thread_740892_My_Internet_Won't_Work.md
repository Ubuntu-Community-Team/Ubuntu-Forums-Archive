---
title: "My Internet Won't Work"
date: 2008-03-31
forum: General Help
---

### Post by CD27 on 2008-03-31
I just got my new laptop (Windows) and configured the internet for it. After I did that, and i try to swap the cable (i can't get my wireless router to work so i can use it as a switch), the internet simply WILL NOT WORK at all on my ubuntu laptop. But when i swap it back over, it works fine on windows. What happened? :(

---

### Post by process91 on 2008-03-31
I'll need more information. For starters, post the result of the following command:

```
ifconfig -a
```

Also, what does your **/etc/network/interfaces** file look like?

---

### Post by CD27 on 2008-04-05
it won't copy over in any kind of text file, don't know why, never has been able to . and i don't have internet access, so i can't just email it to me. so is there anything specific i need to look for?

---

### Post by dstew on 2008-04-05
> After I did that, and i try to swap the cableI am not sure what you are doing. You have a router with several cable ports, but only one cable, correct? So, you plug your Windows laptop into one port, and it works. But, if you plug your Ubuntu laptop into the same port, with the same cable, it doesn't work, correct? Is that what is happening? If not, please explain more fully.

---

### Post by CD27 on 2008-04-06
No. That's not what's happening. It's not working at all. I have two cables total. One is from the modem to the router, the other is from the router to the laptop (whichever one). The windows laptop has Safe Eyes on it, which prevents me from seting up wireless. The other laptop is my Linux laptop, and when i hook it up, the router simply doesn't work. I tried to go on the net setup and use the ip address 192.168.1.1, but it still didn't do anything.

---

### Post by process91 on 2008-04-06
It seems like it's a networking issue, not an Ubuntu issue. To be sure, if you could plug the windows laptop directly into the router (not using wireless) can you get an internet connection?

---

### Post by dstew on 2008-04-06
> The other laptop is my Linux laptop, and when i hook it up, the router simply doesn't work.You mean, when both laptops are connected to the router, the WIndows laptop cannot get to the internet?

---

### Post by Crafty Kisses on 2008-04-06
> **CD27 said:**
> No. That's not what's happening. It's not working at all. I have two cables total. One is from the modem to the router, the other is from the router to the laptop (whichever one). The windows laptop has Safe Eyes on it, which prevents me from seting up wireless. The other laptop is my Linux laptop, and when i hook it up, the router simply doesn't work. I tried to go on the net setup and use the ip address 192.168.1.1, but it still didn't do anything.

Have you tried doing the following:
```
iwconfig
```
See what that says, I'd like to see the output of that, and also go into Terminal, and see if you're receiving packets from any website, you can do this by going into Terminal and typing:
```
ping website name.com
```

---

