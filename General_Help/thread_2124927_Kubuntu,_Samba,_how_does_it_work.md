---
title: "Kubuntu, Samba, how does it work?"
date: 2013-03-12
forum: General Help
---

### Post by Roasted on 2013-03-12
As a long time user of Samba, and a recent full time adoptee of Kubuntu, I'm a little curious on how exactly Samba works. I see I can right click a folder and hit share and specify what level of access specific users have, but I'm wondering exactly where these configs reside. I checked my smb.conf but nothing was edited, unsurprisingly, since you need root to edit that file and I was not prompted when adding it via Dolphin. Anyway, where's the guts of this? How does KDE work with Samba?

---

### Post by Morbius1 on 2013-03-12
Not a KDE user but  the Nautilus version of this of this utility defines them in /var/lib/samba/usershares.

Usually you run the following command to see all your Samba Usershare definitions at once:
```
net usershare info --long
```

The big difference between the Dolphin way and the Nautilus way is that in Nautilus it automatically adjusts the permissions of the shared folder where in Dolphin it does not - at least not the last time I used it.

---

### Post by Roasted on 2013-03-12
> **Morbius1 said:**
> 

The big difference between the Dolphin way and the Nautilus way is that in Nautilus it automatically adjusts the permissions of the shared folder where in Dolphin it does not - at least not the last time I used it.

I'm a little confused over what you're referring to. I always thought the permissions of the folder were... the permissions of the folder. I didn't think anything could be adjusted without some sort of chmod'ing, etc. Unless I'm on the totally wrong page?

---

### Post by Morbius1 on 2013-03-13
> **Roasted said:**
> I'm a little confused over what you're referring to. I always thought the permissions of the folder were... the permissions of the folder. I didn't think anything could be adjusted without some sort of chmod'ing, etc. Unless I'm on the totally wrong page?
If I create a Samba Usershare in Nautilus allowing guest read / write access for example of say  ... my Public folder I am presented with a dialog box that looks like this:[ATTACH=CONFIG]240116[/ATTACH] 
When I select "Create Share" I am presented with another dialog box that asks me if I want it to modify permissions:[ATTACH=CONFIG]240117[/ATTACH]

The last time I used Dolphin ( admittedly some time ago ) it's missing the second step. When I'm done using Nautilus a samba guest client will in fact have r/w access to the share. With Dolphin they cannot unless the user modifies permissions manually.

---

