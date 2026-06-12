---
title: "Adding GNUMP3d to Web Page"
date: 2007-08-18
forum: General Help
---

### Post by cjk422 on 2007-08-18
Hi all,

I have Apache2 web server running on Ubuntu 7.04. I also have GNUMP3d, and I'd like to be able to run it from a subdirectory of my web page, i.e. [http://my-domain/music](http://my-domain/music) will load the GNUMP3d player. I've already set gnump to use port 80, but beyond that I'm clueless. I've spent hours searching and trying to find a solution. Can anyone help me?

Thanks,
Chris

---

### Post by freeflyer57 on 2007-08-18
Do you have a router? If so, change the port to something like 8888, then use the router to foward anybody, who connects to your network through port 8888 to your computer. GNUMP3d should then take over and give the correct file.  Hope that help. If port fowarding is not the problem. Then make sure everything you need is uncommented in GNUMP3d configure log. And that you are allowing people to get in. Check your firewall to make sure that you are not using an auto-blacklist setting.

---

### Post by cjk422 on 2007-08-18
I can get it to work over port 8888, but the problem is you have to connect (from the outside) to *[http://my-domain:8888](http://my-domain:8888)*. I want to set it so if you point your browser to *[http://my-domain/music](http://my-domain/music)* it will load the player. Is this at all possible? Or is this a limitation of the particular software?

I assume this will take some coding, either in index.html or through some sort of alias redirection.

Thanks,
Chris

---

### Post by freeflyer57 on 2007-08-18
I think it may be a limitation, but I never had a Name service. I gave my friends my ip and port number, when i had GNUMP3d. In your website, could you make a link for music that points to mydomain:8888

---

### Post by cjk422 on 2007-08-18
> **freeflyer57 said:**
> I think it may be a limitation, but I never had a Name service. I gave my friends my ip and port number, when i had GNUMP3d.

Name service ... could a DNS entry forward the URL [http://my-domain/music](http://my-domain/music) to [http://ip-address:8888?](http://ip-address:8888?)

That could work ... theoretically ...

---

