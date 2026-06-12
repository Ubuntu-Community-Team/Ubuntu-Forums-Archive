---
title: "How do I FULLY upgrade my system?"
date: 2017-10-31
forum: General Help
---

### Post by 1jarwolf on 2017-10-31
I forget the command but it is not apt-get upgrade or apt-get dist-upgrade...?

I am currently running Ubuntu 16.04.3 LTS

---

### Post by 1jarwolf on 2017-10-31
UPDATE: I believe I have found the answer after multiple google searches.

[COLOR=#ff0000][U][I][B]sudo do-release-upgrade


      [/B][/I][/U][/COLOR]UPDATE: I have changed this back to un solved as this command said no new updates were available. I am currently at 16.04 Xubuntu, meaning, there should be an update for 17.04 zesty for Xubuntu, right? If so, how would I install it?

---

### Post by cc1984 on 2017-10-31
I may be wrong but I suspect the issue is that you are attempting to upgrade from an LTS version to a short term version. Apparently you can upgrade but according to [this article]("http://www.omgubuntu.co.uk/2017/10/upgrade-to-ubuntu-17-10") you will need to opt in. Depending on how you use your system you may or may not want to migrate away from the current LTS version.

---

### Post by cc1984 on 2017-10-31
Of course if you do attempt to upgrade please back up your data.

---

### Post by Tadaen_Sylvermane on 2017-10-31
Edit /etc/update-manager/release-upgrades as needed. It tells you what to do.

---

### Post by mörgæs on 2017-10-31
Is this concerning your newly bought computer from the other thread? 

If yes then don't upgrade. Install the version you prefer and stay with it until support runs out. After that a new, fresh install.

---

### Post by 1jarwolf on 2017-10-31
Alright. There's a new upgrade every two years for LTS right? Also, as a LTS OS, what are the advantages other than I would imagine constant upgrades to the system through out time as to where non LTS is just an update and that's it?

---

### Post by 1jarwolf on 2017-11-01
Well....I went to upgrade it just for the heck of it, it then rebooted, showed that xubuntu screen, and then went to a black screen with a little flashing dash. So pissed. I am thankful that I didn't delete those files that were on my USB as it was in the trash can on my other laptop still lol lol.

---

### Post by sudodus on 2017-11-01
> **mörgæs said:**
> Is this concerning your newly bought computer from the other thread? 

If yes then don't upgrade. Install the version you prefer and stay with it until support runs out. After that a new, fresh install.
+1

---

### Post by C.S.Cameron on 2017-11-01
And then rsync home folder?

---

### Post by mörgæs on 2017-11-01
I prefer to delete /home with all config files in it, keeping only my user files. 

After half a years experiments here and there my config files are not worth recycling.

---

### Post by ian-weisser on 2017-11-01
> **1jarwolf said:**
> Alright. There's a new upgrade every two years for LTS right?

Yes. Be careful with your language: 'upgrade' vs 'release-upgrade'. They are different.

> **1jarwolf said:**
> Also, as a LTS OS, what are the advantages other than I would imagine constant upgrades to the system through out time as to where non LTS is just an update and that's it?

It depends upon what you care about:
If you care about new features and updated software, then LTS is a terrible choice.
If you care about stable APIs/ABIs for your enterprise applications and workflow, then normal Ubuntu (non-LTS) is a terrible choice.
Both are patched for security vulnerabilities at the same time.

---

