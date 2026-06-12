---
title: "TOTP app that runs in Ubuntu/Xubuntu?"
date: 2020-02-19
forum: General Help
---

### Post by Skaperen on 2020-02-19
Twitter wants me to register a two factor authentication method.  one of the methods is using a time-based one time password (TOTP) authentication app.  my only option is to run such a thing on Ubuntu/Xubuntu.  does anyone know of one i could use?

---

### Post by Irihapeti on 2020-02-19
KeePassXC has a TOTP option which I occasionally use.

---

### Post by Skaperen on 2020-02-19
i installed keepassxc (got version 2.3.1).  the man page does not explain how to run the TOTP option.  i plain started keepassxc and the app that starts up has no obvious way to run the TOTP option.  how do i go about using it?

---

### Post by Irihapeti on 2020-02-19
I have version 2.3.1 from the repo.

Start the program and create a new entry in the usual way, and save. Then right-click on it and you'll get a menu. One of the items is Time-Based One-Time password, with several options.

You do need to be able to copy/paste the random number string/seed into the entry.

(I can't remember now where I first found out about this, or I'd post the link.)

---

### Post by Skaperen on 2020-02-20
i'll need to figure out how to import my current data into it.  i can make a CSV and maybe JSON.

---

