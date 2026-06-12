---
title: "I updated Webmin"
date: 2005-09-05
forum: General Help
---

### Post by Freddie on 2005-09-05
Hi, I have been using webmin for a little while now and have been quite happy with it. However, today I decided to upgrade it (as the one is the repository is 1.180 while the newest one is 1.220). i clicked on upgrade and it updated itself and then downloaded all of the extra modules which also needed to be upgraded. I then deleted /usr/share/webmin. However, it all works fine but the silly package manager still thinks that I have 1.180 installed as well as all of the packages (I do still have them but newer versions). So, how can I tell the package manager that they are no more?

---

### Post by arnieboy on 2005-09-05
[QUOTE=Freddie]Hi, I have been using webmin for a little while now and have been quite happy with it. However, today I decided to upgrade it (as the one is the repository is 1.180 while the newest one is 1.220). i clicked on upgrade and it updated itself and then downloaded all of the extra modules which also needed to be upgraded. I then deleted /usr/share/webmin. However, it all works fine but the silly package manager still thinks that I have 1.180 installed as well as all of the packages (I do still have them but newer versions). So, how can I tell the package manager that they are no more?[/QUOTE]
since u neither updated webmin from the repositories, nor did u install the latest deb to replace the old ones, the package manager has no way to find out that U have a newer version installed. 
I would not worry too much about the version in the package manager because they are not updating the repositories for quite some time on Hoary.

---

