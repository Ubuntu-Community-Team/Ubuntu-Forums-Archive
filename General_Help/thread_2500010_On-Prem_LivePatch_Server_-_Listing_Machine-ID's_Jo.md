---
title: "On-Prem LivePatch Server - Listing Machine-ID's Joined to Tier"
date: 2024-08-18
forum: General Help
---

### Post by imanco2 on 2024-08-18
Hello Community,

Having a hard time learning how to identify which machines are associated with a tier? After running the "livepatch-admin report machines prod"   I get[COLOR=#B22222] [B]{}
[/B][/COLOR]
[LIST]
[*]livepatch-admin auth-token xxxxxxxxxxxxxxxxxxxxxxxxx prod
[*]canonical-livepatch status --verbose
[*]canonical-livepatch disable
[*]canonical-livepatch enable xxxxxxxxxxxxxxxx
[*]livepatch-admin auth-token xxxxxxxxxxxxxxx prod
[/LIST]

```
root@livepatch-server:~# livepatch-admin report machines prod
{}

```

```
root@client-machine:~# canonical-livepatch status
last check: 24 minutes ago
kernel: 5.15.0-118.128-generic
server check-in: succeeded
kernel state: &#10003; kernel series 5.15 is covered by Livepatch
patch state: &#10003; no livepatches available for kernel 5.15.0-118.128-generic
tier: prod
machine id: xxxxxxxxxxxxxx


```


Also, how to identify patches applied to a tier? I know patches are initially synced to the "edge" tier. Identify new patches (22.04 and 20.04) and promote those to the "prod" tier.

The commands I know:   [I]ls -1 /var/snap/canonical-livepatch-server/common/patches/|wc -l    and     livepatch-admin sync reports |wc -l
[/I]
  1.  How can I tell the amount of patches applied to a specific tier? (edge or prod)
  2.  How can I tell which patches (22.04 and 20.04 kernel patches) are new vs. old, before I promote from edge to prod tier? (so I'm not blindly promoting)

Thank you very much in advance!

---

### Post by #&amp;thj^% on 2024-08-18
You can only view any active machine/s count through the Ubuntu Pro Dashboard for each subscription to Ubuntu Pro. This gives the number of online machines attached to your Pro token that have pinged Canonical Servers within the last 24 hours. If a machine is detached from your token the reduction in active machine count will not be seen for 24 hours until 24 hours later.
Info: [https://documentation.ubuntu.com/pro/active-machines/](https://documentation.ubuntu.com/pro/active-machines/)

---

### Post by imanco2 on 2024-08-18
I need to install on-prem landscape in order to see each machine?

Will landscape show the machine-ID associated with its tier?

---

### Post by deadflowr on 2024-08-19
Does this help?
[https://ubuntu.com/security/livepatch/docs/livepatch_on_prem/reference/patch_management](https://ubuntu.com/security/livepatch/docs/livepatch_on_prem/reference/patch_management)

I expect you already read that...

---

### Post by imanco2 on 2024-08-19
Yes read that article. Good info on patch promotions. But still clueless how to see which patches are applied to a tier.

I cannot figure out the right command.

(also, installing on-prem landscape in hopes of seeing which machine-id's are associated with a given tier)

---

### Post by imanco2 on 2024-08-19
I've installed on-prem landscape and do not see association of machine-id to tiers.

Does anyone know the proper commands to run on the on-prem livepatch server to view patch levels per tier and machine-id association?

---

### Post by imanco2 on 2024-08-22
Update....

Figured it out

This should be documented on the Ubuntu livepatching guide.

I was able to see machine ID's assiciated with a tier after running all these commands (not sure which helped, so you should try one-by-one)


[LIST]
[*]snap set canonical-livepatch-server     lp.machine-reports.database.enabled=true     lp.machine-reports.database.retention-days=30     lp.machine-reports.database.cleanup-row-limit=1000     lp.machine-reports.database.cleanup-interval="6h"
[*]snap install landscape-api
[*]add-apt-repository ppa:landscape/self-hosted-24.04 -y
[*]apt update
[*]apt full-upgrade
[*]apt update && sudo apt install ubuntu-advantage-tools (dont know if this is necessary, but I ran anyways)
[*]pro enable (dont know if this is necessary, but I ran anyways)
[/LIST]

[LIST]
[*]rebooted
[/LIST]

Now I can run this command to see which machines are attached to a tier: 
        livepatch-admin report machines prod


Also, to show the patches applied to a tier, here are 2 commands I use for checking the latest 22.04 and 20.04 amd64 patches in that tier.

Show patches of tier: 
    livepatch-admin tier patches edge |grep livepatch-5.4.0-18 |grep generic |sort
    livepatch-admin tier patches edge |grep livepatch-5.15.0-11 |grep generic |sort


Show counts of patches per tier:
    livepatch-admin tier patches edge |grep 5.4.0-18 |wc -l
    livepatch-admin tier patches edge |grep 5.15.0-11 |wc -l

Now I can compare latest patches applied to the default "edge" tier and promote to the "dev" tier.

Here's my plan to rollout/promote
1. Check patch count applied to edge tier
2. Check patch count applied to dev tier
3. Compare, if edge has more patches, then need to promote to your next tier (in my case, dev tier)
4. Promote all from edge to dev tier.

Hope this helps others going through poor livepatch documentation

---

