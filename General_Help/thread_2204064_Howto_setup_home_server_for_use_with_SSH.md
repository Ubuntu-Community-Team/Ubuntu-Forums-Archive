---
title: "Howto setup home server for use with SSH?"
date: 2014-02-06
forum: General Help
---

### Post by neu5eeCh on 2014-02-06
File this under educating myself and learning new tricks.

I'd like to try setting up a homeserver so that I can proxy and SSH while browsing at public wifi connections. I've been Googling and have some good leads, but I don't have enough knowledge to usefully narrow my search.

I have a little CuBoxi that I could use as a home server (running Oneiric). Once I set up the home server (I was going to use [this guide]("https://www.youtube.com/watch?v=-wUfzdiE4m8") for setting up the home network and [this for SSH]("https://www.youtube.com/watch?v=5mCNO_aL4BA") -- both by nixie pixie). What information should I be searching for next? Once I set up a home network, are there steps involved in using it for SSH? Could I use something like this in lieu of (or in addition to) dropbox?

---

### Post by Lars Noodén on 2014-02-06
If you just need a simple web proxy, you can use SSH as a SOCKS proxy.  Look at the -D option.  

```

ssh -D 5577 server.example.org

```

Then just point your web browser at the SOCKS proxy at port 5577 on the localhost.  

That works with mail too, but IMAPS is encrypted already.

---

### Post by SeijiSensei on 2014-02-06
I would suggest learning how to set up a simple [shared-key OpenVPN tunnel]("http://openvpn.net/static.html").  Then your remote computer will be completely accessible just as if it were on your local network.

You'll need to forward a port on your router back to the server so you can connect from outside.  Just pick a high port at random and tell your router to send all TCP and UDP traffic arriving at that port back to the server.

---

### Post by neu5eeCh on 2014-02-06
Thanks to both of you. I've never done anything like this, do I don't fully understand what you're suggesting, but just enough. I've already googled both your responses and am educating myself.

---

### Post by dragonfly41 on 2014-02-06
If you are willing to try different approaches here is another ... [https://ngrok.com/](https://ngrok.com/)

I've yet to try this out.

---

### Post by neu5eeCh on 2014-02-06
> **dragonfly41 said:**
> If you are willing to try different approaches here is another ... [https://ngrok.com/](https://ngrok.com/)

I've yet to try this out.

Oh wow. This is totally over my head. I love it. I'm definitely going to experiment with it.

---

