---
title: "How to view a website's Retry-After HTTP return code"
date: 2018-10-28
forum: General Help
---

### Post by Paddy Landau on 2018-10-28
I'm unsure on which forum to post this query.

If a website returns HTTP error code 503 (service temporarily unavailable), how I can I see whether or not it has an HTTP "[Retry-After]("https://tools.ietf.org/html/rfc7231#section-7.1.3")" code, and if so, what its value is?

The reason why I'm asking is that I don't know if my web page is correctly returning the Retry-After value.

If I use Chrome or [FONT=lucida console]curl[/FONT] [FONT=lucida console]--head[/FONT], I can see the 503 return code but not the Retry-After code.

---

### Post by Paddy Landau on 2018-10-28
OK. I figured it out. [FONT=lucida console]curl[/FONT] [FONT=lucida console]--head[/FONT] was correct; the website wasn't working properly.

---

### Post by HermanAB on 2018-10-28
BTW, never poke around in the dark.  Run tcpdump or wireshark and LOOK at the packets.  

The answer is in there, Sculley:
$ sudo tcpdump -nlX -i eth0

or more specifically:
$ sudo tcpdump -nlX -i eth0 host 1.2.3.4 and port 80

---

### Post by Paddy Landau on 2018-10-28
> **HermanAB said:**
> BTW, never poke around in the dark. Run tcpdump or wireshark and LOOK at the packets…
Sorry, I really don't understand how this relates to the question.

When I run *curl --head [website]*, I get the following output.

*Because of a bug in the forums, I can't post the output. But it includes "Retry-After: 7200".*

You can see the Retry-After, which in this case is set to 7200 seconds (two hours).

---

### Post by HermanAB on 2018-10-29
Yes, curl will show you the relevant packets very nicely.  Another way to debug a web server is by crafting http messages manually with telnet.

However, if you have trouble lower down in the stack with ARP or DNS or something weird happens, then tcpdump is invaluable.  Many people are scared of low level network tools, but you should not be.

---

### Post by Paddy Landau on 2018-10-29
Thanks, Herman. I realise now what you mean.

I run the website through GoDaddy, so I can't do that, but it might be useful for someone else reading this thread.

---

