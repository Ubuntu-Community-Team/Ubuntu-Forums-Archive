---
title: "CLI tool to manage services?"
date: 2008-06-07
forum: General Help
---

### Post by daihard on 2008-06-07
Hi.

I did a bit of googling myself but could not find the answer, so here goes...

I am using Kubuntu 8.04 (Hardy Heron). I am looking for a CLI tool that lets me manage services, including turning on/off each service on different runlevels, showing the list of currently installed services, etc. For those familiar with Red Hat, it would be the equivalent of their "chkconfig" tool.

I **did** find the tool named "sysvconfig," but it uses pseudo-GUI and does not seem to handle different runlevels.

Any feedback would be appreciated.

TIA,
Dai

---

### Post by HalPomeranz on 2008-06-07
There's a tool called update-rc.d that does some of what chkconfig does, but not all.  chckconfig is the one thing I really miss from Red Hat.

You might also be interested in the following document, which was a lot of help to me as I migrated from Red Hat to Debian:

[https://help.ubuntu.com/community/SwitchingToUbuntu/FromLinux/RedHatEnterpriseLinuxAndFedora](https://help.ubuntu.com/community/SwitchingToUbuntu/FromLinux/RedHatEnterpriseLinuxAndFedora)

---

