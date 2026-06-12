---
title: "SSH Socks web browsing proxy for remote users"
date: 2017-03-01
forum: General Help
---

### Post by getut on 2017-03-01
I need some help setting up a socks web browsing proxy for remote windows users. I have found TONS of tutorials about doing an SSH Socks proxy for web browsing and it took me way too much time to figure out that the commands in all the tutorials I have found were meant to be run on the REMOTE side and most of the tutorials show connecting to a ssh daemon on the local device.

As of yet I have not found the magic command to keep a permanently running ssh socks proxy on a tiny headless server for my users to connect to from roaming windows stations. I want the ssh socks proxy to stay running all the time on port 80 so that those remote users only have to have their browser configured correctly and port 80 is allowed out from just about anywhere they would be. Stated slightly differently, I don't want them to have to issue any ssh or putty commands on their machines to use this.

Any help is greatly appreciated.

---

### Post by getut on 2017-03-01
Bump.

---

### Post by dragonfly41 on 2017-03-02
I am non too experienced in SSH socks myself. 
 But having recently setup a remote server in the cloud I've been researching ways of SSH tunneling to remote admin resources such as webmin, instead of keeping a remote server port open.

This led me to investigate ngrok.com

[https://ngrok.com/product](https://ngrok.com/product)


Read their documents and search for case profiles such as here ...

[http://mymizan.rocks/2016/11/18/http-and-ssh-tunneling/](http://mymizan.rocks/2016/11/18/http-and-ssh-tunneling/)

This might fit your needs.

---

