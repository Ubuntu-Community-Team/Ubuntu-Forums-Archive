---
title: "acroread in 12.10"
date: 2012-10-24
forum: General Help
---

### Post by nemarona on 2012-10-24
acroread is not available in the Canonical "partner" repositories in Ubuntu 12.10.

I tried installing the .deb for oneiric (since there's no amd64 version for precise) downloaded from [http://archive.canonical.com/ubuntu/pool/partner/a/acroread/]("http://archive.canonical.com/ubuntu/pool/partner/a/acroread/") but run into dependency issues.

What would be an alternative procedure for installing acroread in 12.10?

---

### Post by Pilot6 on 2012-10-24
You can download deb from adobe.com

---

### Post by aspergerian on 2012-10-24
Today I installed acroread in two computers running Xubuntu 12.04.1. What helped me succed was [http://askubuntu.com/questions/89127/how-do-i-install-adobe-acrobat-reader](http://askubuntu.com/questions/89127/how-do-i-install-adobe-acrobat-reader)

Especially, 
"To install Adobe Acrobat in 11.10 or 12.04 you will need to enable the canonical partners repository in the Software Sources tab." [see image on url]

And I had to delete "acroread-fonts" in:
sudo apt-get -y install acroread acroread-fonts

Entered: 
sudo apt-get -y install acroread
which then worked fine.

---

