---
title: "Software Center issues"
date: 2015-08-11
forum: General Help
---

### Post by liam25 on 2015-08-11
Hi guys , just some random issues about the software center here.
Whenever i open the software center , it crashes after loading for a few seconds.
Whenever i type 'sudo apt-get autoclean' in terminal , it prompts me these errors :

E: Could not open lock file /var/cache/apt/archives/lock - open (2: No such file or directory)
E: Unable to lock the download directory

Then i have to type in 'sudo apt-get install --reinstall software-center' .
Strange , everything works now include the 'sudo apt-get autoclean' .
I have to repeat this everytime i restart pc , any help will be appreciated :)

---

### Post by liam25 on 2015-08-12
I fixed it by unmounting /var/cache to tmpfs :KS

---

