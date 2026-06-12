---
title: "Lost Entire Control"
date: 2008-01-03
forum: General Help
---

### Post by Tristam Green on 2008-01-03
As with all great things that go wrong, this begins with me toying around.  I went into "users and groups", and unchecked the property "Administer the System" as my normal user account.  Now, to say the least, I cannot re-check that box and regain control.  I likewise cannot even access "Users and Groups" when in recovery mode.

What gives, and please don't tell me I need to reinstall :\  I just got the system tweaked to where I want it.

---

### Post by PeterJS on 2008-01-03
From recovery mode you can re-add yourself to the admin group from the terminal with:
```

usermod -a -G admin username

```

---

### Post by Tristam Green on 2008-01-03
tried it, it worked, many MANY thanks.  i knew about the 2-tier root system existent in *buntu, but i didn't really know how it worked.  now i have a vast appreciation for it.

---

