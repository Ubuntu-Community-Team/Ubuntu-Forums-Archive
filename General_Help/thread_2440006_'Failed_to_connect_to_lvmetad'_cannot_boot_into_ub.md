---
title: "'Failed to connect to lvmetad' cannot boot into ubuntu 18.04 VM"
date: 2020-04-04
forum: General Help
---

### Post by lol457745 on 2020-04-04
I am unable to boot into my virtual machine which is running Ubuntu 18.04 on VMWare workstation. The error is produced after entering my Ubuntu disk encryption password and prevents the system from booting.

Pic of the full error (hangs on this screen after correctly entering encryption password): [https://i.imgur.com/S2GXDWX.png](https://i.imgur.com/S2GXDWX.png)

Possible cause might be a full disk but i'm unaware of how i'd go about fixing it, goal is to recover the files on the VM but again not really sure how i'd do that. Any ideas?

---

### Post by HermanAB on 2020-04-28
According to the error message you typed the passphrase wrong.  You may think it is correct, but the system says otherwise.

Are you using a standard US keyboard?  If you are using a foreign (AZERTY for example) keyboard, then you may have trouble typing a password before the correct keyboard map is loaded.

---

