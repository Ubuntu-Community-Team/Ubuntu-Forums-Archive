---
title: "Tunnel connection to VPS"
date: 2015-02-28
forum: General Help
---

### Post by Vaindil on 2015-02-28
I've never done anything like this before, so I apologize if my terminology is incorrect. *(This isn't a question about the Raspberry Pi, just read on.)*


I recently acquired a Raspberry Pi and I'm setting it up for various things. I have a local router that the Pi is wired into along with my desktop computer. I want to be able to access the Pi from outside my local network, but my router is plugged into dorm internet so everything is locked down. I can (obviously) access the Pi from my desktop or a wireless device via my personal router, but I can't get to the personal router from the internet.


I have a domain through Namecheap that allows me to use dynamic DNS, and I have that DDNS working with my Pi using inadyn (set up on a subdomain). I also have a VPS running Ubuntu Server 14.10 which uses that domain.


What would be the best way to enable connections to my Pi over the internet? I want access to all ports and whatnot like normal. I started configuring OpenVPN on the VPS, but I stopped to ask this question here. Is there a way to tunnel my Pi's connection through a subdomain of my VPS and access the Pi using that subdomain (again, allowing access to my ports, e.g. pi.website.com:22 for SSH or whatever), or is there a different/better way to do this? If you describe the process and maybe name the packages I should use then I can probably figure it out from there; I shouldn't need a step-by-step. I mainly need to know what to do on the VPS side to accept connections and forward them to my Pi; I'm sure I can figure out what to do on the Pi from there.

---

### Post by QIII on 2015-02-28
Hello!

I am sorry, but we won't allow advice to be given with regard to circumventing your school's network configuration.  This is something you will need to discuss with the school's IT.

Closed.

---

