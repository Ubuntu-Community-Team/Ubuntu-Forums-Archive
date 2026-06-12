---
title: "[SOLVED] nfs hostname resolution"
date: 2008-02-15
forum: General Help
---

### Post by dondad on 2008-02-15
I have two computers on an internal lan where I want to mount a shared folder. I have nfs running on both machines, a mount point set up, and a shared folder on the other machine. I can mount it if I use the ip address of the other box, but not if I use the hostname. The ip addresses are DHCP from the router. I checked the router and the hostnames are ok. How can I get it to mount using the hostname rather than the ip address? Also, how do I make the mount permanent after I finally figure it out?

---

### Post by kaginken on 2008-02-15
DonDad,

     Sounds like all you need is an entry in your /etc/hosts file.  Try this:

sudo cp /etc/hosts /etc/hosts_backup
sudo gedit /etc/hosts

Now add in the hostname and IP like so:

x.x.x.x     hostname

Save and exit.  See if you can now ping the hostname and get replies.  I'd be surprised if you can't - that would mean you have other problems than just a name resolution.

As far as making the mount permanent - try adding it to your fstab (filesystem table).

sudo cp /etc/fstab /etc/fstab_bak
sudo gedit /etc/fstab

Add in your nfs share - if you need help with this, try 

man fstab

Hope this helps!!

---

### Post by dondad on 2008-02-15
> **kaginken said:**
> DonDad,

     Sounds like all you need is an entry in your /etc/hosts file.  Try this:

sudo cp /etc/hosts /etc/hosts_backup
sudo gedit /etc/hosts

Now add in the hostname and IP like so:

x.x.x.x     hostname

Save and exit.  See if you can now ping the hostname and get replies.  I'd be surprised if you can't - that would mean you have other problems than just a name resolution.

As far as making the mount permanent - try adding it to your fstab (filesystem table).

sudo cp /etc/fstab /etc/fstab_bak
sudo gedit /etc/fstab

Add in your nfs share - if you need help with this, try 

man fstab

Hope this helps!!

I am pretty sure that would work, but what happens when the ip address gets renewed and changes (since I am running DHCP). Then it would break again wouldn't it? Right now, the ip address is 192.168.0.131, but if the power goes out or the whole system resets, it could change. I plan to use this mountpoint for some automatic backups and really need to make sure it is always available.

The dns server is my router, and it looks like the dns server in the ubuntu configuration is the right ip address for the router. If I check the router, it has the correct hostname for both of the computers and the network printer. Just trying to figure out why the hostname does not resolve to an ip address via dns. 

The router is a D-link DI 644M isf that makes any difference. Thanks for taking the time to answer.

---

### Post by kaginken on 2008-02-16
You are correct on all counts.  Regardless, as a network/systems administrator for the last...10? years, I've never found a reliable DNS yet.  My latest router still doesn't work correctly.  Two points I'd like to make -

1) Your DHCP will probably very rarely assign a different IP address.  While it may someday, it's very unlikely it will occur frequently so you can probably get away with just tweaking your hosts file once every few years.

2)  If you really want to have that share set up reliably, that machine hosting the share needs a static IP..why not set up a permanent IP for that box, hard code it's static IP in your /etc/hosts file(s) on any client machines you want to connect to it, and as some would say, 'faget about it'!

---

### Post by dondad on 2008-02-16
> **kaginken said:**
> You are correct on all counts.  Regardless, as a network/systems administrator for the last...10? years, I've never found a reliable DNS yet.  My latest router still doesn't work correctly.  Two points I'd like to make -

1) Your DHCP will probably very rarely assign a different IP address.  While it may someday, it's very unlikely it will occur frequently so you can probably get away with just tweaking your hosts file once every few years.

2)  If you really want to have that share set up reliably, that machine hosting the share needs a static IP..why not set up a permanent IP for that box, hard code it's static IP in your /etc/hosts file(s) on any client machines you want to connect to it, and as some would say, 'faget about it'!

Thanks for the replies. I was hoping that I was just missing something, but I guess your suggestion of setting up a static IP or just setting it in the hosts file are the best alternatives. I will mark this one solved.

---

