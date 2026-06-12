---
title: "Fresh install Ubuntu 20.04 ignoring automatic login configuration"
date: 2022-01-20
forum: General Help
---

### Post by wb0gaz on 2022-01-20
On a fresh install of Ubuntu 20.04 into an empty partition, automatic login is failing to cooperate.

Settings > Users shows Automatic Login toggle to the right (enabled)

In an attempt to fix this, in

/etc/gdm3/custom.conf

Added

AutomaticLoginEnable=true
AutomaticLogin=(user name)

Still at boot-up the login screen appears.

How do I get Ubuntu 20.04 to perform automatic login?

I realize this is not preferred in some circles, however, for a machine physically tied to a single user in a closed environment, automatic log-in is a convenience I sorely miss.

Thank you for any advice, requests for clarification, questions, or other assistance in troubleshooting.

---

