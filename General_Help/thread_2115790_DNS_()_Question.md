---
title: "DNS (?) Question"
date: 2013-02-13
forum: General Help
---

### Post by Dan Again on 2013-02-13
I don't even really know how to properly phrase this question, but I'll try.

I just got a Raspberry Pi and I'd like to use it as a little toy web server. I set up a static IP address that seems to be working well enough and also spun up a Tomcat servlet than I can access from another computer on my wireless network by navigating to <static IP address>:8080

I have a domain name hosted by GoDaddy. I'd like to be able to point my browser to <my domain name>.<Raspberry Pi hostname> from anywhere. How do I make this happen?

---

### Post by sandyd on 2013-02-13
> **Dan Again said:**
> I don't even really know how to properly phrase this question, but I'll try.

I just got a Raspberry Pi and I'd like to use it as a little toy web server. I set up a static IP address that seems to be working well enough and also spun up a Tomcat servlet than I can access from another computer on my wireless network by navigating to <static IP address>:8080

I have a domain name hosted by GoDaddy. I'd like to be able to point my browser to <my domain name>.<Raspberry Pi hostname> from anywhere. How do I make this happen?

1.
You can't do <my domain name>.<Raspberry Pi hostname>, but you can do <Raspberry Pi hostname>.<my domain name> - which is a subdomain. i.e. raspberrypi.mydomain.com . It does not need to be the name of the raspberry pi as well. You can also just use <my domain name>

2.
You need an A record in your DNS pointing to the public IP address of your router. If your public IP Address is dynamic - use something like ddclient to keep it updated. A few places like dns.he.net allow dynamic ip updates for your sub/domains. The A record should be set in the sub/domain that you decided on above.

3.
You need to foward port 8080 in your router to <internal staticip>:8080

---

### Post by Dan Again on 2013-02-14
Okay, that seems like very helpful information. When you say I need an A record in my DNS pointing to the public address of my router...
What is an A record? How do I get/make one?
How do I find the public address of my router?
Can I make the public IP address static?

---

### Post by Dan Again on 2013-02-14
Okay, I am looking at my router's firmware menu webpage, and I see a drop-down for DDNS, which is currently disabled. However, there are two other options: DynDNS.org and TZO.com.

---

### Post by papibe on 2013-02-14
Hi Dan Again.
> **Dan Again said:**
> I set up a static IP address ...
LAN or Public?

I'm not very verse in this issue (I haven't done it myself), but this is what I've read:
[LIST]
[*]If you don't have a static public IP, get a dynamic DNS service.
[*]Then go to your admin registrar page and forward the domain you own to one you got from a dynamic DNS service ([Forwarding or Masking Your Domain Name]("http://support.godaddy.com/help/article/422/forwarding-or-masking-your-domain-name")).
[/LIST]Hope it helps and let us know how it goes.
Regards.

---

### Post by papibe on 2013-02-14
> **Dan Again said:**
> Okay, I am looking at my router's firmware menu webpage, and I see a drop-down for DDNS, which is currently disabled. However, there are two other options: DynDNS.org and TZO.com.
I believe DynDNS is not free anymore (just paid service). I don't know about TZO.

Although using your router as a ddns is much easier, you are not limited by those options. You can install 'ddclient' on your server and have lots of options for DDNS services.

Regards.

---

### Post by Dan Again on 2013-02-14
Well, apparently I am less versed than you, as I do not know if it is LAN or public. My guess is LAN. What you're saying in the second point is that I need to get something from a dynamic DNS service, then take this thing to GoDaddy to forward the domain they host for me to dynamic service?

---

### Post by papibe on 2013-02-14
> **Dan Again said:**
> My guess is LAN.
If you are not paying extra bucks for a public IP, then it is a LAN static IP ;)

> **Dan Again said:**
> What you're saying in the second point is that I need to get something from a dynamic DNS service, then take this thing to GoDaddy to forward the domain they host for me to dynamic service?
That's the idea. I don't know the details on how to exactly do it, but I know that is the common practice.

[Here]("http://support.godaddy.com/groups/domains-management-and-services/forum/topic/godaddy-and-dynamic-dns/")'s another reference from the GoDaddy's forum (which points to my previous link BTW :D).

Let us know how it goes.
Regards.

---

