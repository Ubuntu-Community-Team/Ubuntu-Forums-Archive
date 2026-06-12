---
title: "SIGSEGV libjvm Compiler opening pycharm project"
date: 2019-03-07
forum: General Help
---

### Post by paul792 on 2019-03-07
On a brand new Lenovo E585 (AMD Ryzen 5 2500U with Radeon Vega Mobile Gfx) I installed Ubuntu 18.10 for which i also had to set a number of kernel parameters; not sure if it matters for this issue though.... I also upgraded to kernel 5.0.

I have an issue starting pycharm, as soon as i open a project i get a segmentation fault pointing to a Compiler activity.

I tried different pycharm versions (2018.3.5 and 2017.2.7) and also with different JRE versions (the version shipped with pycharm and also jre 8u144, 8u192 and 8u201) but i always get stuck on this, i just can't open a project successfully and do some development work.

Notice i also cleaned up pycharm and idea project files (in ~/.pyCharm.... and the .idea folder in the project).

I'm thinking that this is not a pycharm or JRE issue but an issue in the layer below? maybe some missing libraries of some kind? However i have no clue yet where to look for and what libraries to install. Any tips are very much appreciated.

Paul

---

### Post by monkeybrain20122 on 2019-03-07
What are the errors if you start it in the terminal?

---

