---
title: "Is there any tui or text box utility for configuring static IP?"
date: 2018-12-16
forum: General Help
---

### Post by blason on 2018-12-16
Hi Team,

Does anyone aware of any utlility like network-tui to configure the static IP? I am creating my customized OS and need to have static IP configured but users might not be techy to configure the same edisting /etc/network/interfaces. Instead thinking if we have any terminal utility for setting IP address?


Thanks and Regards,
Blason

---

### Post by TheFu on 2018-12-16
wicd-curses is one, but don't leave network-manager tools on the machine. It is probably more complex than most end-users would like/understand.

/etc/network/interfaces was deprecated in 17.10 and later, FYI.

If you need to setup static IPs, why not use something like Ansible?

---

