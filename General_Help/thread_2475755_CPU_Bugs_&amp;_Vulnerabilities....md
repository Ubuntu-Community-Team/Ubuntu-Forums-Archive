---
title: "CPU Bugs &amp; Vulnerabilities..."
date: 2022-06-07
forum: General Help
---

### Post by wyattwhiteeagle on 2022-06-07
I ran these two commands and found these.
I'm wondering what is the order of importance in dealing with these?
What can be done to secure the vulnerabilities and remove the bugs?

Please remember I don't have the money to just buy a new processor, motherboard, or a new laptop.

tac /proc/cpuinfo
```
bugs        : cpu_meltdown spectre_v1 spectre_v2 spec_store_bypass l1tf mds swapgs itlb_multihit
```
lscpu
```
Vulnerability Itlb multihit:     KVM: Mitigation: VMX disabled
Vulnerability L1tf:              Mitigation; PTE Inversion; VMX EPT disabled
Vulnerability Mds:               Vulnerable: Clear CPU buffers attempted, no microcode; SMT disabled
Vulnerability Meltdown:          Mitigation; PTI
Vulnerability Spec store bypass: Vulnerable
Vulnerability Spectre v1:        Mitigation; usercopy/swapgs barriers and __user pointer sanitization
Vulnerability Spectre v2:        Mitigation; Retpolines, STIBP disabled, RSB filling
Vulnerability Srbds:             Not affected
Vulnerability Tsx async abort:   Not affected

```

---

### Post by Doug S on 2022-06-07
Several of your bugs have mitigations in place. Only 2 show as vulnerable:

```

Vulnerability Mds:               Vulnerable: Clear CPU buffers attempted, no microcode; SMT disabled
Vulnerability Spec store bypass: Vulnerable

```

My 20.04.4 test server shows:

```
Vulnerability Itlb multihit:     KVM: Mitigation: VMX disabled
Vulnerability L1tf:              Not affected
Vulnerability Mds:               Not affected
Vulnerability Meltdown:          Not affected
Vulnerability Spec store bypass: Mitigation; Speculative Store Bypass disabled via prctl
Vulnerability Spectre v1:        Mitigation; usercopy/swapgs barriers and __user pointer sanitization
Vulnerability Spectre v2:        Mitigation; Enhanced IBRS, IBPB conditional, RSB filling
Vulnerability Srbds:             Not affected
Vulnerability Tsx async abort:   Not affected
```

But my main debian 11.3 server shows:

```
Vulnerability Itlb multihit:     KVM: Mitigation: Split huge pages
Vulnerability L1tf:              Mitigation; PTE Inversion; VMX conditional cache flushes, SMT vulnerable
Vulnerability Mds:               [COLOR="#FF0000"]Vulnerable: Clear CPU buffers attempted, no microcode; SMT vulnerable[/COLOR]
Vulnerability Meltdown:          Mitigation; PTI
Vulnerability Spec store bypass: [COLOR="#FF0000"]Vulnerable[/COLOR]
Vulnerability Spectre v1:        Mitigation; usercopy/swapgs barriers and __user pointer sanitization
Vulnerability Spectre v2:        Mitigation; Full generic retpoline, STIBP disabled, RSB filling
Vulnerability Tsx async abort:   Not affected
```

So, I am interested in your question.

---

### Post by TheFu on 2022-06-07
Well, all the code is available, so you could learn the language(s) used for the specific bugs and fix them, then submit 'pull requests' back to the project team for the code where the bugs exist.  Of course, many of these bugs weren't seen by experts, so the chance that you or I will be correctly fixing any is extremely tiny.

Some projects have already provided mitigations. Enable those.  How is spelled out all over google links.  The mitigations almost always have performance impacts. Some are 1% and some have been shown to be 30%.  Only you can decide if the security matters sufficiently for any single mitigation to be worth the mitigation or not.  For me, I've left all the defaults as they were.  Most systems here don't have any end-users, so the chances that a nasty end-user will be able to take advantage of a firmware issue in a CPU is even smaller than my ability to find and correct the code issue.  That's my judgement. You may come to a different judgement.

As for a remote attacker taking advantage of these bugs, there are thousands of other, more likely, issues to be concerned about first. That's also in my judgement and your judgement will likely be different on that too.

If I were running sensitive data processing on cloudy services where I didn't know who all the peer people were on the say physical system, then my judgement would be different and these CPU attack methods between different VMs would matter more to me.

---

### Post by wyattwhiteeagle on 2022-06-07
My main concerns are performance, stability, and security.

With me being an end-user with limited experience in Linux and linux-based...
I believe I am more of a danger to myself than a nasty remote predator.

In my experiences, the securities, mitigations, and vulnerabilities can have impacts on performance.
As you pointed out, it's up to the user to determine which ones are worth using.

Do my current cpu vulnerabilities/mitigations mean the machine is unstable or lacking in performance?

---

### Post by Doug S on 2022-06-07
> **wyattwhiteeagle said:**
> Do my current cpu vulnerabilities/mitigations mean the machine is unstable or lacking in performance?Unstable, no. Performance, yes some. It has been too long since I did specific tests on cost of performance for mitigations, so I would have to re-test to give current information. The performance degradation is also workflow dependant.

@TheFu: Thanks for your input. I suspect my Debian server is O.K. but will do some homework to be sure. I am the only user, and since I no longer travel for work, external SSH is disabled .

---

### Post by TheFu on 2022-06-07
Most of the recent CPU mitigations disable things related to opportunistic instruction paths and hyperthreading, so there are definitely performance aspects.  As Doug points out, those impacts are very workload dependent.  DBs have typically been hit the hardest. Most end-users wouldn't run into DB related CPU impacts, at least not to any important level.

As with most answers, try it. See what's different in your workloads and systems, then decide. Nobody else uses their computer in exactly the same way you do.

The CPU issues don't concern me in the least. My main concern is that I'll click on a website or have an email attachment full of phishing stuff that infects my system and all network storage with malware.  I think that's the most likely thing to happen for most users.  After the malware is running, it really can't be cleaned. Wipe and start fresh are the only answers - computer-wide.  If you have a dual-boot system, infection on the Linux side can easily jump to the Windows side if that storage is mounted too.  Or to a network storage device.  Windows malware will get local storage and any remote storage, mainly CIFS/Samba, but anything that is mounted - perhaps DFS or AFS too.

I have almost zero concern about remote VPN or remote ssh being allowed, since those are both setup to allow key-only access and I use IPs, not DNS when I'm in parts of the world where the DNS cannot be trusted. Of course, there are plenty of other caveats for remote access.  None of those are related to the CPU bugs, to my knowledge.

And keep your routers and wifi-APs patched. If it has been more than 2 months since the last patch, check now.  My WAN router gets updates every few weeks, usually related to the webapp used to manage it, not the core OS or underlying admin CLI tools, but once a month or so, one of those underlying things gets updated too.  I forgot to patch last Friday night, so I'm patching now.  17 updates.  IPSec, sqlite, python 3.8 (and a few related packages), php-radius, SASL libs, glib, curl ... basically, there are always router updates. Always.

---

### Post by wyattwhiteeagle on 2022-06-07
I found this...
[https://forums.gentoo.org/viewtopic-p-8592765.html?sid=06badfdada90b6f184ffd7586fbfca4a](https://forums.gentoo.org/viewtopic-p-8592765.html?sid=06badfdada90b6f184ffd7586fbfca4a)

It's in French and I don't know exactly how accurate Google Translate is.

The linked forum thread seems to deal with the cpu mds microcode issue.
It seems to suggest integrating the updated microcode and thus mitigating some or all of the cpu vulnerabilities.

I haven't tried it on my machine as I'm not sure how to integrate something like this.

---

### Post by TheFu on 2022-06-08
The firmware for the CPU is included with the specific kernel and the defaults are setup when the kernel was compiled by whoever compiled the kernel (typically Canonical).  To override those defaults, I'd expect either settings in  sysctl.conf  or /etc/sysctl.d/ OR grub parameters passed in during boot, but I don't know. Haven't changed the default mitigation settings myself.

---

