---
title: "Edgy+Feisty packages"
date: 2007-03-20
forum: General Help
---

### Post by qpwoeiruty on 2007-03-20
In general, besides package specific problems, is installing Feisty packages in Ubuntu Edgy a safe thing to do? I had to update my libcurl3 packages using what was in packages.ubuntu.com for Feisty in order to fig a bug I was having with bzflag. Will this cause problems for me later on or if I am going to install something that depends on newer software than in the edgy repos, is it OK to install Feisty's packages?

---

### Post by adam.tropics on 2007-03-22
You can get yourself in dependency hot water yes. [You might find this an interesting read]("http://ubuntuforums.org/showthread.php?t=268687") if you want the latest and greatest. It's really best to investigate whether there is actually anything you're after in the newer version, as often the actual differences will be minimal..

---

### Post by qpwoeiruty on 2007-03-27
Just getting a newer libcurl installed was a pain in itself.
I wasn't really sure what to do except dpkg -i and keep dling and installing all the stuff it depended on. I ended up with about 25-30 feisty packages...

As I said, I was having a problem with Edgy's version of libcurl3. There's a bug in Edgy's version that causes bzflag to give "Core Segmentation Fault" errors.  The Feisty version didn't have the problem, so I used that.

Thanks for the link! It looks interesting. I'll have to try that next time

---

