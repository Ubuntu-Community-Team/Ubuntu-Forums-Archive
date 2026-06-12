---
title: "Simulated Package Install?"
date: 2022-08-18
forum: General Help
---

### Post by wyattwhiteeagle on 2022-08-18
I know it's done by using the -s switch...
where does the -s go...

```
sudo -s apt install <package name>
```
```
sudo apt -s install <package name>
```

---

### Post by &amp;KyT$0P# on 2022-08-18
The correct way would be
```
apt -s install <package name>
```

Your first command passes the [FONT=Courier New]-s[/FONT] option to [FONT=Courier New]sudo[/FONT], not [FONT=Courier New]apt[/FONT].  See [FONT=Courier New]man sudo[/FONT] for what that would do.

Your second command would do what you're seeking, but the use of sudo/root is unnecessary.

---

### Post by wyattwhiteeagle on 2023-07-29
> **halogen2 said:**
> The correct way would be
```
apt -s install <package name>
```

Your first command passes the [FONT=Courier New]-s[/FONT] option to [FONT=Courier New]sudo[/FONT], not [FONT=Courier New]apt[/FONT].  See [FONT=Courier New]man sudo[/FONT] for what that would do.

Your second command would do what you're seeking, but the use of sudo/root is unnecessary.
Thanks
I'm marking this as solved

---

