---
title: "Efficient, Stable, Secure and Scalable - lost!"
date: 2014-04-14
forum: General Help
---

### Post by npinn001 on 2014-04-14
Hi all,

So I'm gearing up to install a fresh server install this coming weekend, and I need a bit of help please. 

What do I want to achieve?

I want security. I want to be able to have a locked down system that has a decent firewall set up. I usually use fail2ban and secure ssh with a key etc, but I guess what I am asking is, is there a benefit to having a seperate Firewall OS running to the server using something like Proxmox as the base? Or should I use KVM, or use Virtualbox?

I want efficiency. I'll be using Plex to serve media around the home, but I also want to be able to do some testing in advance of making changes or run a web server for a website. So would this be well served by running a VM on the server base, or as a seperate machine on something like Proxmox, or just all in one? For me, efficiency covers not only overhead but downtime etc.

Scalable - I need to be able to add storage after. This should be covered anyway.

Thanks

---

### Post by ian-weisser on 2014-04-14
If you're serving media around your home, then any ordinary flavor of Ubuntu should be fine for your needs.

Generally, I recommend against an overly complex setup for home use...it can annoy other family members.
Example: Keep your server and router on separate physical boxes so a broken or experimental service won't crash your whole network, and so family members can reset the router and internet connection if it fails when you're not around.

Adding storage is a question of your physical system layout and capacity. All Ubuntu systems are quite expandable that way.

---

