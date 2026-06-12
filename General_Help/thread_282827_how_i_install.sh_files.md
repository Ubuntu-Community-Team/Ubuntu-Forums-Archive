---
title: "how i install.sh files?"
date: 2006-10-23
forum: General Help
---

### Post by eighthate on 2006-10-23
How do i install .sh files? thankls
i'm using ubuntu 6.06

---

### Post by Kameli on 2006-10-23
By typing ./package.sh, ./ checks filetype and then determines which method he will use to install, you can also install .sh with sh install.sh, and you can install .run by typing ./package.run. But i recommend ./ because it checks filetype and then install it with right style.

---

### Post by Tomosaur on 2006-10-23
Technically, you don't install sh files, you just run them. An .sh file is simply a shell script. Some scripts will install files, while others will act as a program. Usually, you will run a .sh file like this:
```

sh /path/to/myScript.sh

```

Alternatively, you can use the following command to make your script executable:
```

chmod 755 /path/to/myScript.sh

```

And then in the future, all you have to do to run you script would be:
```

/path/to/myScript.sh

```

---

### Post by eighthate on 2006-10-23
thanks for ur help!

---

### Post by cbh2000 on 2008-07-08
An easier way to execute the .sh file is open the .sh file with a text editor (Right-click>Open With>Mousepad or AbiWord) select all the text and the copy and paste into a terminal and hit enter if it doesn't start.

---

