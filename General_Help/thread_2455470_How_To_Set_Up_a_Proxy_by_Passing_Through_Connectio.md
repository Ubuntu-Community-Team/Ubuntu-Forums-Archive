---
title: "How To Set Up a Proxy by Passing Through Connection Through ssh to Server"
date: 2020-12-20
forum: General Help
---

### Post by theaudacitor on 2020-12-20
Hello and thanks for taking a look.

I want to set up a proxy to have my torrent client and browser connect through it. I don't want to use squid on ubuntu server since it does http proxy protocol and all network from torrent client or browser to there is unencrypted. Even if I can make https work, I don't want to leave something open for 27/4 with plain text authentication or none at all.

I have heard of connecting to the server through ssh and then open a local port to pass all connection through it to the ssh connection:

```ssh-keygen -t ed25519```
```ssh-copy-id user@vpsserver```
```ssh user@vpsserver -D 5050 -n```

Then I can set up `127.0.0.1` on port `5050`. That way my connection should be passed from that port to the ssh, therefore acting like a proxy. My question is, which proxy protocol should I choose when per say I am configuring it in qbittorrent? (Image of setting page below)

[https://i.stack.imgur.com/FS4jk.png](https://i.stack.imgur.com/FS4jk.png)

Should I choose socks5 or 4 for proxy protocol(or how)? As far as I know it, it should be socks5 but I have no reason as to why it is. Would appreciate if someone can explain how this pass through works and how the protocol is applied.

Lastly, if you have a better way please reply below, open to all ideas. Wish you all a nice day!

---

### Post by TheFu on 2020-12-20
27/4?  That must be a different planet. ;)  Where do you really live? Hope the lag time for messages to Earth isn't too bad.

I don't know anything about qbittorrent, but doesn't it use thousands of different ports?  I don't see how you can proxy that without a full VPN and full routing. I suppose some paid VPN services also do some sort of weenie proxy service. Don't know anything about that, sorry.

ssh-keygen and ssh-copy-id are 1-time commands.  Only needed when you want new ssh-keys or have a different remote system to connect into (ssh-copy-id).  ssh-copy-id is a convenience tool. You can manually do what it does, if you prefer.  Over the decades, people have screwed that manual process up so often that a tool was created.

I don't know the answers to the other questions either.  I use an ssh socks5 proxy when traveling to access web-apps on my home network when straight ssh or x2go or openvpn aren't the better choice.  Just depends on the need.

---

