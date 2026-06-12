---
title: "Torrent download speed"
date: 2007-03-10
forum: General Help
---

### Post by rafaelperrone on 2007-03-10
I'm having some trouble with torrent downloads with Ubuntu Edgy. I have already tried it with Azureus and Bittorrent and both give me download speeds around 10KB/s while I usually get 90KB/s under WinXP. I have already configured my dlink router and opened the necessary ports in it (Im sure this is not the problem because I have green faces all the time with Azureus).

So I tried running utorrent using Wine and used the same port I was using with Azureus and I got downloads at about 90 KB/s again. I believe the problem is some other config in Azureus (and not the ports). I checked the max number of connections in utorrent and I used the same number in Azureus, but this didnt solve my problem.

Is there any other thing you think my be the problem? Is there any other config I should check under Azureus?

Thanks in advance.

---

### Post by Jmccaffrey on 2007-03-10
If you have an nvidia network card, than that could be the problem.  There are issues with the "free" driver forcedeth on that card.  If you do have that card, try using the nvnet drivers provided by nvidia.

Also uTorrent is often considered a tainted client and probably should not be used if you are using bittorrent to aquire files that you may not retain the proper liscensing for.  There are some more "minimal" clients out there that you may try, like BitTornado.

---

### Post by dpar on 2007-03-10
I have found that Edgy has iptables activated by default. If I configure iptables to allow Azureus, I get much better download speeds.

---

### Post by rafaelperrone on 2007-03-10
> **dpar said:**
> I have found that Edgy has iptables activated by default. If I configure iptables to allow Azureus, I get much better download speeds.

how do you do that? have no idea what iptables are and how to configure them.

---

### Post by dpar on 2007-03-11
iptables is a firewall. Download Firestarter from Synaptic. It is the Gui frontend for iptables.I'm off to bed right now but I'll be back tomorrow if I can help you any more.:)

---

### Post by Hallvor on 2007-03-11
Almost certainly a firewall issue. I`m getting wild download speeds under Ubuntu on bittorrent. Much faster than under Windows for some reason. Recently upgraded my connection and my record now is some 1100 kb/s! :) But before I opened the port with Firestarter, it was very slow.

---

### Post by dpar on 2007-03-11
Baaack!  Anyway, once you download Firestarter, Start up Azureus. Then start Firestarter (it's in System>Administration). Click on the 'Events' tab in firestarter and you should see a bunch of blocked events on port 59243. Right click on one of those events and a menu will pop up. Click on "allow for everyone'.
That should be it. You can close Firestarter if you want and you should now have better connection speeds with Azureus.:) :)


P.S.- I did this with all my download clients.....Frostwire,ktorrent,Deluge,etc.

---

### Post by Detonate on 2007-03-11
Hey Dpar, when I installed Azureus, it defaulted to port 49928.  When I test this port from the tools menu in Azureus, it returns "...NAT error".  I ran Firestarter and right clicked on the entry in Events and told it to allow everyone, but it still returns "...NAT Error" when I test it.  Am I doing something wrong?  I too, am having very slow downloads with torrents.

---

### Post by Detonate on 2007-03-11
Never mind, I figured it out, I had to open the port in both my router and in the DSL modem.

---

### Post by Ek0nomik on 2007-03-11
> **Jmccaffrey said:**
> If you have an nvidia network card, than that could be the problem.  There are issues with the "free" driver forcedeth on that card.  If you do have that card, try using the nvnet drivers provided by nvidia.

Also uTorrent is often considered a tainted client and probably should not be used if you are using bittorrent to aquire files that you may not retain the proper liscensing for.  There are some more "minimal" clients out there that you may try, like BitTornado.

How is it considered a tainted client?

---

### Post by fearpi on 2007-03-11
> **Ek0nomik said:**
> How is it considered a tainted client?

I'm also confused about this.

---

### Post by rafaelperrone on 2007-03-11
> **dpar said:**
> Baaack!  Anyway, once you download Firestarter, Start up Azureus. Then start Firestarter (it's in System>Administration). Click on the 'Events' tab in firestarter and you should see a bunch of blocked events on port 59243. Right click on one of those events and a menu will pop up. Click on "allow for everyone'.
That should be it. You can close Firestarter if you want and you should now have better connection speeds with Azureus.:) :)


P.S.- I did this with all my download clients.....Frostwire,ktorrent,Deluge,etc.

Did exactly what you said, but I still have bad or no download at all.
Posting some screenshots of both Azureus and Firestarter. Im using port 35035.

When I check the Peers tab at the torrent details on Azureus, i see lots of "Waiting for handshake" connections and just a few "Fully established". Maybe its something to do with that.

What else should I try?

---

### Post by ffxr on 2007-03-11
i followed these guides & improved my torrent speed markedly... i use ktorrent

[http://torrentfreak.com/speed-up-your-torrents-ii/](http://torrentfreak.com/speed-up-your-torrents-ii/)
[http://btfaq.com/serve/cache/25.html](http://btfaq.com/serve/cache/25.html)


i didnt need to touch iptables or firestarter, just fwded a few ports on my router.. they might give you a few ideas. : )

---

