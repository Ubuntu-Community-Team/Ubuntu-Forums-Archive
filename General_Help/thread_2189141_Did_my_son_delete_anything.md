---
title: "Did my son delete anything?"
date: 2013-11-20
forum: General Help
---

### Post by grier-devon on 2013-11-20
So I was letting my son play on the computer today and when I looked over he was in the software sources under other software tab. I pulled him off and everything look good put I was hoping you all could take a look and tell me if everything looks like it is there, I am running Ubuntu 13.10 64 Bit.

[ATTACH=CONFIG]247971[/ATTACH]

---

### Post by fantab on 2013-11-20
Not sure but select 'Canonical Partners' and run 
```
sudo apt-get update
```

Not sure because we don't know if you were using the Partner Repo in the first place...

---

### Post by Bashing-om on 2013-11-20
grier-devon; Hi !

My suggestion is to check the "Canonical Partners" repository (the top entry).
Do you have need to use/read source code ? Else not needed. By default the "Source Code" repositories are enabled, but if unchecked the updates will be MUCH faster. 

[INDENT][INDENT]just what I think
[/INDENT][/INDENT]

---

### Post by deadflowr on 2013-11-20
Does your son have the admin password you use?
Or one you set for him?

If he tried to change anything in software sources, he would need to use an administrator's password, or run as root.

Otherwise, the list you posted look fine.
Independent is the extras repos, and then you added the google one for chrome, when you installed chrome.
As stated the partners repos are never enabled by default.

---

### Post by Bibek on 2013-11-21
looks good, he cant do anything unless he knows your root password. but in any case, you have the right repos. so its all good.

---

### Post by grier-devon on 2013-11-21
Hey everyone thanks so much, I did enable the Canonical partners, I don't really view source so I do not think I will need that one. I think I am going to have to change my password cause I think he was watching me type and saw me enter my password, the crazy thing he is four. I just tonight set him up on his first computer, it is a five year old HP with dual core AMD, Nvidia GPU and 4 GB of memory. Set up with Edubuntu, see how he does. Thanks so much for the help everyone.

---

