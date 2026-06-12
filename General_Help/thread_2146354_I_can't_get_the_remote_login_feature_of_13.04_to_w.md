---
title: "I can't get the remote login feature of 13.04 to work."
date: 2013-05-18
forum: General Help
---

### Post by scweston on 2013-05-18
Hi,

I've done a fresh install of Ubuntu 13.04 on my laptop and I'm trying out the remote login feature directly from the ubuntu login screen. I've already clicked on the '?' next to remote login and set up the remote desktop RDP details for my desktop machine (which also runs ubuntu).

Unfortunately when I put in the email address and password details for my ubuntu one account to list the remote desktop I've set up it always tells me I've entered the incorrect email or password. I'm 100% confident I'm entering the correct details and I can access my ubuntu one account perfectly fine through firefox using the same details. I can see the computer is definitely linked to the network and internet (i've checked it with both a wireless and wired connection).

Can anybody suggest what I'm doing wrong and how I should correct this. 

I appreciate any help, so thank you in advance for reading this.

Stephen

---

### Post by scweston on 2013-05-19
I've tried experimenting a bit and still can't get the remote login feature of 13.04 to recognise my ubuntu one email and password.

I tried downgrading to Ubuntu 12.10 just to see if that would work, and strangely, it works perfectly and recognises my email and password without issue.

I'm assuming this is a bug in Ubuntu 13.04, but I can't see anybody else complaining of this issue so I'm not sure. Please, does anybody know a workaround? Unfortunately I don't know how to file bug reports.

Regards. Any help is still appreciated.

Stephen

---

### Post by sudodus on 2013-05-19
It's probably a bug. Please report it at launchpad :-)

Even if your report will be a doublet, there are people who will find that and your report will increase the focus on this particular feature.

But you asked about a work-around. You can install remote login software and do the same thing inside your logged in session. The simplest way is probably to run ssh (only text mode) or ssh -X (graphical mode). Next step might be for example rdesktop.

---

### Post by arne-n on 2013-09-05
You are not doing anything wrong. Remote Login is not supported in Ubuntu 13.04. Go to [https://uccs.landscape.canonical.com/](https://uccs.landscape.canonical.com/) and you will see the following text:
> Remote desktops from any device, anywhere...
Access your remote desktops from any device running Ubuntu 12.10

I tried and got the same problem as you. IMHO it's bad of Ubuntu to include the Remote Login option in 13.04 when it's not supported.

---

