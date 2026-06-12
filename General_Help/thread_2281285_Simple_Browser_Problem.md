---
title: "Simple Browser Problem"
date: 2015-06-05
forum: General Help
---

### Post by Mazate on 2015-06-05
[COLOR=#333333][FONT=Lucida Grande]Hi there

I have a rather strange issue. I just switched owncloud providers recently. For those who don't know what owncloud is, it doesn't really matter. Just for the sake of this post its a website. I switched providers but now I can't get my browsers to show the site with the new provider. If I ping the domain it returns the NEW IP address. If I do a traceroute, it routes to the new site just fine. My desktop clients sync up with the new site just fine as well. However, when I go on any of my web browsers they pull up the old site. I dual boot windows and Mint and this is a problem on both OS's. I've cleared the cache many times. I've flushed the DNS more times than I care to count. I've reset my router. Nothing helps. Like I said, its just the browsers but nothing else.

Any help is appreciated.[/FONT][/COLOR]

---

### Post by kerry_s on 2015-06-06
do you have it set as your home page ?

---

### Post by Mazate on 2015-06-06
No, nor is it bookmarked.

---

### Post by Keith_Helms on 2015-06-07
Are you saying this new provider has the exact same URL as the old provider?   http(s)://some.domain.com/somepage

---

### Post by Mazate on 2015-06-07
Yes because I use my own domain and point it to the new hosting ip.

---

### Post by Keith_Helms on 2015-06-07
Okay, I have a few questions then.

How are you associating a domain name with an IP address?  Did you put an entry in /etc/hosts?  

Do you have a proxy set in your browser?  If so, you might need to add an exception for this site.

Are you using Firefox, and if so, does it work using Chrome?

If you're using Firefox, you could try going to about:config and setting keyword.enabled = false.  That will change the behavior of the address box so that it doesn't double as a search box.  Are you entering a full URL, i.e. with an http:// or https:// prefix?  If you're entering just the domain name - some.domain.com - try adding a slash at the end.

If nothing else works, you could probably just enter the IP address in the address box - http(s)://nnn.nnn.nnn.nnn/somepage.

---

### Post by SeijiSensei on 2015-06-07
> **Mazate said:**
> Yes because I use my own domain and point it to the new hosting ip.

Do you have access to the server's logs?  What do they show?

---

### Post by Mazate on 2015-06-07
You associate your domain with an ip address with the domain's registrar on the DNS Zone File.  I do not have a proxy set.  I've tried Firefox and Chrome.  I can't use the ip address for the url because it's a shared ip with others on the same hosting server.

---

### Post by Mazate on 2015-06-07
The server's logs wouldn't be useful since the browser is connecting to the old hosting rather than the new... likely it's not connecting to the old hosting but rather showing me a cached page somehow.

---

### Post by Keith_Helms on 2015-06-07
> **Mazate said:**
> You associate your domain with an ip address with the domain's registrar on the DNS Zone File.  I do not have a proxy set.  I've tried Firefox and Chrome.  I can't use the ip address for the url because it's a shared ip with others on the same hosting server.

So you and other clients go to the same IP address and the owncloud provider figures out who you are based on the domain name you came in with, right?

I assume your old provider was a different company at a different IP address.  It sounds like a DNS server somewhere still has an old entry associating the domain name with the old IP address.

Just to see if it helps, try using a different DNS server temporarily.  Manually configure your system or router to use the Google DNS server at 8.8.8.8  

On your Mint system, you can click on the network manager icon on the taskbar, select edit, and then select the connection you're using.  Select the IPv4 tab, change the mode from automatic (DHCP) to automatic (DHCP) addresses only, and then enter 8.8.8.8 below under DNS servers.  Save it, then disconnect and reconnect.

At that point your PC should be using the Google DNS server instead of the one from your ISP.  If you click on the network manager icon again and select information, you should see 8.8.8.8 listed as the Primary DNS.

Retry your browse request and see if it goes to the right IP address this time.

---

### Post by Mazate on 2015-06-08
> **Keith_Helms said:**
> So you and other clients go to the same IP address and the owncloud provider figures out who you are based on the domain name you came in with, right?

I assume your old provider was a different company at a different IP address.  It sounds like a DNS server somewhere still has an old entry associating the domain name with the old IP address.

Just to see if it helps, try using a different DNS server temporarily.  Manually configure your system or router to use the Google DNS server at 8.8.8.8  

On your Mint system, you can click on the network manager icon on the taskbar, select edit, and then select the connection you're using.  Select the IPv4 tab, change the mode from automatic (DHCP) to automatic (DHCP) addresses only, and then enter 8.8.8.8 below under DNS servers.  Save it, then disconnect and reconnect.

At that point your PC should be using the Google DNS server instead of the one from your ISP.  If you click on the network manager icon again and select information, you should see 8.8.8.8 listed as the Primary DNS.

Retry your browse request and see if it goes to the right IP address this time.

Referring you to my original post, if I ping the domain, it returns the new ip address.  If I do a traceroute, it routes correctly to the new hosting provider.  I only have this problem in browsers, but yes I have already changed the dns servers and that didn't do anything for me.  (Other than speed up my web browsing noticably.)

---

### Post by Keith_Helms on 2015-06-08
I'm running out of ideas for why your browser stubbornly keeps going to the old IP.   When you have the page up in Firefox, hit Ctrl-Shift-R.  That is supposed to force it to reload the page and not use any cache, even though you've flushed it many times.

---

### Post by cariboo on 2015-06-09
I'd suggest clearing your browser cache to see if it makes a difference.

---

