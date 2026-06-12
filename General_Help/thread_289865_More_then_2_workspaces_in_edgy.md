---
title: "More then 2 workspaces in edgy?"
date: 2006-10-31
forum: General Help
---

### Post by jincast90 on 2006-10-31
Is it possible to get more then the default 2 virtual desktops in edgy. I used to love having the four in dapper.

---

### Post by bollix47 on 2006-10-31
right click on a workspace - select preferences and choose number of workspaces.

---

### Post by LMP900 on 2006-10-31
Right click the workspaces

Select **Preferences**

Choose how many desktops you want

---

### Post by jincast90 on 2006-10-31
All right. Thanks you guys. While I am still here, can anyone tell me if they have problems adding bookmarks in Firefox? I press Bookmarks->Bookmark this page.. and I don't have any option called add like in dapper.

---

### Post by boban on 2006-10-31
> **jincast90 said:**
> All right. Thanks you guys. While I am still here, can anyone tell me if they have problems adding bookmarks in Firefox? I press Bookmarks->Bookmark this page.. and I don't have any option called add like in dapper.

Pressing "Bookmark this page" should work well (windows with "add" just pop's up)... It's working on my machine...

---

### Post by jincast90 on 2006-10-31
> **boban said:**
> Pressing "Bookmark this page" should work well (windows with "add" just pop's up)... It's working on my machine...

You see I dont get this add button. In dapper I used to have a button with a  + on it saying add. I have the cancel button but not the add button.

---

### Post by boban on 2006-11-01
> **jincast90 said:**
> You see I dont get this add button. In dapper I used to have a button with a  + on it saying add. I have the cancel button but not the add button.

Hmm... Maybe something is wrong with permissions to ~/.mozilla directory... try:

```

chown your_username ~/.mozilla -R
chmod 775 ~/.mozilla -R

```

When I changed permission to 000 I wasn't able to add bookmarks (but still - "add" button was visible)...

If that won't help - try reinstalling firefox...

---

### Post by tophatandy on 2006-12-12
thanks for sharing a fix for the workspace thing.. had the exact same problem..

=D

---

