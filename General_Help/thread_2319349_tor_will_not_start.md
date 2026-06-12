---
title: "tor will not start"
date: 2016-04-03
forum: General Help
---

### Post by Hotchilli on 2016-04-03
I am installing tor via apt-get seems I need to confiure something ?

 ~ $ sudo tor
Apr 03 15:36:51.839 [notice] Tor v0.2.4.27 (git-412e3f7dc9c6c01a) running on Linux with Libevent 2.0.21-stable and OpenSSL 1.0.1f.
Apr 03 15:36:51.839 [notice] Tor can't help you if you use it wrong! Learn how to be safe at [https://www.torproject.org/download/download#warning](https://www.torproject.org/download/download#warning)
Apr 03 15:36:51.839 [notice] Read configuration file "/etc/tor/torrc".
Apr 03 15:36:51.843 [notice] Opening Socks listener on 127.0.0.1:9050
Apr 03 15:36:51.843 [warn] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
Apr 03 15:36:51.843 [warn] Failed to parse/validate config: Failed to bind one of the listener ports.
Apr 03 15:36:51.843 [err] Reading config failed--see warnings above.

---

### Post by oldos2er on 2016-04-03
Don't run it with sudo?

---

### Post by Hotchilli on 2016-04-04
same output without sudo

---

### Post by X-RED_Tech on 2016-04-04
You can use TOR browser in a self-contained folder and that is the preferred method. 
[https://www.torproject.org/projects/torbrowser.html.en](https://www.torproject.org/projects/torbrowser.html.en)
Download and extract wherever you like. Open the folder and double click start Tor browser.

---

### Post by QDR06VV9 on 2016-04-04
Yes Tor Browser is the preferred method...But if you need more control.
Your error from your first post
> Apr 03 15:36:51.843 [warn] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
to fix enter this in the terminal
```
sudo killall tor
```
Then you can now start Tor after configuring your network to use a Proxy
```
tor
```

For a nicer(Easier) way to control Tor
SelekTOR is an open source Java-based GUI front-end for the Tor Client which has a few advantages over Vidalia (the official Tor GUI)

[https://www.dazzleships.net/selektor-for-linux/](https://www.dazzleships.net/selektor-for-linux/)

[http://www.webupd8.org/2014/09/selektor-tor-gui-with-country-exit-node.html](http://www.webupd8.org/2014/09/selektor-tor-gui-with-country-exit-node.html)

---

