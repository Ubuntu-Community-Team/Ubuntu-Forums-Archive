---
title: "How to Restore Trashed File that Prevents Updates?"
date: 2013-06-15
forum: General Help
---

### Post by Ubuntist on 2013-06-15
I can't get any software updates.  Running [FONT=system]apt-get check[/FONT] produces the following error message:

[FONT=system]Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_raring_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.[/FONT]

And, indeed, when I look at the file that [FONT=system]apt-get[/FONT] is complaining about, [FONT=system]/var/lib/apt/lists/gb.archive...Translation-en[/FONT], I see that it is the click-to-agree-to-terms page from the internet link I was using when I attempted to update a few days ago.

Anyway, how can I get a correct version of the file?

P.S.  I've tried simply deleting the file in the hope that Ubuntu would see it missing and regenerate a sane version of it.  No luck.

---

### Post by plucky on 2013-06-15
> **Ubuntist said:**
> I can't get any software updates.  Running [FONT=system]apt-get check[/FONT] produces the following error message:

[FONT=system]Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_raring_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.[/FONT]

And, indeed, when I look at the file that [FONT=system]apt-get[/FONT] is complaining about, [FONT=system]/var/lib/apt/lists/gb.archive...Translation-en[/FONT], I see that it is the click-to-agree-to-terms page from the internet link I was using when I attempted to update a few days ago.

Anyway, how can I get a correct version of the file?

P.S.  I've tried simply deleting the file in the hope that Ubuntu would see it missing and regenerate a sane version of it.  No luck.

Delete the list files with ```
sudo rm -rf /var/lib/apt/lists/*
``` and then reload them with ```
sudo apt-get update
```

Good Luck

---

### Post by Ubuntist on 2013-06-15
Yo, plucky, you da man, dude!

Thanks -- it worked perfectly.

---

