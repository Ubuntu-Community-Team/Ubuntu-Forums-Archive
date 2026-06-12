---
title: "Windows Ubuntu Subsystem - using gksu"
date: 2018-05-01
forum: General Help
---

### Post by jlaursen-dk on 2018-05-01
Hi

I'm trying to install virt-manager, and access my server through my windows computer.

I've installed that new Windows Subsystem Ubuntu, which so far seems pretty nice.

So, the ubuntu i get is a console only enviroment, but obviously gksu needs desktop enviroment. I found that you should be able to do this using Xming. I've installed Xming, and added "export DISPLAY=':0.0' " ot my bashrc file. 

When executing the command gksudo virt-manager i get the following errors:

In the Ubuntu subsystem:
```
Error copying '/home/jala/.Xauthority' to '/tmp/libgksu-Ranp9g': No such file or directory
```

and Xming X throws this error:
[IMG]https://i.imgur.com/6BsIAJY.png[/IMG]

---

