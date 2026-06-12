---
title: "Autocomplete ssh logins on a FreeIPA system?"
date: 2020-12-03
forum: General Help
---

### Post by NertSkull on 2020-12-03
I have user authentication set up using FreeIPA for a handful of computers in my home.  SSH keys are handled through that.

I want to tab-autocomplete my ssh logins so I don't have to type my hostnames.  This worked out of the box when I was playing around with Arch linux.  I could type ssh me@my {tab} and it would complete to ssh [EMAIL="me@myhost.mydomain.com"]me@myhost.mydomain.com[/EMAIL] and I could log in.

This does not work on ubuntu (I'm actually on Kubuntu, but don't think it matters).  I've turned off HashKnownHosts in the /etc/ssh/ssh_config.  And that works for a raspberry pi I have that is not controlled by FreeIPA.  I can tab-complete that ssh login.  But none of the freeipa ones.

There has to be a way to do this, because like I said it worked on Arch after I had logged in once through ssh.  Maybe there is a separate file somewhere that can store these entries for me so that on second attempt it will look up there for auto completion?  Or some way to interact with FreeIPA to get the hostnames.  I noticed if I delete the known hosts in /var/lib/sss/pubconf/known_hosts and then log in to one of the freeipa machines, then that file gets populated with all the known hosts from freeipa.  So I *think* maybe that file is populated from FreeIPA?  But it's hashed, so I don't think that's where Arch was getting it from, since it's hashed (unless it gets hashed by ubuntu when coming over, but I turned off hash, so I don't think so).

Anyway, I'm just speculating and have no idea.  I'm thinking a separate file/location from which ssh could look up the domains might be the best.  Maybe then I could turn back on hashing for known_hosts which would probably be safer.  But I don't really want to maintain a list, I would like to have it auto-add hosts I've logged into like on Arch.

---

### Post by TheFu on 2020-12-03
I use the ~/.ssh/confg file.

---

### Post by ActionParsnip on 2020-12-03
Or make scripts that login as you need.

---

### Post by TheFu on 2020-12-03
> **ActionParsnip said:**
> Or make scripts that login as you need.

I did that for years, before discovering the ~/.ssh/config file which is used by all ssh-capable tools. When old-timers learn about this file, it changes their setups completely.  It is more useful than ssh-copy-id.

---

### Post by ActionParsnip on 2020-12-03
> **TheFu said:**
> I did that for years, before discovering the ~/.ssh/config file which is used by all ssh-capable tools. When old-tiers learn about this file, it changes their setups completely.  It is more useful than ssh-copy-id.

Not used ssh-copy-id. I just do it using ssh
```

cat ~/.ssh/id_rsa.pub | ssh user@server "cat >> /home/user/.ssh/authorized_keys"

```

Dead simple and works all over. ssh-copy-id may not be available on the systems you are working on :)

---

### Post by NertSkull on 2020-12-04
> **TheFu said:**
> I use the ~/.ssh/confg file.

This works. Didn't know about this, thanks.  Not quite what I'm looking for because I have to manually put entries in it seems, and it doesn't auto-add after a first initial log in.  But that's not a big deal.  After reading up on it, the config file actually makes things even simpler and easier, so overall it's a better solution anyway.  

Thanks again!

---

