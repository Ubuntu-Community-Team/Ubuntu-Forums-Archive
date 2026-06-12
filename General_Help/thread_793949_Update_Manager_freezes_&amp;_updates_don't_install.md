---
title: "Update Manager freezes &amp; updates don't install"
date: 2008-05-14
forum: General Help
---

### Post by birdySi on 2008-05-14
I've recently updated Ubuntu to 8.04. Since first day every update I do over Update Manager doesn't update. Update Manager "freezes" and doesn't do any update. After that I use commands:

sudo apt-get update
sudo apt-get upgrade

If I rerun upgrade I got message:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  libqt4-core libqt4-gui libqt4-sql openssh-client openssh-server ssl-cert
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.

And in Update Manager I have still 19 updates which aren't installed.

I have even tried 
sudo apt-get clean
sudo apt-get purge
sudo apt-get check

Sill the same result. 

Please help me solve this problem. Tnx.

---

### Post by birdySi on 2008-05-14
Just in this minute I also realized that if I press Preferences on top Panel on Update Manager icon nothing appears. In bottom Panel apears new tab with title "Starting Administration" and after few seconds tab disapears and nothing happens...

---

### Post by jon_herr on 2008-05-14
Update manager doesn't freeze for me... but the same packages have been kept back:

 openssh-client openssh-server ssl-cert

Which concerns me since they are known to have a security vulnerability...

Jon

---

### Post by jon_herr on 2008-05-14
Fixed it...
Instead of using 
apt-get upgrade

use
apt-get dist-upgrade

Then the ssl stuff and others will be brought up to date.

---

### Post by birdySi on 2008-05-15
Thanks Jon, this helped me empty list in update manager.

But I have still one problem. When I start Update Manager and then press Check button nothing happens. I even wait for whole night and still Update Manager becomes gray and freezes. I must use kill command to close Update Manager.

---

### Post by sissn on 2008-05-15
I had the same problem but found this fix!

Worked fine for me!

> **brown705 said:**
> I was having the same problem myself, but I just found the answer at the bottom of this thread:

[https://answers.launchpad.net/ubuntu/+question/29446](https://answers.launchpad.net/ubuntu/+question/29446)

For your reference, I'll paste the post with the fix from the launchpad.net forum here:

[QUOTE=brown705;4895802]
SwissMike said on 2008-04-18:

Problem solved.

Turns out that the localhost setting in /etc/hosts was incorrect. The fix is going to menu ' System', then 'Administration', then 'Network'. Select the tab Hosts, enter password in dialog box, then change the localhost name:

127.0.0.1 PCName.networkName

to

127.0.0.1 PCName

and save it. Done. Whole problem gone. Interestingly, Bug #195308 confirms the same problem. Hope this small issue gets fixed before the Apr 21 release as it was nasty while it lasted.

Greetings from Switzerland,
Mike. 

Worked for me! \\:D/

Michael[/QUOTE]

---

### Post by birdySi on 2008-05-15
Thanks sissn,

I resolved problem. The problem was indeed in /etc/hosts

---

### Post by CJ_Hudson on 2008-05-15
Greeno here. Yep thanks, had same problem and that's fixed it!

---

