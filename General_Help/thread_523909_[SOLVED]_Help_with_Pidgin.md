---
title: "[SOLVED] Help with Pidgin"
date: 2007-08-12
forum: General Help
---

### Post by jeremy1138 on 2007-08-12
Does anyone have any idea why Pidgin isn't connecting to either AIM or Yahoo for me?  I just installed it a few days ago and it won't connect to any of my screen names.  Gaim does exactly the same thing too.  Does anyone have any ideas how I might fix this problem or what I might do to diagnose the problem myself?  Also, I'm not sure if this is relevant or not, but I can connect through my Firefox browser to AIMExpress on the AIM website.  

Thanks in advance for any help you can offer! :)

---

### Post by prince_niceguy on 2007-08-12
Best way to debug would be run through command line and see if it is giving any error on connection. If yes then we can debug and find out what is the issue.

I am able to connect to yahoo. I do not have aim so cannot confirm the same.

---

### Post by jeremy1138 on 2007-08-12
Ok I just ran Pidgin from the terminal and I let it sit for a while until an error message came up in Pidgin.  The message in pidgin said that I'm disconnected and that my connection timed out.  No errors were spit back into the terminal; this is all it says:
```

jeremy@jeremy-laptop:~$ pidgin

```
Is there anything else that I might try?

EDIT:
Thanks for the quick reply!

---

### Post by jeremy1138 on 2007-08-12
Is there anywhere that I can look to find a tutorial or something?  Maybe there is some way that it's being blocked so it can't communicate with the network?  Is there a way to check?

---

### Post by kellemes on 2007-08-12
Firewall running?

---

### Post by jeremy1138 on 2007-08-12
> **kellemes said:**
> Firewall running?

I don't have a firewall running currently...  I did have firestarter going yesterday but it didn't seem to make any difference...  Gaim and Pidgin weren't working before I put the firewall on...

Thanks for the quick reply! :)

---

### Post by DirtDawg on 2007-08-12
Yahoo has worked flawlessly in Pidgin for me. There's a thread in the Suse forums that has a couple suggestions:
[http://forums.suselinuxsupport.de/index.php?showtopic=57953](http://forums.suselinuxsupport.de/index.php?showtopic=57953)

Other than that, maybe you have a setting wrong somewhere?

Remember to use screen_name, not [email]screen_name@yahoo.com[/email].

My advanced settings: 
"Proxy Type" set to "Use GNOME Proxy Settings."
My File Transfer Server is: filetransfer.msg.yahoo.com
File Transfer port is: 80
Encoding is: ISO-8859-1

I'm not sure any of this has anything to do with anything. I'm just tossing out ideas as it sounds like you're stuck. One user in the Suse forum even says reinstalling solved the issue for him.

---

### Post by DirtDawg on 2007-08-12
I also found this in the Pidgin FAQ. Again, I'm not sure it has anything to do with anything, but maybe it's worth looking at:
[http://developer.pidgin.im/wiki/Protocol%20Specific%20Questions#WhycantIconnecttoYahoofrombehindafirewallorNAT](http://developer.pidgin.im/wiki/Protocol%20Specific%20Questions#WhycantIconnecttoYahoofrombehindafirewallorNAT)

---

### Post by jeremy1138 on 2007-08-12
I'm trying to reinstall now...  Someone in that forum you pointed me to mentioned that reinstalling worked for them...  We'll see...  Messing with the settings didn't help... 

Thanks for the replies!

---

### Post by jeremy1138 on 2007-08-12
Reinstalling doesn't seem to have worked either...  I'm at a loss now...  I really want to get this working; it's one of the last really annoying problems that I need to sort out to get this Ubuntu working smoothly.

I'm sure something will come along!  Thanks for all your help!  Please let me know if anyone has any other ideas.  :)

---

### Post by BlackAnthrax on 2007-08-12
I use AIM/YAHOO/GMAIL daily with Pidgin, so it is very possible, I haven't had to do anything extra. However, call me crazy, but I have one yahoo screename that won't connect. perhaps create a new one and test it? Also, do you have any HARDWARE firewalls or such? You may need to forward a port or so...

---

### Post by jeremy1138 on 2007-08-13
Does anyone know how I can set up an HTTP or SOCKS proxy for my AIM account in Pidgin? 

To set up the HTTP proxy, GAIM asks for:
1)Host
2)Port
3)Username
4)Password

For the SOCKS4 and SOCKS5 proxies it wants the same things...  I have no idea what I'm doing with proxies so is there any way that someone could tell me what to put in those fields?  Maybe that will get Pidgin working?  Thanks for all your help everyone! :)

---

### Post by jeremy1138 on 2007-08-13
What is the 'use environmental settings' for?  Is there something that I can change around in Linux to get this working?  Is there some program that I need to download to get the other types of proxies working?  I'm lost with proxies...

---

### Post by DirtDawg on 2007-08-14
Have you tried using a different client yet just to see if they work? Maybe Kopete, centericq or even the unix version of the Yahoo messenger. At least that way you could see if it's pidgin problem or something with your system. 

I hope you get this worked out. I sympathize with your frustration.

---

### Post by DirtDawg on 2007-08-14
Most people who have similar problems seem to be running a firewall. If you are using any kind of a router, it may have a firewall installed by default (I know mine does). It's possible that's what's keeping you from connecting regardless of whether you have a firewall installed on your computer or not.

---

### Post by jeremy1138 on 2007-08-14
Thanks for all your help everyone!  I just got Pidgin working by editing my advanced settings to all use port 80 with the no proxy setting enabled.  I did this for both my yahoo and aim accounts and all work fine now.  The ports that they were using must have been blocked by my router.

---

