---
title: "File =&gt; Create New Folder ?"
date: 2008-02-06
forum: General Help
---

### Post by skunkbad on 2008-02-06
I have set up php/apache2, and the "localhost" directory is in File System var/www. I want to create a folder in that location, but the option is ghosted out in the file menu.

The goal is to eventually be able to use Filezilla to download and upload files from this www directory.

Thanks for any help.

---

### Post by PeterJS on 2008-02-06
/var/www is not owned by your user, so you don't have permission to write there. You've got a couple options, you can change the ownership on /var/www/ to your user with:
```

sudo chown -R *username* /var/www

```
Or you can leave the ownership as is, and alwasy use a nautilus instance lanuched with elevated privilages to write there with:
```

gksudo nautilus /var/www

```

---

### Post by skunkbad on 2008-02-06
I chose option number 1. The "nautilus" option seemed scary. I've only been using Ubuntu for less than a week!

THANKS!

---

