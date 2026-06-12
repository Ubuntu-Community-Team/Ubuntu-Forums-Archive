---
title: "Ubuntu Pro also for 32bit 18.04?"
date: 2023-04-08
forum: General Help
---

### Post by a.borque on 2023-04-08
Hello!
On an older machine I am still running a 32bit version of 18.04(.06).
This is going to drop out of support soon unless I can enable Ubuntu Pro for it.
On the other hand I have read that Ubuntu Pro is only available for 64bit version on x86 and ARM.
So, can I extend updates for my 32bit 18.04 until 2028 as promised somewhere else with Ubuntu Pro, or not.
Thanks for a reply and clarification!
A.Borque
PS: Going onto a 64bit version is no option and no valid answer here unless there is a better way to do this than setting up the system all new!

---

### Post by ian-weisser on 2023-04-08
Ubuntu Pro questions should be asked to the Pro sales team, whom we are not. We are your fellow users, not Canonical employees. We have no special insight into the proprietary product called Ubuntu Pro.

So I asked Google for you:

Source: [https://ubuntu.com/legal/ubuntu-pro-description](https://ubuntu.com/legal/ubuntu-pro-description)

> 
Security and Compliance 
1. Expanded Security Maintenance (ESM)
       [...]
1.4 ESM does not provide:
1.4.1 Coverage for architectures other than 64-bit x86 AMD/Intel for Ubuntu releases 14.04 LTS, 16.04 LTS 


Support Exclusions
[...]
2. Ubuntu Pro Desktop support does not provide:
[...]
2.4 Support for architectures other than x86_64


Your 32-bit architecture seems NOT promised to receive security updates nor desktop support.

---

### Post by MAFoElffen on 2023-04-08
...and talking with the Canonical "Ubuntu Pro" Team when I tested this for the "Ubuntu Forum Members" Subscription, it is not available for arch ARMxx at all. Even though the packages are in the Ports Repo (and will install on arm64), trying to add support for anything (after the install) fails, because that program does not support that arch.

 I know that doesn't make sense to me either. Why bother to port the packages to something they do not support? All I could figure out for that, is that it leaves that as a future possibility, if they ever decide to offer that.

So from what they told me, Ubuntu Pro is only available for arch amd64.

---

