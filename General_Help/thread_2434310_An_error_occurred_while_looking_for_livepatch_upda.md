---
title: "An error occurred while looking for livepatch updates"
date: 2020-01-03
forum: General Help
---

### Post by ubububub on 2020-01-03
Hi,

I have an Asus laptop running Ubuntu 18.04. Everything has been fine so far until recently. 
Every time I log in there is a red shield on Livepatch when it starts. I click on it and get the (greyed out) message "An error occurred while looking for livepatch updates" which I cannot click on. The only way I can get Livepatch to 'be green' again is to go into the settings in Software & Updates and turn it off and on again.
I don't know what's wrong or how to check what the error is. Is there a log I can check or something?

I had Windows 10 on the laptop before I installed Ubuntu over it (because Windows is rubbish and was a lot of trouble) and as I said everything was fine until now. I am not new to Ubuntu either as I had it on a previous laptop a few years ago.

What's wrong?

---

### Post by deadflowr on 2020-01-03
Livepatch runs a check once an hour.
You can look at journal logs for issues.
You might try this one, for instance:
```
journalctl -u snap.canonical-livepatch.canonical-livepatchd | tail -100
```

---

