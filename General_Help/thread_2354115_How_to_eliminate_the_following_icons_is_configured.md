---
title: "How to eliminate the following: icons is configured multiple times in etc/apt/sources"
date: 2017-02-28
forum: General Help
---

### Post by thedoctor818772 on 2017-02-28
I am running Ubuntu 16.10 on my notebook and upon updating I keep getting the following in the terminal:

```


W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:16 and /etc/apt/sources.list:21




```

What does this mean and how can I eliminate this?

Thanks!

---

### Post by thedoctor818772 on 2017-02-28
I found this solution which worked for me:



[LIST=1]
[*]sudo rm /etc/apt/sources.list
[*]sudo software-properties-gtk
[*]Pick your options
[*]Save
[/LIST]
at the following site (ubuntu forums also): 

[HTML]http://askubuntu.com/questions/760896/how-can-i-automatically-fix-w-target-packages-is-configured-multiple-times[/HTML]

Thanks!

---

