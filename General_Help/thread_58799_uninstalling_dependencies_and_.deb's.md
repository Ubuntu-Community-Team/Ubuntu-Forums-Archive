---
title: "uninstalling dependencies and .deb's"
date: 2005-08-21
forum: General Help
---

### Post by 5-HT on 2005-08-21
Just getting started with ubuntu, and have read the unofficial guide as well as a lot of posts on the forum to get used to linux and ubuntu but there are two things I'm still unsure of towards installation/removal of programs and was wondering if someone may be able to help me out?

1. When installing a program  through apt-get or synaptic that needs you to download few dependencies to run,
 when it comes to uninstalling the program, are those dependencies also automatically uninstalled?

Or should I make note off all these dependencies and try to uninstall them directly through synaptic or apt-get?

2. If  a program's not found in the repositories, and you download the .deb package instead...when it comes to uninstalling that program can you then do it through apt-get or synaptic (maybe you'd need to download the .deb into apt's cache folder)? 
If not, how does one go about uninstalling the program?


Thanks for any help,
(hopefully this is in the right forum)

---

### Post by arnieboy on 2005-08-21
[QUOTE=5-HT]Just getting started with ubuntu, and have read the unofficial guide as well as a lot of posts on the forum to get used to linux and ubuntu but there are two things I'm still unsure of towards installation/removal of programs and was wondering if someone may be able to help me out?

1. When installing a program  through apt-get or synaptic that needs you to download few dependencies to run,
 when it comes to uninstalling the program, are those dependencies also automatically uninstalled?

Or should I make note off all these dependencies and try to uninstall them directly through synaptic or apt-get?

2. If  a program's not found in the repositories, and you download the .deb package instead...when it comes to uninstalling that program can you then do it through apt-get or synaptic (maybe you'd need to download the .deb into apt's cache folder)? 
If not, how does one go about uninstalling the program?


Thanks for any help,
(hopefully this is in the right forum)[/QUOTE]
Yes it is the correct forum.  
The answer to your first question: Dependencies are NOT uninstalled when u uninstall a package with apt-get or synpatic. If u are a stickler on conserving disk space try using "aptitude". That will track ur dependencies and and uninstall them along with the "main" package. aptitude is in the repositories in case u wanna try it out.
The answer to your second question: yes u can use apt-get or synpatic to uninstall a package that u have installed separately. For apt-get the usual command is:
```
sudo apt-get remove *package_name*
```. The easiest way to uninstall it would be to open synpatic and search for it and uninstall  it.

---

### Post by 5-HT on 2005-08-21
Thanks for the help, it cleared up everything!

Looked into aptitude (it's even installed as part of the default ubuntu installation now), and just need to read the help files on it to learn all the options.

Thanks again.

---

