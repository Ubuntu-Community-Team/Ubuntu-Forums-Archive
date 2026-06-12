---
title: "Independent Users possibility"
date: 2017-09-30
forum: General Help
---

### Post by whatsnext on 2017-09-30
Dear All,

Thanks in advance for your help.

I am a long time user of Ubuntu, and for the last 3 years of Ubuntu mate, which I love.

For proffesional reasons, I need to install old versions of software (Firefox 51, javascript, JRE 32bits, and others). As my system is working fine and fully update, I have thought in creating a new user account and install this outdated software on this account, bulkheading my standard mate user account that is perfectly tuned, as I said.

My problem is that when I created the new user account, all the software of my old account is also available to the new account, so I am scared that if I modify the software versions on the new user account, the old account will also suffer these modifications...

Is there any way of completely  separating the software versions between the two accounts? I mean creating the new user account as a fresh software installation, completely independent from the old user account so two users can have different software or different versions?

Thanks again for your help and brgds.

---

### Post by TheFu on 2017-09-30
Yes, but not using the normal tools.  APT is system-wide.

I would probably just create a virtual machine with an older version of Ubuntu-whatever running, then install the exact packages required and pin those in the package manager.  I'd also create a VM snapshot, so if anything did get updated, going back would be trivial.

There might be better methods, but that is what I'd do.

---

