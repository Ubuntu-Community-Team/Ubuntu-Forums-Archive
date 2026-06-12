---
title: "How to find &amp; verify the strong keys for PPAs?"
date: 2024-05-24
forum: General Help
---

### Post by &amp;KyT$0P# on 2024-05-24
Just ran across [this]("https://discourse.ubuntu.com/t/new-requirements-for-apt-repository-signing-in-24-04/42854").  Although I am using 22.04 and have no plans to upgrade to 24.04, I think it would be wise to abide this anyway if possible, given how much an Ubuntu system's security hinges on these keys.

So checked all APT keys on this system, and found [FONT=monospace]rsa1024[/FONT] keys are being used for two Launchpad PPAs.  Seems per [this bug]("https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/2065932") that although Launchpad PPAs using [FONT=monospace]rsa1024[/FONT] key should be dual-signed with a strong key, there is not (yet) any straightforward way to change to the strong key (and that bug is about 24.04, so it's not clear whether fix for that bug would be released to 22.04).  I know how to manually replace the keys in my system, but that requires knowing what the strong keys are.  One of the PPAs in my case is [official SMPlayer PPA]("https://launchpad.net/~rvm/+archive/ubuntu/smplayer"), but I can only find mention of its [FONT=monospace]rsa1024[/FONT] key?

How to find the strong key for a Launchpad PPA such that can be sure of the key's authenticity?

---

### Post by currentshaft on 2024-05-24
vvv

---

### Post by &amp;KyT$0P# on 2024-05-25
> **currentshaft said:**
> You'll have to ask the developer to upgrade their signing key.

Quoting from the Ubuntu Discourse link -
> A PPA on Launchpad triggers a “weak algorithm” warning, what do I do?

PPAs are currently in the process of being upgraded to a 4096-bit RSA key ... No action is needed (or possible) from PPA owners.

> the risk of someone compromising you by factoring a RSA-1024 private key is relatively low to other infosec vulnerabilities. I really would not worry about it.

Thanks, sounds like fixing this is not urgent.  Maybe the strong keys will become listed after just waiting for more of the PPA migrations have completed.

---

### Post by &amp;KyT$0P# on 2024-07-31
> **halogen2 said:**
> One of the PPAs in my case is [official SMPlayer PPA]("https://launchpad.net/~rvm/+archive/ubuntu/smplayer"), but I can only find mention of its [FONT=monospace]rsa1024[/FONT] key?

Now that page is listing only a rsa4096 key.

Upgrading each PPA to the strong key only requires deleting the key and re-adding the PPA.  For example for the aforementioned SMPlayer PPA:
```
sudo rm -v /etc/apt/trusted.gpg.d/rvm-ubuntu-smplayer.gpg*
sudo add-apt-repository -n ppa:rvm/smplayer
```
And can verify the added key by checking that its fingerprint matches the one listed on the PPA's Launchpad page.

---

