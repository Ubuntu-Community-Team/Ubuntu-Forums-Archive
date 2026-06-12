---
title: "Vmware and wireless"
date: 2008-04-12
forum: General Help
---

### Post by john36 on 2008-04-12
I am not quite sure where to post this.
I am running Gutsy on a Thinkpad x60s.

Here's the issue.
When I installed vmware-server it put all the modules into
/lib/modules/2.6.22-14-generic

However I usually boot into
2.6.22-14-386

The problem is my wireless modules (madwifi) are NOT in generic, but only in 386
Therefore if I want to use vmware, I have no wireless.

So, how can I control where Ubuntu puts the modules.  I know I can't copy them from one kernel to the other.

I'll be happy with any  solution, but I'd prefer to have the vmware modules where I usually boot into
2.6.22-14-386

Thanks.

---

### Post by dcstar on 2008-04-12
> **john36 said:**
> I am not quite sure where to post this.
I am running Gutsy on a Thinkpad x60s.

Here's the issue.
When I installed vmware-server it put all the modules into
/lib/modules/2.6.22-14-generic

However I usually boot into
2.6.22-14-386

The problem is my wireless modules (madwifi) are NOT in generic, but only in 386
Therefore if I want to use vmware, I have no wireless.

So, how can I control where Ubuntu puts the modules.  I know I can't copy them from one kernel to the other.

I'll be happy with any  solution, but I'd prefer to have the vmware modules where I usually boot into
2.6.22-14-386

Thanks.

The 386 kernel is for old CPUs, you should be using the generic kernel anyway.

VMware server requires the generic kernel that uses the features of modern CPUs.

---

### Post by john36 on 2008-04-13
Thanks.  That gave me the clue.
I just installed the generic restricted modules and all is good.

---

