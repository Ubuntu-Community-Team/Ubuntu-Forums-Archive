---
title: "not work update manager in ubuntu 12.04"
date: 2013-02-05
forum: General Help
---

### Post by psarunkumar on 2013-02-05
hi,

anyone help me how update software in Ubuntu 12.04?
i attached screenshot.

---

### Post by snowpine on 2013-02-05
It looks like maybe you have mixed-up software sources of 10.04 lucid and 12.04 precise?

```
cat /etc/apt/sources.list
```

---

### Post by grahammechanical on 2013-02-05
So, you have followed the advice to run the command

```
sudo apt-get install -f
```

that is good. What is now the problem? Have you tried to run Software Updater from the Power/Cog menu? What happens? What error messages do you get?

Regards.

---

