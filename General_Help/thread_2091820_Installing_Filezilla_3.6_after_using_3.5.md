---
title: "Installing Filezilla 3.6 after using 3.5"
date: 2012-12-06
forum: General Help
---

### Post by mynot on 2012-12-06
Using Xubuntu 12.04:

I have been using Filezilla successfully for 12 months, however I struck a problem when I upgraded to 3.5. The IT people at the web host tell me the problem is fixed in Filezilla 3.6 and I should upgrade.

I found these instructions many times on the web:
sudo add-apt-repository ppa: n-muench/programs-ppa
sudo apt-get update 
sudo apt-get install filezilla

After this, it continued to run 3.5, so I (completely) removed 3.5, and repeated these commands. It still runs 3.5. How can this be?
Thanks

---

### Post by howefield on 2012-12-06
> **mynot said:**
> It still runs 3.5. How can this be?

Because you are running 3.5 perhaps ?

If you added the Precise repository information to your sources.list looks like you'll get 3.5.

Filezilla version 3.6 is in the Quantal repository.

---

