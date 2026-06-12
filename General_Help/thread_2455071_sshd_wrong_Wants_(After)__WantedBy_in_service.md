---
title: "sshd wrong Wants (After) / WantedBy in service?"
date: 2020-12-11
forum: General Help
---

### Post by jetojedno on 2020-12-11
sshd's service definition says [FONT=courier new][COLOR=#000000]WantedBy=multi-user.target[/COLOR][/FONT] and it's pre-condition is [FONT=courier new][COLOR=#000000]After=network.target auditd.service[/COLOR][/FONT][COLOR=#000000][FONT=Menlo].  Both seem wrong to me, for different reasons.

It seems to me that sshd is a multi-user program so it should have [/FONT][/COLOR][FONT=courier new][COLOR=#000000]Wants=multi-user.target[/COLOR][/FONT][COLOR=#000000][FONT=Menlo] (or [FONT=courier new]After=[/FONT]) rather than [/FONT][/COLOR][FONT=courier new][COLOR=#000000]WantedBy=multi-user.target[/COLOR][/FONT].

Secondly, [FONT=courier new][COLOR=#000000]After=network.target[/COLOR][/FONT] starts sshd too early (as the network isn't up) so it fails if sshd is configured to listen on a single if / ip address rather than all and everywhere.  This is common for multi-NIC computers, where one (or more) of the NICs is used for special purposes, such as a service end-point.  This should, I think, be [FONT=courier new]After=[COLOR=#CA3323]**network**[/COLOR][COLOR=#000000]-online.target auditd.service[/COLOR][/FONT].

Am I missing something or not understanding why it's set up like this?

Thanks
David

---

