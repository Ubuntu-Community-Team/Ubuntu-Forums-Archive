---
title: "linking to a webserver from a webserver? Confusing!"
date: 2008-02-09
forum: General Help
---

### Post by phillips321 on 2008-02-09
Hi guys,

At home i have a web server running fine (192.168.1.119). I also have another box used purely for torrenting (192.168.1.122), this torrent box runs a web interface.

From inside my network i can access both of the boxes, but from outside the network i can only route port 80 traffic to one internal ip, i have to choose the webserver on 192.168.1.119.

From outside the network i would also like to be able to view the torrent web interface but i only have one external ip. I dont mind how i access the torrent web interface other than i need it running on port80. (I know i could just choose port 8080 and route that port to 192.168.1.122 but i'd much rather use something like torrent.example.com).

How do i go about doing this? Any ideas?

Cheers guys.

P.s. What about creating a site on the web server (192.168.1.119) and pointing then to 192.168.1.122 but hiding this from someone outside of the LAN?

---

### Post by SpaceTeddy on 2008-02-09
i am not quite sure i understand what you are tryint to say, but as far as i do understand it would see two different ways of doing this...

**Idea A** is redirecting a different port as you suggested it so that an external request on port  8080 get redirected to the torrent machine while all external requests to port 80 go to the webserver. Doing this with subdomains it afaik not possible with packet manipulation.

**Idea B** is setting up the web server to redirect a certain folders or hostnames to the torrent machine. This can be done via apache's mod_proxy. Documentation can be found at [http://httpd.apache.org/docs/1.3/mod/mod_proxy.html ]("http://httpd.apache.org/docs/1.3/mod/mod_proxy.html"). This way you can setup a different hostname for the torrent machine while not doing a second port redirect. But this also means that loading the torrent interface will put stress on both internal server - not just one.

hope this helps

---

### Post by phillips321 on 2008-02-09
Cool option B looks like what i need.

thanks for that

Guess i'll do some research then come back if i get stuck.

Many thanks :)

---

