---
title: "Killing A Process Using Htop Question"
date: 2014-11-30
forum: General Help
---

### Post by jooge on 2014-11-30
So I just installed htop and did my reading on how it works and I pretty much understand the key points but I have hit a wall on one thing and I hope you guy/gals can help me.

I'm a college student and some sites are blocked here so I use a VPN to fix that problem. So my question is: I have to run the command as root to connect to the VPN and when I'm done just closing the terminal will not kill the process (disconnect me from the VPN service). I ran this in a new terminal:

> kill -9 <PID>

[IMG]http://i59.tinypic.com/2q3x8g7.png[/IMG]

But as you can see nothing happened. I have highlighted the process here so you can see it:

[IMG]http://i61.tinypic.com/2nrhwr8.png[/IMG]

I am able to terminate all other processes other than this one. Am I missing something here?

---

### Post by nerdtron on 2014-11-30
> 
I am able to terminate all other processes other than this one. Am I missing something here?                         

Yes.
Each process is launched by a certain user. This instance is owned/launched by the root user. That means only the root user can kill it.

If you want to kill it, use sudo:
```
sudo kill -9 2904
```

---

### Post by jooge on 2014-11-30
> **nerdtron said:**
> Yes.
Each process is launched by a certain user. This instance is owned/launched by the root user. That means only the root user can kill it.

If you want to kill it, use sudo:
```
sudo kill -9 2904
```

Bingo! Worked like a charm. Thank you my friend.

[[IMG]http://www.sherv.net/cm/emoticons/drink/coffee-machine.gif[/IMG]]("http://www.sherv.net/") [[IMG]http://www.sherv.net/cm/emoticons/eating/bright-breakfast-smiley-emoticon.gif[/IMG]]("http://www.sherv.net/")

---

