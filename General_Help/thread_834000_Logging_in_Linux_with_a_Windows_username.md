---
title: "Logging in Linux with a Windows username"
date: 2008-06-19
forum: General Help
---

### Post by jamesattard on 2008-06-19
I managed to join my Linux box with the company's domain, following the tutorial at [http://www.onnoot.com/wiki/how_to_join_ubuntu_samba_to_a_windows_2003_active_directory_domain](http://www.onnoot.com/wiki/how_to_join_ubuntu_samba_to_a_windows_2003_active_directory_domain) . 

The company however requires that at the login screen, I literally use my windows username, instead of logging with linux username and then use net ads join. How can I create a linux username with is mapped to the windows equivalent.

example: linux username = jamesattard, windows username = ACME/james.attard

Is this possible?

---

### Post by justleen on 2008-06-19
depens what you want.. 

We use a windows network here too, and I run Ubuntu on my laptop. I dont logon with my windows username, just my local name. 

Once logged in, I mount the different drives I need - its at this point that i use my windows username and password. 

So... why do you need to logon with your username? what do you need of the network?

---

### Post by lisati on 2008-06-19
If their network's set up properly, they should be able to infer your machine name. If it's your own machine you're using, I see no reason to make your local login the same as the login name they require for their part of the network.

---

### Post by jamesattard on 2008-06-19
Basically we have an internet browsing monitor software which is basically a web content monitoring software. this software communicates with windows active directory to check the mapping between the windows domain username and ip address. at the moment this software cannot map my IP address to my username, even after i do the "net ads join", and thus i am invisible for the software (actually appearing only as IP).

---

### Post by jamesattard on 2008-06-19
* bump *

---

### Post by werries on 2008-06-19
don't bump unless its been 24 hours, please and thank you.

also, have you tried calling and asking your company for help? =D

---

### Post by jamesattard on 2008-06-19
lol ok i didn't know about the 24hr bump rule. well, i'm the only guy who uses linux in the company.

anyways after some research it appears that i need to install some pam modules to be able to use a windows username. still stuck though. this seems a very black box kind of configuration from what i'm seeing.

---

### Post by werries on 2008-06-20
does your company allow remote login? cause if so, why not just use the Terminal Server Client that comes with ubuntu. My brother uses it to log on to his University of Michigan account and use the windows stuff.

---

### Post by robklg on 2008-06-20
What you will want is authentication using winbind against the domain controller, and PAM accepting this login.

Here's a (redhat) guide to do this:

[http://tech.givemethe.net/node/18](http://tech.givemethe.net/node/18)

See the section 'PAM'.

If the domain user is the first to login to the Linux workstation, home directory and everything is automagically created.

It's what you need right?

---

### Post by jamesattard on 2008-06-20
hey guys I managed to do what I requested and documented it in my techblog: [http://www.madvip.net/node/92]("http://www.madvip.net/node/92"). In a nutshell, I used Likewise-open.

---

