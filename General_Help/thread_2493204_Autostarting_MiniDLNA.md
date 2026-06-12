---
title: "Autostarting MiniDLNA?"
date: 2023-12-06
forum: General Help
---

### Post by KDMerrill on 2023-12-06
When I restart my Ubuntu box after software updates, my miniDLNA never seems to auto-restart, and I have to manually issue these commands:

    minidlnad -R
    sudo service minidlna start

What do I need to do to have this happen automatically after a restart?

Kevin in VA

---

### Post by madscientist032 on 2023-12-06
IMHO best way to approach this is to leverage [FONT=courier new][COLOR=red]systemctl[/color][/font] via the following command.

```

sudo systemctl enable minidlna.service

```

EDIT: the original advice (stubbing in a crontab entry) I proposed was not favorable and should not be used. Systemctl is a better solution.

---

### Post by KDMerrill on 2023-12-07
Thanks!

---

