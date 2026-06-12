---
title: "How to hide gedtit's backup file from ls?"
date: 2008-01-23
forum: General Help
---

### Post by Zdravko on 2008-01-23
Every time I type ls, I see all the backup files from gedit - with suffix ~. Is there a way to not display them?

---

### Post by capink on 2008-01-23
Try:

```
ls --hide=*~
```

You can make this the default behaviour of ls by setting the following alias in your ~/.bashrc:

Open the file:

```
gedit ~/.bashrc
```

And append the following line to it:

```
alias ls='ls --hide=*~'
```

---

