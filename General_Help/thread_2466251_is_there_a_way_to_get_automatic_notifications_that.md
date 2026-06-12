---
title: "is there a way to get automatic notifications that tells the user if there is no inte"
date: 2021-08-24
forum: General Help
---

### Post by ardouronerous on 2021-08-24
**is there a way to get automatic notifications that tells the user if there is no internet connection?**

I'm running Xubuntu 20.04.

Is there a way to get automatic notifications that tells the user if there is no internet connection? Something like this: 

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289036&stc=1[/IMG]

In  my country, we get frequent Internet disconnections and I would like   to know if and when the connection drops. Is there an something that  could do this?

The reason why I  want something like this is because yesterday, when I was online  chatting with a friend and I was also playing a game, I was unaware my  connection dropped and my friend sent me a message and I never got any  notifications that my friend sent me a message due to the connection  being lost. I only found out my connection dropped 30 minutes into my  game.

---

### Post by dragonfly41 on 2021-08-24
Can you not create a cronjob which pings at intervals to test internet connection while you are in a session?

---

### Post by The Cog on 2021-08-24
A crontab entry like this maybe?
```
* * * * * ping -c3 1.1.1.1 || zenity --warning --text "Internet gone wobbly again!"
```

---

### Post by Impavidus on 2021-08-24
I've had such notifications for ages. Now digging into it, it appears that nm-applet is responsible for those notifications on Xubuntu (running 21.04 myself). Maybe that has something to do with running the indicator applet in the xfce panel? IDK. But that would only notify when the connection with the router breaks/is established. Monitoring the connection from there to the internet is a different matter.

---

### Post by ardouronerous on 2021-08-24
> **Impavidus said:**
> I've had such notifications for ages. Now digging into it, it appears that nm-applet is responsible for those notifications on Xubuntu (running 21.04 myself). Maybe that has something to do with running the indicator applet in the xfce panel? IDK. But that would only notify when the connection with the router breaks/is established. Monitoring the connection from there to the internet is a different matter.

The problem with that is that the router doesn't show any problems though when the connection drops, it still has all it's green lights on, so it doesn't show any problems in the network applet, but when I try to browse, it says "Server not found," so the solution as put forward by my ISP is to close/open the router, but I never get notifications of when the connection drops, I have to discover it for myself.

> **dragonfly41 said:**
> Can you not create a cronjob which pings at intervals to test internet connection while you are in a session?

I don't know how to do a cronjob though.

> **The Cog said:**
> A crontab entry like this maybe?
```
* * * * * ping -c3 1.1.1.1 || zenity --warning --text "Internet gone wobbly again!"
```

I don't know how to do a cronjob. I heard it requires root permission to do cronjobs. Is there a way to do a cronjob but in my Home folder instead?

---

