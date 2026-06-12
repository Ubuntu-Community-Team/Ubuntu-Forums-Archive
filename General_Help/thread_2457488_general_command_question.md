---
title: "general command question"
date: 2021-02-03
forum: General Help
---

### Post by cmcanulty on 2021-02-03
I made this alias to do updates, upgrades & clean easily. My question is why is the -S needed after every sudo? If I remove the -S after each sudo it fails.

```
alias uc='sudo -S apt-get update; sudo -S apt-get upgrade -y; sudo -S apt-get dist-upgrade -y; sudo -S apt-get autoremove -y; sudo -S apt-get autoclean -y'
```

---

### Post by dinkidonk on 2021-02-03
You could try to use "su" instead of "sudo", og have "sudo" run multiple commands like this:

```
sudo sh -c "date; uname"
```

---

