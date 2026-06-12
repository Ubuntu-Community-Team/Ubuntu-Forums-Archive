---
title: "TLP does not executed till admin account is loged. Uubuntu 16.04."
date: 2016-06-12
forum: General Help
---

### Post by juan53 on 2016-06-12
Hi

I write this post because I upgrade my laptop to Ubuntu 16.04 and TLP does not work as it should do, I guess. When I start the computer and I go to my daily account, the energy program that laptop follows is the general, as if TLP hadn't start running. Where as, when I go to the admin account, then, TLP starts running and everithing goes normal. If I close the ession with the admin account and I log in the everyday user, TLP also works normally. Is there a solution for this?

I installed the last version by erasing Ubuntu 14.04 from the disk. My laptop is a Dell Latitude 5450 and it operates the system in legacy mode (classic way). I installed TLP from the official repositories of Ubuntu.

Thanks for your time.

---

### Post by Linuxisfast on 2016-06-12
What does tlp-stat show in your daily account. Also what does systemctl status tlp show?

---

### Post by juan53 on 2016-06-12
As far as I know, tlp-stat only can be executed using sudo command and offers a general stadistic of energy usage. How could I get the user stats?

---

### Post by Linuxisfast on 2016-06-12
tlp is a service that runs in background and senses when system is on battery via acpi call. So regardless of which account you are on, it runs and with administrative rights.

---

### Post by juan53 on 2016-06-12
I do apologize for my mistake. Yes, it's true. That's a background service. The reason why started to think that is because the usage rate doesn't drop from 12w in the first few minutes, I started to change the session. But, the behaviour between TLP installed in 14.04 and TLP installed in 16.04 isn't the same. Consumption rate isn't as accurate at the beginning, and the rates maintain high for a while (just 3 minutes or so). Are this changing tension and usage rates healthy for the laptop? Does it need some extra adjustment?  Thanks for reading, and again, sorry for the misunderstanding.

---

