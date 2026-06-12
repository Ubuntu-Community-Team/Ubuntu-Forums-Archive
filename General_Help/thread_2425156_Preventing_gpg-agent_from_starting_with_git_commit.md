---
title: "Preventing gpg-agent from starting with git commits/pushes"
date: 2019-08-21
forum: General Help
---

### Post by CaffeineFreeless on 2019-08-21
**Summary:** I want to prevent GPG2's gpg-agent from starting up whenever I sign my git commits. How do I do this?

**Details:**

I have a unique problem that I've nailed down: whenever I sign my git commits, gpg-agent starts up and I can no longer suspend my computer at that point.

To be specific, my computer will stand by, and then force itself out of standby. No amount of cajoling or prayer will get my computer to stay suspended.

This continues until I kill *both* gpg-agent and ssh-agent. Then I can suspend again.

I'm not sure what gpg-agent's relationship is with ssh-agent, because *before* gpg-agent is started, I can suspend no problem even with ssh-agent.

I'm in no mood to spend more time investigating the specifics of why this happens. I have an acceptable workaround and I can do without whatever conveniences gpg-agent offers. How do I prevent that thing from ever running again while still retaining my ability to sign git commits?

---

### Post by haplorrhine on 2019-08-21
Oh god.  I confused SSH with SSL again.

---

