---
title: "Need help making web apps work on LAN like WAN"
date: 2007-01-02
forum: General Help
---

### Post by pjbgravely on 2007-01-02
Here is the situation.

    I have a chat program installed on a Ubuntu server on the same LAN as my desktop. I have used no-ip to provide a URL to point WAN users to my server. When I try to use the chat program on my desktop some things like the pictures and logout call to the no-ip URL and they don't work.

Is there any way I can set a url to resolve to an IP address I set, instead of the one on my ISP's DNS? I thought there was a way to set real URL's to resolve to /dev/null. Maybe I'm wrong.

    For example, The WAN users have the URL [http://.edmund.no-ip.com/chat](http://.edmund.no-ip.com/chat), which directs them to my Internet IP on port 800. Because I am on the same LAN as the server, if I use that URL, I get redirected to my server, but then  the answer gets lost as it leaves my IP headed to my IP.

    I can access my server by using [http://edmund:800/chat](http://edmund:800/chat) where edmund's IP is defined in /etc/hosts, but run into trouble when parts of the chat use the absolute address [http://edmund.no-ip.com](http://edmund.no-ip.com) which doesn't resolve. 

If edmund.no-ip.com wasn't a real address then I could simply put it into my /etc/hosts file. I tried installing bind on the server and defining that to the local IP of my server but I cannot seem to flush the DNS cache to even test it. It still resolves to the real  no-ip.com IP, and then back to mine. I'm not sure this will even work.

  Paul

---

### Post by jpkotta on 2007-01-02
Edit: Hasty post.

---

### Post by pjbgravely on 2007-01-07
I figured it out.

I wasn't thinking that I couldn't add the port redirect to /etc/hosts. The fix was to add port 80 to the servers apache, and add the url to hosts, pointing to the server's IP. I realize I'm lost when it comes to bind so I better learn that next.

Paul

---

