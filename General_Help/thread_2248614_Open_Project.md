---
title: "Open Project"
date: 2014-10-15
forum: General Help
---

### Post by Robert_Fairing on 2014-10-15
I would like to install Open Project in Ubuntu 14.04 but cannot find a way to get it done. I am not new to Ubuntu but still need step by step instructions. Thie will be a stand alone instalation and does not need to be tied in with any network.

Thanks in advance.

---

### Post by Bucky Ball on 2014-10-15
Did you follow the install instructions [HERE?]("https://community.openproject.org/projects/openproject/wiki/Installation_Ubuntu") Looks pretty involved. That might change with version 4.0, which is apparently due soon, according to the site. The instructions they have are for 12.04 and version 3.0 but may still work fine with 14.04.

Good luck.

---

### Post by Robert_Fairing on 2014-10-15
Yep, tried that but get error messages on trying to get ruby and nothing seems to work after that. I w3as thinking it was something to do with 14.04 over 12. I have read there is a deb package but have not found it anywhere.

---

### Post by tgalati4 on 2014-10-16
If it was easy, it would have been done by now.  You can build a virtual environment of 12.04 and carefully follow the 12.04 instructions.  Or wait for bitnami to build it as a stack and install the stack:  [https://bitnami.com/stacks?utf8=%E2%9C%93&q=openproject](https://bitnami.com/stacks?utf8=%E2%9C%93&q=openproject)

Ruby is a tricky framework to get installed and running correctly.  Also, you need to install the same version of Ruby that is used in OpenProject, and that might conflict with other libraries in your system--this is known as *Dependency File Hell*.  Try installing [Tracks]("http://getontracks.org").  That will earn your Ruby stripes.

---

### Post by Robert_Fairing on 2014-10-16
You lost this old guy up until you provided the link to bitnami. I reall would like to run Open Project as a stand alone and not have to be tethered to wifi. I want to do scheduling and project managment while on the job and in remote locations. I hate the thought of waving the white flag and doing a duel boot with windows.

---

