---
title: "How to clean out ufw (firewall) settings?"
date: 2008-05-14
forum: General Help
---

### Post by abcuser on 2008-05-14
Hi,
I have turned on firewall and set default deny policy:
sudo ufw enable
sudo ufw default deny

I can see that a lot of settings have been done:
sudo iptables -L

If I disable firewall:
sudo ufw disable
then iptables shows no settings.

So far so good, but when I turn on firewall again:
sudo ufw enable
all settings preserves. This is good.

I know I can use delete rule command to delete one rule, but how to clean (delete) out all rules created by command "sudo ufw default deny"?
Thanks,
Abcuser

---

