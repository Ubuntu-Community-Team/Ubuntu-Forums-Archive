---
title: "Users Gone"
date: 2008-05-18
forum: General Help
---

### Post by 64Media on 2008-05-18
I'm running Ubuntu 8.04, and I turned on my computer one day and the main user that I usually select from the list is just gone.

How do I log in without a user?

---

### Post by Mhurst1 on 2008-05-18
Did you try to just type in the user name and password?

---

### Post by 64Media on 2008-05-18
I tried what I *thought* was my username, but either it still doesn't work or I don't have it exactly right.

Either way, I still can't get in.

---

### Post by meierfra. on 2008-05-18
Boot into recovery mode (you might have to press "Esc" during boot up to get to the grub menu) 

type
```

ls /home
```

and your correct user name should appear.

---

### Post by meierfra. on 2008-05-18
You can also change your password in recovery mode:

```
passwd your_username
```

---

