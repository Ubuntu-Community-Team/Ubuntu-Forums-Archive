---
title: "Programs are missing in adept"
date: 2007-04-08
forum: General Help
---

### Post by linuxmann on 2007-04-08
I just reinstalled kubuntu yesterday and when i went to adept i noticed there were about 4500 packages instead the about 18000 i saw when the last time kubuntu was installed. When i reinstalled the operating system i made sure my dsl was on so the installer could install the security packages for my operating system. I did everything right so, why arent all of the packages there?

---

### Post by ihavenoname on 2007-04-08
> **linuxmann said:**
> I just reinstalled kubuntu yesterday and when i went to adept i noticed there were about 4500 packages instead the about 18000 i saw when the last time kubuntu was installed. When i reinstalled the operating system i made sure my dsl was on so the installer could install the security packages for my operating system. I did everything right so, why arent all of the packages there?
make sure you have all the repos enabled. It seems you only have main and security enabled. You need to manually enable universe and multiverse  to get the rest. kdesu kate /etc/apt/sources.list and uncomment the necessary lines.

---

### Post by linuxmann on 2007-04-08
I enabled them but they are still not showing up. I am confused on that kdesu kate /etc/apt/sources.list thing you mentioned.

---

### Post by ihavenoname on 2007-04-08
> **linuxmann said:**
> I enabled them but they are still not showing up. I am confused on that kdesu kate /etc/apt/sources.list thing you mentioned.
oh sorry, I probably wasn't very clear. You remove the # from the lines  that start with deb and have universe in them. Like this
```
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe main restricted multiverse
```

after you do that open a terminal. (alt+F2 and type konsole) 
and type  sudo apt-get update. Then open adept and you "should" have all you packages.

---

### Post by linuxmann on 2007-04-08
Thats strange. I didnt see any # in the lines of what you've mentioned. Unless i am still confused about the whole thing. for clarification i will share pictures to see if there is still a problem or not.

[http://img73.imageshack.us/img73/7788/snapshot2gm1.png](http://img73.imageshack.us/img73/7788/snapshot2gm1.png)

[http://img73.imageshack.us/img73/7407/snapshot1yw5.png](http://img73.imageshack.us/img73/7407/snapshot1yw5.png)

[http://img67.imageshack.us/img67/5976/snapshot3gu3.png](http://img67.imageshack.us/img67/5976/snapshot3gu3.png)

EDIT: I had to update kubutu on the updater. Now everything works and there are 18467 packages to download so far.

---

### Post by ihavenoname on 2007-04-08
double post

---

### Post by ihavenoname on 2007-04-08
> **linuxmann said:**
> Thats strange. I didnt see any # in the lines of what you've mentioned. Unless i am still confused about the whole thing. for clarification i will share pictures to see if there is still a problem or not.

[http://img73.imageshack.us/img73/7788/snapshot2gm1.png](http://img73.imageshack.us/img73/7788/snapshot2gm1.png)

[http://img73.imageshack.us/img73/7407/snapshot1yw5.png](http://img73.imageshack.us/img73/7407/snapshot1yw5.png)

[http://img67.imageshack.us/img67/5976/snapshot3gu3.png](http://img67.imageshack.us/img67/5976/snapshot3gu3.png)

EDIT: I had to update kubutu on the updater. Now everything works and there are 18467 packages to download so far.

My post above had a slightly modified line. But the jist of it was that if it had universe some where in the line and it started with deb you should uncomment it. 

I am glad you now have it working. 

btw how old are you?

---

