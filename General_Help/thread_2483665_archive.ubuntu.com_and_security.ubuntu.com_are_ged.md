---
title: "archive.ubuntu.com and security.ubuntu.com are gedraged"
date: 2023-02-06
forum: General Help
---

### Post by p4sh on 2023-02-06
Dear community,

it looks like archive.ubuntu.com and security.ubuntu.com are degraged, despite the status on the status page.

My "apt-get update" takes more than 10 minutes (from different locations across the world => EU/London, RU/Moscow, KZ, Armenia and other.


Could anyone help to mitigate the issue?

Thanks in advance,
Pasha

---

### Post by ajgreeny on 2023-02-06
Which version of Ubuntu are you using? I hope it is a fully supported version.

Please open a terminal and run command
***sudo apt update***
Copy the output you see in total and paste it back here using Code-tags please.

See my signature below for a How-to if you do not know Code-tags.

---

### Post by p4sh on 2023-02-06
Hi ajgreeny, thanks for reply.
`apt-get update` doesnt fail with error - just facing very slow download for any packages.

There are a plenty of replies in the IRC chat from people facing the same.


regards,
Pasha

---

### Post by ajgreeny on 2023-02-06
Sorry for my misunderstanding!
I am now also seeing this problem with the update command taking many minutes and sometimes telling me that certain repos are not available and have therefore been overlooked or ignored in the following upgrade process.

Like you I have tried changing the location of the repos used from my normal default of UK to the main repos but it didn't help at all.

I suspect that this may be just a temporary problem with access to these repos for some reason that I'm unaware of, but I will search more and come back with any possible answers or information should I find anything that helps.

---

### Post by ajgreeny on 2023-02-06
Well, two hours ago I was, as I said above, having the same problem as you with a very slow and interrupted run of **sudo apt update** but just a few mi utes ago all was running exactly as it normally has in the past; perhaps whatever was going wrong has been put right.

Let's hope that is the situation.

---

### Post by Bashing-om on 2023-02-06
incident history at [https://status.canonical.com](https://status.canonical.com) (further down the page) states that the incident was ack'd at 5pm GMT.

---

### Post by Tadaen_Sylvermane on 2023-02-07
I'm guessing I caught part of this yesterday myself. When trying to do a chroot install and it would just hang endlessly. Then trying to run updates on my Elementary OS install and it would get to X% and just hang. Cancelling and restarting would continue it. I had to cancel and restart half a dozen times to do about 150mb of updates.

---

