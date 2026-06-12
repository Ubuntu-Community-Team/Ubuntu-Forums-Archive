---
title: "Live patch is not working."
date: 2023-11-08
forum: General Help
---

### Post by laxmidhar on 2023-11-08
Hai,
I am using a HP probook which has 16GB RAM 512GB SSD Rayzen 7 series processor and installed Ubuntu 22.04 LTS. I am facing two problem.
1. Live patch is not working, Itried below code but still no change also not getting the green shield logo in the top bar.
```
sudo ua enable livepatch
[sudo] password for laxmidhar: 
One moment, checking your subscription first
Stderr: internal error, please report: running "canonical-livepatch" failed: cannot find installed snap "canonical-livepatch" at revision 246: missing file /snap/canonical-livepatch/246/meta/snap.yaml


Stdout: 
Unable to configure Livepatch: Failed running command '/snap/bin/canonical-livepatch config remote-server=https://livepatch.canonical.com' [exit(46)]. Message: internal error, please report: running "canonical-livepatch" failed: cannot find installed snap "canonical-livepatch" at revision 246: missing file /snap/canonical-livepatch/246/meta/snap.yaml


ERROR: Unable to configure Livepatch: Failed running command '/snap/bin/canonical-livepatch config remote-server=https://livepatch.canonical.com' [exit(46)]. Message: internal error, please report: running "canonical-livepatch" failed: cannot find installed snap "canonical-livepatch" at revision 246: missing file /snap/canonical-livepatch/246/meta/snap.yaml

```

```
sudo ua status
[sudo] password for laxmidhar: 
SERVICE          ENTITLED  STATUS    DESCRIPTION
anbox-cloud      yes       disabled  Scalable Android in the cloud
esm-apps         yes       enabled   Expanded Security Maintenance for Applications
esm-infra        yes       enabled   Expanded Security Maintenance for Infrastructure
livepatch        yes       disabled  Canonical Livepatch service
realtime-kernel* yes       disabled  Ubuntu kernel with PREEMPT_RT patches integrated
usg              yes       disabled  Security compliance and audit tools


 * Service has variants


For a list of all Ubuntu Pro services and variants, run 'pro status --all'
Enable services with: pro enable <service>


     Account: laxmidhar530@outlook.com
Subscription: Ubuntu Pro - free personal subscription

```

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293031&stc=1[/IMG]

2. Getting Invalid config param 0014 while booting the device. Just wanted to know what and where is the issue.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293032&stc=1[/IMG]

Thanks and regards,
Laxmidhar

---

