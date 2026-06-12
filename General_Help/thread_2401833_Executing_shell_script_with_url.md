---
title: "Executing shell script with url"
date: 2018-09-23
forum: General Help
---

### Post by lizard2014 on 2018-09-23
I want to execute a shell script when someone enters Facebook.com or Twitter.com in the url bar of Firefox. How to do that without letting these sites open?

---

### Post by TheFu on 2018-09-23
I'm pretty certain that allowing a URL to run anything outside the browser sandbox would be a huge, huge, huge, security problem.

If you want to block specific sites: [https://lifehacker.com/5817447/how-to-block-unwanted-ads-in-all-applications-and-speed-up-web-browsing-with-the-hosts-file](https://lifehacker.com/5817447/how-to-block-unwanted-ads-in-all-applications-and-speed-up-web-browsing-with-the-hosts-file)

---

### Post by lizard2014 on 2018-09-23
Is it possible to run a command in background which keeps monitoring web activity and once these websites are opened in Firefox, only then the command proceeds further. (What I want is when someone enters either of the two websites mentioned above, system should automatically log out of the current user, then login to another user and open the website).

---

### Post by HermanAB on 2018-09-23
Have a look at the squid proxy.  Some googling will find many guides.

---

### Post by TheFu on 2018-09-23
> **lizard2014 said:**
> Is it possible to run a command in background which keeps monitoring web activity and once these websites are opened in Firefox, only then the command proceeds further. (What I want is when someone enters either of the two websites mentioned above, system should automatically log out of the current user, then login to another user and open the website).

I have no idea how to do that as stated.  Perhaps the easy answer is to have 1 browser instance block all the sites, then use another browser running inside a separate "container" for access to the other sites.  You can even make one use a VPN/proxy/TOR and have the other not use any VPN.  Getting this stuff to work isn't "beginner friendly" at this point, I wouldn't think,  

And there wouldn't be anything automatic about it, but you can script almost anything.

---

### Post by SeijiSensei on 2018-09-24
Another vote for Squid.  You can run it on the same machine as the browser, then tell the browser to use localhost:3128 as its proxy.  You can permit or deny by domain name, URL, time of day, etc., etc.  I don't think Squid can invoke a shell script, though, nor do I think you would want to.  

If the purpose of the shell script was to display a message for the user saying access to the site is blocked, you can accomplish that goal by editing the default message Squid displays for blocked sites.

If you are managing multiple client machines, you'll want to set up a server that runs Squid.  You can configure each client to use the proxy separately, or make that machine the default gateway for the clients and use "transparent" proxying.  There's a lot of information about this on the web.  I maintain a proxy for a customer that serves some 200+ clients and controls access to places like Facebook.  It also scans every downloaded object using ClamAV and the SquidClamAV add-on for the proxy.

SSL sites are more difficult to manage.  Squid has a nifty method to accomplish that, but it requires installing SSL certificates on the proxy server and each client machine.  See the material about "SSL Bump" for details.

---

### Post by TheFu on 2018-09-24
I love these forums!  A few different options for the problem, depending on your need.  

With the squid option, it would be smart to review your network architecture to ensure there isn't any way for the clients to bypass the proxy to get external access.  BTW, this is how large companies do it.  They don't allow desktops external access without going through a proxy.  They also block external DNS to the clients, since it is possible to tunnel packets through DNS.

---

### Post by SeijiSensei on 2018-09-24
We use transparent proxying to insure compliance.  It also avoids the need to configure each browser to use the proxy.  All DNS goes to the servers that are part of the Active Directory structure.  None of my client's users, medical and administrative staffers, would know the first thing about tunneling packets through DNS.

---

### Post by TheFu on 2018-09-24
I helped setup a school with a transparent proxy that did some blocking. Less than a week later, we found huge DNS traffic going external.

Years ago, I consulted at a fairly large company. No external, unproxied, un-MiTM'd, packets got to external locations, unless the person used their personal cellular data connection.  
Corporate cellular data devices terminated on our network and had to go through the same proxies to get to external sites, if that was allowed for those users.  Usually, there was a white-list so they could get to employee benefit websites like 401(k) plans and health insurance, but many "management" employees had nearly unrestricted access, going through the proxies.

---

### Post by SeijiSensei on 2018-09-24
We had an issue with streaming sites.  I stopped that by blocking all connections from ports > 1023 on local machines to high ports on remote hosts.  We had to add a couple of exemptions for things like GoToMyPC.

---

