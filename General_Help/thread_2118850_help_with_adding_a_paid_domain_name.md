---
title: "help with adding a paid domain name"
date: 2013-02-22
forum: General Help
---

### Post by darkvip3r on 2013-02-22
Hello there :) i am new to this forum.

I am having issues with a paid domain i got.. how do i add it to my Apache web server so it only points to one domain name??

---

### Post by Habitual on 2013-02-22
> **darkvip3r said:**
> I am having issues with a paid domain i got.. how do i add it to my Apache web server so it only points to domain??"my Apache web server"? Do you mean your local machine?

If yes, [How do I host a real domain name at home?]("http://www.boutell.com/newfaq/creating/domainathome.html")

The actual domain name would help.

---

### Post by darkvip3r on 2013-02-22
the domain name is socialzone.im

And how would i deny other domains i have on dyn.com from showing my website??

---

### Post by Habitual on 2013-02-22
Well, if you won't answer my questions, I will have to quit asking them.

Best of luck.

---

### Post by darkvip3r on 2013-02-22
sorry i mean lamp. i did not mean to be rude :)

---

### Post by cole.mickens on 2013-02-22
> **darkvip3r said:**
> sorry i mean lamp. i did not mean to be rude :)

Anyway, who did you buy your domain through? Does your home WAN IP change very often? If not, you don't really need dyn.com if your domain registrar will serve as your Nameserver.

The way it works is like this:

- you register the domain
- your tell the registrar what nameserver to use (possibly them, or dyndns, etc)
- you tell the nameserver to resolve whatever.com -> 123.221.23.1 or whatever your IP address is. (You probably want an A record)

Then on your machine, you have to teach it what to do when it receives the HTTP request. You configure Apache to respond on an interface, and/or on a specific hostname/ip address/etc.

Does that all make sense? If you're planning on running something yourself there's a lot to be wary of. Is your ISP cool with it? Do you have the bandwidth? Are you sure you want a public server in your home network? etc.

---

### Post by darkvip3r on 2013-02-22
its a dynamic ip address i have, i have the bandwidth and i brought it from name.com, i am using dyn to use as it updates and i am not sure how i add the domain name from name.com to my server

---

### Post by darkvip3r on 2013-02-22
> **cole.mickens said:**
> )

Then on your machine, you have to teach it what to do when it receives the HTTP request. You configure Apache to respond on an interface, and/or on a specific hostname/ip address/etc.

how do i do what you say here?

Sorry if i didn't give you enough info. i am new to this sort of thing

---

