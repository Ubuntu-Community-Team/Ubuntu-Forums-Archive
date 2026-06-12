---
title: "Unable to surf using Firefox although all networking appears to be correct"
date: 2005-08-30
forum: General Help
---

### Post by wendallsan on 2005-08-30
Hi all,

I am running Ubuntu on 2 systems, one at home and one at work.  The system at work is running great.  The system at home is running great other than the fact that I am unable to use the Firefox browser to surf the web.  The home system is connected to the network fine, I have tried both dhcp and manually configured IP settings and am getting the same result.  I can ping hosts on my subnetwork and on the Internet, so it is getting to my router and doing domain name lookups fine.  I can do things like download files for system updates and installing new software using Synaptic, so I do have network connectivity, it is just that no web pages are coming up.  

The process that I am seeing in Firefox is this: I will type in a URL (for example "www.opera.com") and hit enter, at the bottom of the browser, I get the message "looking up host", which resolves itself in a second or 2 and the message is replaced with "connecting to www.opera.com".  This hangs from a couple seconds to up to a minute depending on which site I am trying to get to, and then an alert message comes up stating "The connection was refused when attempting to connect to opera.com".  

Has anyone run into this before?  I am confused because I have not changed any options within Firefox that I am aware of, and the system at work is running fine, while this one is not.  I am running Hoary, and both systems were installed from the same installation media.  If I can get this resolved, I am planning on using Ubuntu as my primary Linux distro, as I'm very happy with it's ease of use and layout so far.  Thanks to anyone that can suggest a solution to this!

---

### Post by 5-HT on 2005-08-30
Are you running through a software firewall (or have configured iptables) that may be blocking ports 80 or 443 (shouldn't be the router unless it was reconfigured)  ?


I had the same symptoms with the same error that were fixed by adjusting my firewall.

It's funny as I'd expect to see something along the lines of "unable to find host" or  "this page cannot be displayed"  instead of "The connection was refused when attempting to connect..."
 

Another thing to try would be to see if you have Firefox set up using a proxy (which isn't enabled by default so this probably won't do you much good, though always good to check).

Hope you get Firefox up and running.

---

### Post by mond on 2005-08-30
What ISP are you using?

> "The connection was refused when attempting to connect to..."

I was getting the same response a while back and I think it was a problem with my ISP (Pipex). It went away after a while but it was very annoying as it seemed a bit random.

Try rebooting your router and computer and you could always contact your ISP to find out if they are experiencing any technical problems.

That's all I can think of I'm afraid.

---

