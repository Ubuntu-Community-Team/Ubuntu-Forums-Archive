---
title: "systemd-coredump vs core-dump-handler for application dependency issue"
date: 2022-10-07
forum: General Help
---

### Post by idiealot on 2022-10-07
I'm trying to install a package I had working fine on 20.04 (CML2) which relies on systemd-coredump. I upgraded to 22.04 and since I've upgraded I haven't been able to use CML. I am reinstalling the application and I've come to the point where dpkg reports that CML2 cannot be installed without the systemd-coredump application but when I try to install systemd-coredump I get a failure that systemd-coredump has been replaced with (or conflicts with) core-dump-handler. Am I safe to remove core-dump-handler and replace it with systemd-coredump on 22.04?

---

