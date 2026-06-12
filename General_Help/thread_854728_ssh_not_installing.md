---
title: "ssh not installing"
date: 2008-07-09
forum: General Help
---

### Post by headlessb on 2008-07-09
I keep getting this in synaptic when I try to install ssh:
"ssh: Depends: openssh-server but it is not going to be installed"

I have an idea of what it could be but wanted to see if anyone has come across this problem. I'm running Ubuntu 8.04 LTS Desktop

---

### Post by ktrnka on 2008-07-09
Are you trying to install openssh-server? The client should already be installed. If you are trying to install "ssh" it's just a metapackage.

---

### Post by headlessb on 2008-07-09
when I try installing openssh-server I get this:
openssh-server:
  Depends: openssh-client (=1:4.7p1-8ubuntu1) but 1:4.7p1-8ubuntu1.2 is to be installed

---

