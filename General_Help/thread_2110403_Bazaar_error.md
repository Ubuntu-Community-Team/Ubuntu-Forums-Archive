---
title: "Bazaar error"
date: 2013-01-30
forum: General Help
---

### Post by 2cool4u92 on 2013-01-30
Hi,

I'm having an error with bzr. I'm working under a proxy in my college, but I was able to get it to work before and the error remains when I'm using unrestricted internet too.

When I try to fetch a project,

```

 krishna@krishna-Lenovo-G560:~$ bzr branch lp:calibre

```I get the error
```

/bin/bash: line 0: exec: corksrew: not found
ssh_exchange_identification: Connection closed by remote host
ConnectionReset reading response for 'BzrDir.open_2.1', retrying
/bin/bash: line 0: exec: corksrew: not found
ssh_exchange_identification: Connection closed by remote host
bzr: ERROR: Connection closed: Unexpected end of message. Please check connectivity and permissions, and report a bug if problems persist. 

```corkscrew is spelled "corksrew" so I'm guessing a typo, but I can't figure out where to modify it, any ideas ?

---

### Post by 2cool4u92 on 2013-01-30
Hey,

I got some help from the irc and partially solved my problem. I went to ~/.ssh/config
Then corrected the typo("corksrew" to "corkscrew"). Next I need to configure corkscrew to ssh under a HTTPS proxy.
Loads of thanks to <mgz> from #bzr :D

---

