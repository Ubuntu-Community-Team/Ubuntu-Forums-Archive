---
title: "Editing php files in opt directory as admin"
date: 2014-01-03
forum: General Help
---

### Post by uzumakifahim on 2014-01-03
Hi,

I'm using Ubuntu 12.04. I'm learning PHP to test the output I need to run the .php files from /opt... directory. Fact is that, when I open any .php files in gedit or geany it doesn't let me to edit the file. How can I create/edit new files using Geany/Gedit in the /opt... directory as admin?

Thanks in advance.

---

### Post by Dave_L on 2014-01-03
You can run gedit as admin using this command:

```
gksudo gedit &
```

You could also change the ownership of the PHP files using the command "chown". But that's a potential security risk.

---

### Post by uzumakifahim on 2014-01-03
Really thanks for your help. I'm marking this thread as solved!!!

---

