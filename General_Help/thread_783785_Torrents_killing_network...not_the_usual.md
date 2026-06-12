---
title: "Torrents killing network...not the usual"
date: 2008-05-06
forum: General Help
---

### Post by Anduu on 2008-05-06
Not sure if this is Deluge(0.9.5.0) related but this is where I run into my little problem.

When downloading a torrent everything goes along smoothly at first.I can surf fine etc.After a while my network connection drops and reconnects and continues to do so every few minutes as long as the torrent is downloading.

It has only started doing this recently(ie the last few days...)

Anyone else notice this happening?

---

### Post by retrow on 2008-05-06
I found no such problems with *Transmission*.
When the upload speeds are close to your peak upload speed, it takes longer to open new pages, but apart from that everything works just fine.

---

### Post by agim on 2008-05-06
It could very likely be that your ISP is choking you off because you are using P2P. This is something that has become a bigger and bigger problem. I think there is actually some litigation now with some of the ISPs. If you use torrent, make sure you use random ports. Most p2ps are used through ports 6881 to 6889. Go to preferences->network and it will give you the random port option.

---

### Post by jw5801 on 2008-05-06
> **Anduu said:**
> Not sure if this is Deluge(0.9.5.0) related but this is where I run into my little problem.

When downloading a torrent everything goes along smoothly at first.I can surf fine etc.After a while my network connection drops and reconnects and continues to do so every few minutes as long as the torrent is downloading.

It has only started doing this recently(ie the last few days...)

Anyone else notice this happening?

I had similar issues with Deluge, I honestly have no idea why, and my attempts at diagnosis failed miserably! Transmission & kTorrent both work fine for me.

Contrary to popular belief P2P is not illegal so your ISP should not be choking you for using bittorrent. The bittorrent protocol itself is perfectly legal, most distros nowadays offer to distribute their .iso's using it! The misconception is purely due to the fact that most people use it to distribute things that copyright doesn't entitle them to.

---

### Post by agim on 2008-05-06
Yeah, I know its not illegal.
Here is a link about comcast choking off p2p users. They are not the only ones.

[http://www.washingtonpost.com/wp-dyn/content/article/2008/02/12/AR2008021202778.html?hpid=moreheadlines](http://www.washingtonpost.com/wp-dyn/content/article/2008/02/12/AR2008021202778.html?hpid=moreheadlines)

There are thousands of similar stories on the web.

and another:
[http://www.computerworld.com.au/index.php/id;1740976740](http://www.computerworld.com.au/index.php/id;1740976740)

---

### Post by jw5801 on 2008-05-06
> **agim said:**
> Yeah, I know its not illegal.
Here is a link about comcast choking off p2p users. They are not the only ones.

[http://www.washingtonpost.com/wp-dyn/content/article/2008/02/12/AR2008021202778.html?hpid=moreheadlines](http://www.washingtonpost.com/wp-dyn/content/article/2008/02/12/AR2008021202778.html?hpid=moreheadlines)

There are thousands of similar stories on the web.

and another:
[http://www.computerworld.com.au/index.php/id;1740976740](http://www.computerworld.com.au/index.php/id;1740976740)

You'll also note that it wound up with a senate inquiry ;)

I have a funny feeling that ISPs do things like that to come off looking good in the eyes of the ignorant, whilst reducing their traffic and thus costs. I am in a rather cynical mood today though... :p

---

### Post by agim on 2008-05-06
Yes, I did notice the senate inquiry. I also notice that it is going on. I don't understand what you're getting at? It is happening, thats just the way it is. And its not just Comcast. This is a rather important issue involving net neutrality. Making pretend it doesn't happen or that its rare... burying our head in the sand isn't going to make it go away.
I'm surprised. This has been discussed on this forum before, I thought someone with your bean count would be more aware of this. The matter has gone all the way to the FCC, if you google it, you can find that Verizon has tried to ban P2P (in fact, the p2p ban has been in their users contracts).

---

### Post by jw5801 on 2008-05-06
> **agim said:**
> Yes, I did notice the senate inquiry. I also notice that it is going on. I don't understand what you're getting at? It is happening, thats just the way it is. And its not just Comcast. This is a rather important issue involving net neutrality. Making pretend it doesn't happen or that its rare... burying our head in the sand isn't going to make it go away.
I'm surprised. This has been discussed on this forum before, I thought someone with your bean count would be more aware of this. The matter has gone all the way to the FCC, if you google it, you can find that Verizon has tried to ban P2P (in fact, the p2p ban has been in their users contracts).

Sorry, I don't mean to come across as though I'm not aware of it, I know it happens (thankfully not as much in Australia, although our ISPs are terrible regardless), I guess I'm suggesting that it's up in the air at the moment and I'm confident that we should come down on the right side of the fence. If not I'll move to Sweden!

The main thing I was suggesting was that the reason companies attempt this kind of thing has nothing to do with any 'noble cause' as the media often suggests. They don't do it to 'stamp out illegal file sharing,' they do it to reduce the strain on their network so they pay less to the backbone providers they rent the bandwidth from.

---

### Post by Ameneon on 2008-05-06
While I noticed this turning more into a focus on ISP rather than Ubuntu/Deluge I thought I'd add my 2c at least to the technical side of things; using 8.04 and Deluge 0.5.8.9 and have no problems at all, on the contrary I can maximize my 30mb connection both up and down just fine, so if there's a tech problem contributing to this it's at least not prevalent in all configurations..

---

### Post by Archmage on 2008-05-06
Try to reduce your connections in the torrent-client. This sounds to me like your router can't handel that many connections and is resting itself.

Today only a limited number of router can handle more than 100 connections.

---

### Post by Anduu on 2008-05-06
> **Archmage said:**
> Try to reduce your connections in the torrent-client. This sounds to me like your router can't handel that many connections and is resting itself.

Today only a limited number of router can handle more than 100 connections.

Yep it's my router.

I have it tucked away and didn't even think to check what its doing.I'm not sure why it is doing this all of a sudden...it's only a couple months old.

In the process of troubleshooting now...we'll see what happens.

Thanks for all the input guys :)

---

