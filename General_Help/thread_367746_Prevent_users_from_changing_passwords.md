---
title: "Prevent users from changing passwords"
date: 2007-02-22
forum: General Help
---

### Post by SumBudE on 2007-02-22
Is there a way I can prevent my kids from changing their own passwords on our family computer?  We're running Edgy.  Thank you.

---

### Post by ViRMiN on 2007-02-22
Okay, first thing that springs to mind is:

```

sudo chattr +i /etc/shadow

```

That'll prevent even root from changing the shadow file.  When you need to modify the contents do:

```

sudo chattr -i /etc/shadow

```

---

