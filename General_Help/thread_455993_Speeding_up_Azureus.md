---
title: "Speeding up Azureus?"
date: 2007-05-27
forum: General Help
---

### Post by God Of Atheism on 2007-05-27
I like the Azureus bittorrent client with regards to features, but don't like how it eats memory and cpu time and after a while stops up- and downloading (this morning I had red smilies for all downloads and blues for all seeds). I do use a non-standard port, which I did open as a listening port following the instructions for iptables somewhere on the Azureus wiki. I tried Deluge as well, but that crashed almost instantly. I had that latter problem with Opera as well sometimes, which lead me to try Azureus in the first place.
So a few questions:
Has anyone tried to compile Azureus? If so, what were the results and how exactly did you compile it?
Is there a way to limit it's memory and cpu usage? (this night I left it running minimized to find java using about 800MB in the morning)
Should I forward ports on my router?I do get connections when I start up Azureus, but most of the time very few (if at all), even for torrents with large amounts of seeds and peers.
Should I use a different java RTE? I'm using Sun Java 6 at the moment.

---

### Post by viciouslime on 2007-05-27
The sun one is best. Also, I don't think it is possible to "compile" azureus as it is java based which is an interpreted language.

Definitely forward ports, very important. Or, you could invest in a more modern router with uPNP, much simpler. If your router already has uPNP support then make sure you turn it on!

Another thing to look at is your upload speed. Try limiting it to about half of your available upload bandwidth and see if that increases your download speed. You can also try setting it to "auto". If you don't do this all your upload bandwidth is taken up by seeding the torrents and there isn't enough to send the necessary info for downloading so you effectivly choke your connection.

---

### Post by God Of Atheism on 2007-05-27
I know java is interpreted, but I also understood there are some compilers for it, like gcj.

I have an ECI B-focus 270PR router, which is a few years old by now, I doubt it has uPNP, but I'll check for details on the internet. As to the forwarding, should I forward all the usual bittorrent ports to the `custom' port, or is a part enough?

I set my upload speed to about 5/6 of my maximum upload speed, that's still more than you recommend, but so far I haven't seen me ever getting close to that, so I cannot yet judge about whether that's too much or not.

---

