---
title: "Installing svk from CPAN, not Ubuntu Repositories"
date: 2005-04-25
forum: General Help
---

### Post by Levander on 2005-04-25
Am wondering if anybody's got experience installing svk from CPAN and not the Ubuntu repositories?  Apparently, svk is one of the programs that currently evolving rapidly and emerging out of an alpha state.  0.26 in hoary, 0.991 in CPAN.

Part of my problem is that I've already installed svk v.026 from the repositories.  And, I remember when I installed it, it installed a *lot* of perl modules as dependencies.  And, since I have no experience with CPAN, I'm wondering if I uninstall svk and all the perl modules via apt-get (checking that its okay first with deborphan), I'm wondering if CPAN will "auto-reinstall" all these dependencies?

Or, do I need to leave all these perl modules on my system that I installed from apt-get, and just remove the svk package itself?  Just don't know if cpan will go and install all these dependent modules for me or not.

Also, when I run cpan from the command line for the "cpan svk", do I need to sudo that command?

---

