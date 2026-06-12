---
title: "Blocking websites."
date: 2020-02-01
forum: General Help
---

### Post by joburg on 2020-02-01
1) Is there any way that I can determine which website is automatically communicating with my computer in Ubuntu?
 
2) Is there any way that I can block a specific website from communicating with my computer?

---

### Post by aljames2 on 2020-02-01
You may need to explain more about your setup and what you are trying to accomplish. When your system is open to the internet, likely all websites you visit are “communicating” with your computer via cookies, super-cookies, and other unknowns depending on how you use the computer & configuration.  

You may be able to use your etc/hosts file to block specific IPs & domains.  Look in to you firewall settings as well.  I use Pi-hole with DNSBL on my pfSense router to filter out/block inbound web traffic based on how I set it up.  

In some cases you may have a bigger problem such as an infection of some type.  Rogue websites that have already infected an unprotected computer can sometimes adjust to your counter measures “after the fact”, through scripts that call-back (outbound) to the “mother ship” and dynamically adjust to your counter measures.

---

### Post by joburg on 2020-02-01
Thanks aljames2, the etc/hosts files may help me block an unwanted  website, if only I can now determine which website it is. What happens  is that every so often (once or twice a month) there is suddenly a huge  download to my computer and I don't know where it comes from. I would  like to somehow determine where this download comes from and maybe block  the site if necessary.

---

### Post by NM5TF on 2020-02-01
Have not found a way to identify the offending site(s) yet, but take a look here to see if this will help...after you find what site(s)
are causing the downloads...

[https://addons.mozilla.org/en-US/firefox/addon/blocksite/](https://addons.mozilla.org/en-US/firefox/addon/blocksite/)

tommy

---

### Post by HermanAB on 2020-02-02
You can monitor your network with various tools, including 'ntop', which can show a list of bandwidth hogs.

[https://www.ntop.org/guides/ntopng/](https://www.ntop.org/guides/ntopng/)

Once you identified the culprit, you can do something about it.

Ntop is part of the Ubuntu system, so you can install it with:
$ sudo apt install ntop

Here is another guide that may be useful:
[http://luca.ntop.org/download/ntop-users-guide/ntop_Users_Guide_2.3.pdf](http://luca.ntop.org/download/ntop-users-guide/ntop_Users_Guide_2.3.pdf)

---

