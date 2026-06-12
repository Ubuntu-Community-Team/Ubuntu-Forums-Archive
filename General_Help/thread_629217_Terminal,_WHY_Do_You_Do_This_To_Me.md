---
title: "Terminal, WHY Do You Do This To Me?"
date: 2007-12-02
forum: General Help
---

### Post by Mark76 on 2007-12-02
cd home/mark/Desktop/xfce4-smartpm-plugin-0.2.2
bash: cd: home/mark/Desktop/xfce4-smartpm-plugin-0.2.2: No such file or directory
 cd xfce4-smartpm-plugin-0.2.2
bash: cd: xfce4-smartpm-plugin-0.2.2: No such file or directory
cd home
bash: cd: home: No such file or directory
cd /home
cd /mark
bash: cd: /mark: No such file or directory
cd /Desktop
bash: cd: /Desktop:** No such file or directory**
cd
cd /Desktop
bash: cd: /Desktop: No such file or directory
cd /mark
bash: cd: /mark: No such file or directory
cd /home
cd /mark
cd: /mark: No such file or directory
cd /mark
bash: cd: /mark: No such file or directory

:(

---

### Post by PmDematagoda on 2007-12-02
Actually the terminal did not do anything, you are simply using the improper codes.

For example:-

```
cd /Desktop
```

is actually

```
cd /home/username/Desktop
```

and ```
cd /mark
``` assuming that it is your username is mark is actually:-

```
cd /home/mark
```

---

### Post by inforce on 2007-12-02
Try this :-

cd /home
cd mark
cd Desktop
cd xfce4-smartpm-plugin-0.2.2
or 
./xfce4-smartpm-plugin-0.2.2 if it is a script to be run

When you put a / it means start at the root of the drive

So when you type cd /mark it is looking at the root, not under home

You can also use cd /home/mark/Desktop/xfce4-smartpm-plugin-0.2.2

If you type pwd it will tell you which directory you are currently in.

Tim

---

### Post by Daveth on 2007-12-02
or, if you are as lazy as I am, you can drag and drop your file into the terminal which then gives you its full path. You can then apply commands to it there.

---

### Post by ronmarley1 on 2007-12-02
Here's a great site to learn the command line:
[http://linuxcommand.org/](http://linuxcommand.org/)

---

