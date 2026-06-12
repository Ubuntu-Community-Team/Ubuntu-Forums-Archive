---
title: "Installing KDE : problems"
date: 2004-10-28
forum: General Help
---

### Post by GLDavid on 2004-10-28
Hello !

First of all, congratulations for Ubuntu. I appreciate to work on a Debian-like style with a esay way to install.
But, I've got a little problem : I just want to install kde with apt-get. Here's my sources.list :
```

deb http://archive.ubuntu.com/ubuntu/ warty main restricted universe multiverse 
deb http://archive.ubuntu.com/ubuntu/ warty-security main restricted 
deb http://archive.ubuntu.com/ubuntu/ warty-updates main restricted universe multiverse 
```
A very common sources.list, isn't it ?
But when I put : apt-get install kde, here are the errors :
```

kde: Depends: kde-amusements but it will not be installed
       Depends: kdeaddons but it will not be installed
       Depends: kdemultimedia but it will not be installed
```

 :confused: Well, what can I do ?

Thank you very much for answers.

Bye bye.

---

### Post by im_ka on 2004-10-28
welcome onboard!

kde is not supported by ubuntu (read: there are no official ubuntu packages at the moment).

you need to add universe to be able to install kde. there's a howto on universe on the ubuntu website.

---

### Post by GLDavid on 2004-10-28
Hello

Thank you im_ka for your answer. But, the problem is still here. I add this line in my source.list and the problem is not solved :
```
deb http://archive.ubuntu.com/ubuntu/ warty universe
```
So, is it this way to install KDE ?

Bye bye

---

