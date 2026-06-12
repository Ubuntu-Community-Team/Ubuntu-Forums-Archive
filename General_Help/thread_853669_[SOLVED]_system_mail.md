---
title: "[SOLVED] system mail"
date: 2008-07-08
forum: General Help
---

### Post by jerome1232 on 2008-07-08
Ok so when I log into a Virtual terminal, it says "you have new mail", how can I check this system mail? furthermore does it have a real use?

---

### Post by iaculallad on 2008-07-08
> **jerome1232 said:**
> Ok so when I log into a Virtual terminal, it says "you have new mail", how can I check this system mail? furthermore does it have a real use?

Install the mailx client first:

```
sudo apt-get install mailx
```

To view your system mails on the terminal:

```
mail
```

It has a real help when you configured your network to report updates, errors, or system functions in to your administrator system mail account.

---

