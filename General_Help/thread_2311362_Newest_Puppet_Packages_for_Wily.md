---
title: "Newest Puppet Packages for Wily"
date: 2016-01-26
forum: General Help
---

### Post by Brando569 on 2016-01-26
I'm trying to get re-acclimated with Ubuntu since I'm looking for DevOps/SysAdmin jobs and most places either only use Fedora/RedHat or Ubuntu, neither of which I prefer over Arch. Now I'm starting to remember why I ditched the Debian-based distros and jumped ship to Arch and never looked back. 

I'm trying to install a puppet master on my Ubuntu VM (already setup my LAMP stack and other things, so I can't really just start over with a fresh install) and after downloading and doing the initial configurations I was wondering why my Arch puppet agent wasn't talking with my puppet agent. The passenger site on my master kept saying **The environment must be purely alphanumeric, not ''** I had no idea what that meant so I just kept going, after issuing the test command on the agent I got this:

**Error: Could not request certificate: Error 400 on SERVER: The environment must be purely alphanumeric, not 'puppet-ca'** 

which was slightly more verbose than the error from the passenger site. After some more searching I found out that the error is caused by the master version being below the agent version. Apparently my master version in Ubuntu is 3.7.2 and the agent version in Arch is 4.3.1!! So the Ubuntu package is severely out of date and I looked at the PuppetLabs website and they have their deb packages to add their repos but there is nothing that I can see for Wily Werewolf! Is it even possible to get the newest packages without having to manually install it?

---

### Post by QDR06VV9 on 2016-01-26
I know what you mean with Arch just love it..
But back to you..See if you can make sense of this [https://docs.puppetlabs.com/puppet/latest/reference/upgrade_major_server.html](https://docs.puppetlabs.com/puppet/latest/reference/upgrade_major_server.html)

---

### Post by Brando569 on 2016-01-26
I don't think that will work since it says you have to upgrade the way you launch the master to puppetserver...which is in their repository :( I'm currently using passenger with Apache.

---

### Post by Brando569 on 2016-01-26
I ended up just creating a new vm with 14.04 on it and installed Puppet Enterprise on it.

---

