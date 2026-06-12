---
title: "problem installing java"
date: 2008-04-30
forum: General Help
---

### Post by coool on 2008-04-30
Hi
I am relatively new to ubuntu. I am using hardy. I have this problem when i try to install java.

I wanted an rss aggregator and blog reader. So i downloaded blogbridge ([http://www.blogbridge.com](http://www.blogbridge.com)). But i am unable to install this as it uses java to run. More specifically it says it requires a program called 'javaws'.

So i downloaded the required deb files. They are
1) openjdk-6-jre
2) openjdk-6-jre-lib
3) openjdk-6-jre-headless
4) libaccess-bridge-java.
These packages will be referred to by their numbers henceforth

The problem is when i try to install 2, it says 1 3 and 4 need to be installed. So when i try to install 1 3 or 4, it gives all the 4 packages as dependencies including itself. All other dependencies are satisfied. So i am not able to install any of these packages.

Hope you have understood my problem.

What should i do to install these packages? Any ideas?

---

### Post by forrestcupp on 2008-04-30
All you have to do to install java is type in a terminal
```
sudo apt-get install sun-java6-plugin
```

Always check the repositories before you go downloading something.

---

