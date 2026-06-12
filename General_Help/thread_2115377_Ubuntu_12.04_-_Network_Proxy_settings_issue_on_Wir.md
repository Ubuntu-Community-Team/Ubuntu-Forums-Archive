---
title: "Ubuntu 12.04 - Network Proxy settings issue on Wired network at work"
date: 2013-02-12
forum: General Help
---

### Post by LostInTheMatrix on 2013-02-12
I had absolutely no response to my Thread under "Networking and Wireless" so I am posting here...

I am having issues with network proxy settings while on wired network at work.
First of all - Internet access works fine on both wireless as well as wired network at home. 
The problem is that when I am at work, my computer is on wired network. In order to successfully access internet from my web browsers, I turned on the Auto-Proxy-Detect feature in both web browsers - Firefox and Chrome - and with that I could access internet from the web browsers successfully.
The problem is that, outside of the web browsers none of the apps can access the internet, not even Ubuntu Software Center. When I ping, say [www.google.com](www.google.com), or any other internet address from the command line I get a message saying the Destination Host unreachable.
Under the Network Settings > Network Proxy, I choose the Method as "Automatic" and click on the "Apply System Wide" button, but that does not do anything. It does not prompt me for password - probably because I have the URL field blank. 

How do I fix this?

---

### Post by dcstar on 2013-02-14
> **LostInTheMatrix said:**
> I had absolutely no response to my Thread under "Networking and Wireless" so I am posting here...

I am having issues with network proxy settings while on wired network at work.
First of all - Internet access works fine on both wireless as well as wired network at home. 
The problem is that when I am at work, my computer is on wired network. In order to successfully access internet from my web browsers, I turned on the Auto-Proxy-Detect feature in both web browsers - Firefox and Chrome - and with that I could access internet from the web browsers successfully.
The problem is that, outside of the web browsers none of the apps can access the internet, not even Ubuntu Software Center. When I ping, say [www.google.com](www.google.com), or any other internet address from the command line I get a message saying the Destination Host unreachable.
Under the Network Settings > Network Proxy, I choose the Method as "Automatic" and click on the "Apply System Wide" button, but that does not do anything. It does not prompt me for password - probably because I have the URL field blank. 

How do I fix this?

Find out the Proxy settings and enter them manually.

---

