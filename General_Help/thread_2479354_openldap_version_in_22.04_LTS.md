---
title: "openldap version in 22.04 LTS"
date: 2022-09-22
forum: General Help
---

### Post by nzm96 on 2022-09-22
Hi,

A really 'basic' question that I cannot find an answer for. We have the intention to migrate from RHEL7/openldap to ubuntu 22.04LTS/openldap.

In my testing, I discovered that ubuntu comes with version 2.5.11: fine. However, after some days of testing, I apt upgraded my test system, to discover that now suddenly my openldap has been upgraded to 2.5.13.

So, does ubuntu not use the system like RHEL/debian: one fixed specific openldap version in a certain ubuntu release, and implement security fixes through backports? Ubuntu upgrades to newer upstream versions of openldap?

I did not know that. Does this go for more software in ubuntu? Is there somewhere an overview of this policy, and what packages it applies to?

It 'feels' a bit eary to realise that we will be getting new upstream openldap versions when we regularly update our ubuntu boxes. Am I exaggerating..? It's just not what we're used to see.

Thanks for your insights!

---

### Post by grahammechanical on 2022-09-22
I know nothing about the upgrade policies of Redhat but with Ubuntu the term LTS = Long Term Support = 5 years support. It is customary for Ubuntu LTS desktop versions that a few important applications to be upgraded during this five year support period. I know this applies to Firefox web browser, Thunderbird email client and Libreoffice office suite. There may be others.

I have no familiarity with Ubuntu server but I assume that the same policy applies to certain important programs in Ubuntu server.

Ubuntu LTS versions can also get Extended Security Maintenance (ESM). When this option is taken up the OS get security fixes for another 5 years.

Regards

---

### Post by nzm96 on 2022-09-28
Did not receive a notification of your reply. Sorry, but thanks for the information!
Anyone else with more specific info to share..?

---

### Post by TheFu on 2022-09-28
I wouldn't be surprised if the 3rd level version changes, as that is for bug fixes that don't modify behavior or interfaces.
I would be surprises if 2nd or 1st level version changes happened, except for very specific desktop programs.

BTW, some Canonical server programs are installed as snaps, not using APT.  Snaps get updated without asking, and the snap daemon checks for updates 4x a day, by default.  There are settings to delay this, but it cannot be stopped completely with out external blocking - a firewall.  It is extremely frustrating for admins trying to have a stable platform for our users when snaps can be update as the snapstore decides.  If we wanted that, we'd run MS-Windows, right?

BTW, FreeIPA doesn't have an Ubuntu server, just clients, so you'll want to retain a few RPM-based systems if you use FreeIPA.  I find it a bit embarrassing that Canonical doesn't have a good LDAP-based user management tool shipped with Ubuntu Server. Embarrassing.  The fact that it is easier to join an AD domain than to hook up to a Linux LDAP during desktop installs is also embarrassing for Canonical.

---

