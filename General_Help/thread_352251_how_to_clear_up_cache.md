---
title: "how to clear up cache???"
date: 2007-02-03
forum: General Help
---

### Post by burmanabhay88 on 2007-02-03
I'm new to Linux. I use Ubuntu 6.10 Edgy. Can someone please tell me how to clear up my installed applications cache??? when i download new programs using Add/ Remove Programs, a copy of the installation file gets saved in var/cache/apt/. How do i delete these. I need to do so to create some space on HDD. I cannot remove them manually.

---

### Post by mcduck on 2007-02-03
In terminal 'sudo apt-get clean' will do the job for you. You can als clean the package cache from Synaptic's settings, and there's also option to delete downloaded packages after installing.

---

