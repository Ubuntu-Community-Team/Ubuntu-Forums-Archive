---
title: "cannot connect to equifax"
date: 2019-06-24
forum: General Help
---

### Post by jgw on 2019-06-24
This is very strange.  I cannot connect to [www.equifax.com](www.equifax.com)   I have tried with both firefox and google chrome.  I have tried on 2 separate computers.  It just times out.  I can, however, goto [www.equifax.com](www.equifax.com) on my phone and on my wife's machine (it run Windows 10).

I have no idea what is blocking this one.  Since it happens on 2 different browsers its not that.  Since it does it on 2 separate computers its not that.  It does, however, work on Windows 10

Thoughts?

---

### Post by Frogs Hair on 2019-06-24
It works here on Firefox from US.

---

### Post by HermanAB on 2019-06-25
$ nslookup [www.equifax.com](www.equifax.com)

---

### Post by jgw on 2019-06-25
Thank you for the reply.

I can get there on a microsoft machine but not 3 different ubuntu machines.  I believe ubuntu is doing this but have no idea how or why or how to fix it.  nslookup gave me:
greg@gregdown:~$ nslookup [www.equifax.com](www.equifax.com)
Server:		127.0.0.53
Address:	127.0.0.53#53

Non-authoritative answer:
Name:	[www.equifax.com](www.equifax.com)
Address: 216.46.96.115

If I try and link from a google list ([www.equifax.com/personal](www.equifax.com/personal))  It tries to goto [https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&ved=2ahUKEwjotLyCkIXjAhUD7J8KHT3vABAQFjAAegQILhAC&url=https%3A%2F%2Fwww.equifax.com%2Fpersonal%2F&usg=AOvVaw26QPVv_vGeVZhPMXQ_jlGc](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&ved=2ahUKEwjotLyCkIXjAhUD7J8KHT3vABAQFjAAegQILhAC&url=https%3A%2F%2Fwww.equifax.com%2Fpersonal%2F&usg=AOvVaw26QPVv_vGeVZhPMXQ_jlGc)

If I just enter [www.equifax.com](www.equifax.com), or try the address (216.46.96.115) given with  nslookup I get a blank page and eventually it times out.  Took a look at 127.0.0.53#53 which seems broken.
There is no little line telling me its trying, transferring, etc. Its very strange.......

I have, obviously, done something pretty clever here <sigh>

Thank you...............

---

### Post by HermanAB on 2019-06-25
I suspect that you have a browser advert allergy.
;)

Try the site with adblock or noscript enabled.

---

### Post by jgw on 2019-06-25
thank you for the reply.

Tried it with, and without adblock and noscript - no cigar.

Also tried in firefox, chromium, and google chrome - nope

Its gotta be something in my network connection but its beyond me what it might be.  Maybe I should re-install network.  The problem is that its doing it on three separate ubuntu computers but works on a windows machine.  This tells me that my router is not doing it as they are all running off that (actiontec c2000a)

---

### Post by #&amp;thj^% on 2019-06-25
Are you using a VPN on your Ubuntu machines.?
**EDIT:** I just tried with my VPN enabled and show the same as you see.
I Quit the VPN and can now access the site.

---

### Post by HermanAB on 2019-06-25
It seems to me that your system resolves the site, but doesn't display it.  So it is probably not a network problem.

What happens with lynx, or links text browsers?

---

### Post by jgw on 2019-06-25
Thanks again for the replies.

IT WAS THE VPN!!!!!!!!!!!  Turned it off and it appeared!  Now I will goto my vpn folks and ask the question (PIA)

Thanks again!!!!!!!!!!

---

### Post by jgw on 2019-06-26
I complained to PIA (my VPN) and received the following - thought maybe folks might want to know:


We apologize for the inconvenience this may have caused you. We are not in the business of blocking anything you wish to browse.  Unfortunately, blacklisting of IPs is a very common problem with VPNs. Some large websites, including retailers, streaming services, banks, and marketplaces like Craigslist, place a blanket ban on VPN use. While we rotate our IPs regularly, we are unable to render support or assistance in accessing restricted content via our service. Your VPN may need to be turned off to access these services.

We have a solution that may work out for you without requiring you to turn off the VPN.  This can only be accomplished on a desktop, however, but it involves making use of our browser extensions for either, Opera, Chrome, or Firefox.  

Within each extension's settings is what we call the Bypass List.  This is a registry for websites that are known to block VPNs. Once websites are saved to it, the VPN will automatically open up the site, but will keep information encrypted elsewhere.

---

### Post by #&amp;thj^% on 2019-06-26
> **jgw said:**
> I complained to PIA (my VPN) and received the following - thought maybe folks might want to know:


We apologize for the inconvenience this may have caused you. We are not in the business of blocking anything you wish to browse.  Unfortunately, blacklisting of IPs is a very common problem with VPNs. Some large websites, including retailers, streaming services, banks, and marketplaces like Craigslist, place a blanket ban on VPN use. While we rotate our IPs regularly, we are unable to render support or assistance in accessing restricted content via our service. Your VPN may need to be turned off to access these services.

We have a solution that may work out for you without requiring you to turn off the VPN.  This can only be accomplished on a desktop, however, but it involves making use of our browser extensions for either, Opera, Chrome, or Firefox.  

Within each extension's settings is what we call the Bypass List.  This is a registry for websites that are known to block VPNs. Once websites are saved to it, the VPN will automatically open up the site, but will keep information encrypted elsewhere.

Yep, and I should of stated that in my previous post but I knew you would get the same answer I did. 
I'm not yet convinced the addons work as advertised.
This was all due to one of the biggest leaks in equifax a couple of years ago. >>>:[https://www.privateinternetaccess.com/blog/2017/09/equifax-yet-another-catastrophic-leak-old-world-cant-get-away-with-this-anymore/](https://www.privateinternetaccess.com/blog/2017/09/equifax-yet-another-catastrophic-leak-old-world-cant-get-away-with-this-anymore/)

---

### Post by jgw on 2019-06-26
it didn't work for me.  

"Within each extension's settings is what we call the Bypass List" was interesting but I have no idea how to enter the offending url.  I guess I will email them and ask.

I know about that leak.  Congress passed a law, on behalf of the banks, years ago.  I think I posted this but.  The bank told the congress that the personal information was just that and the individual was responsible for his/her personal information and it wasn't their fault if there was a leak - it was the fault of the person involved!  The congress bought it and extended that to anybody who had personal information (banks, internet, whoever).  As far as I know that remains in force although I remain amazed that nobody seems to understand that.  I do remember that, at the time, there was no internet (I go back a way) just, basically, email and the usenet.  So, basically, if somebody gets your info YOU are at fault!  (its almost amusing <sigh>)

---

### Post by #&amp;thj^% on 2019-06-26
> **jgw said:**
> it didn't work for me.  

"Within each extension's settings is what we call the Bypass List" was interesting but I have no idea how to enter the offending url.  I guess I will email them and ask.



I'm not sure if you found the setting or not but see screenshot. And it is at the bottom, may have to uncover to see it.
**FWIW: This addon needs a ton of improvement**

---

### Post by jgw on 2019-06-27
I wrote to them and got directions.  A bit confusing, I think.  Here is the start:
"Since you have PIA already installed on your computer, if you are going to use the extension, please be sure that the PIA software that you installed previously is disconnected, or not running. 

If you attempt to use the browser extension as well as the program itself, you "will" have connection conflicts, and at times not being able to connect at all."

I wrote back asking if he really wanted me to install the extension, turn off pia and then access the url.  I think he was referring to the installation but who knows?  I do now have it installed, however, and they did have directions on howto to add stuff to the bypass list.  I will make a run at it tomorrow.

---

