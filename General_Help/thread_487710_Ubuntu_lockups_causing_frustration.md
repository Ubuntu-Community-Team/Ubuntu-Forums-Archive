---
title: "Ubuntu lockups causing frustration"
date: 2007-06-29
forum: General Help
---

### Post by Keisad on 2007-06-29
AGH!

So, I have installed Ubuntu on my computer. I like it, the only downside is that it freezes about every ten-fifteen minutes. 

This is REALLY aggravating. 

I can tell when it is soon to freeze. Before it does, no visual activity on the computer can process unless my mouse is moving. If I minimize a window, it will not minimize until I keep the mouse moving long enough to let it do so.

I have looked at my var/log/syslog and it seems that everytime I freeze, this

NetworkManager: <information>^Iwpa_supplicant(5517):

has something to say. Everytime it freezes, it was making the last logged activity. 

Help?

---

### Post by loserboy on 2007-06-29
I don't know whats wrong but since nobody helped yet.... try disconnecting from your network and see if it still freezes

---

### Post by MCSE_Crossover on 2007-06-29
My computer used to freeze too when I tried using wireless security. Try disabling wireless security for the time being and uninstall the WPAsupplicant package. See if this resolves your problem. What type of wireless card are you using? Is it natively supported or do you have to use ndiswrapper to get it to work?

---

### Post by Keisad on 2007-06-29
Thanks for the replies, I will try doing both and post back when I've experimented long enough.

---

