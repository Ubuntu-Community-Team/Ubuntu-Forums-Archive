---
title: "What Exactly Is Ubuntu Pro?"
date: 2024-01-24
forum: General Help
---

### Post by willbetamax on 2024-01-24
Is "Ubuntu Pro" like a special separate "edition" of Ubuntu or just a subscription on top of the normal Ubuntu LTS which grants 5 more years of updates?
I have seen several videos and sites referring to it as a "Premium edition of Ubuntu".

---

### Post by MAFoElffen on 2024-01-24
Ubuntu is Ubuntu.

Ubuntu Pro, is a sort of service subscription. As a User you are qualified to cover 5 machines in Ubuntu Pro.

Even though the doc's say:
> 
Ubuntu Pro is a version of Ubuntu offered by Canonical for public clouds, focused on enterprise and production use. It is based on Ubuntu components but comes with a set of additional services that are activated out of the box. Ubuntu Pro also provides Extended Security Maintenance (ESM).

It is not a "version". What is does is adds things to Ubuntu, such as ESM, which adds repo's for updates for security, etc. So that those kinds of things can be updated for an additional 5 years.

Being it is not functionally anything that can be realistically considered as "another version", it doesn't run any different. It really doesn't make those kinds of changes to the installation.

For commercial paid customers, it adds types of "Support" in a Service contract. There is a difference in free and non-free.

---

### Post by guiverc on 2024-01-24
To me the difference is 

Ubuntu Pro is just Ubuntu, with

- ESM meaning a longer security life of the product, but here I'll suggest read the fine print before you use it; eg. [16.04 ESM for a Desktop system ]("https://wiki.ubuntu.com/SecurityTeam/ESM/16.04")required you to switch some *deb* packages to *snap* in order to still get security fixes.   ESM though is really beneficial for server systems anyway.

- [Ubuntu Security team]("https://wiki.ubuntu.com/SecurityTeam/FAQ") only provide security checks on packages in *main* or *restricted*, as they've always done.  If you have Ubuntu Pro* enabled* though, you can get security fixes for packages found in 'universe', meaning Pro provides additional security that wasn't offered before.

Ubuntu Pro is an *optional extra *as I see it.

---

### Post by willbetamax on 2024-01-24
Thanks everyone.
Now it's much clearer.

---

