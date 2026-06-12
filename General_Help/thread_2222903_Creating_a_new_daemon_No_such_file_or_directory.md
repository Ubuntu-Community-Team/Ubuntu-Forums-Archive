---
title: "Creating a new daemon: No such file or directory"
date: 2014-05-08
forum: General Help
---

### Post by hojjat on 2014-05-08
I am trying to create a new daemon; I wrote the bash script and plcaed it in /etc/init.d and made it executable. The script works fine when called directly like *sudo sh /bin/etc.d/myscript start*. However, when I call *sudo service myscript start* I get this error:

```

env: /etc/init.d/myscript: No such file or directory

```

The warning is not really helpful, because the file actually exists. Any advice as to what I am missing here?

---

### Post by hojjat on 2014-05-08
Never mind, I decided to use Upstart instead.

---

