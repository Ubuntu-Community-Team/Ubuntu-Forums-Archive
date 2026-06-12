---
title: "ATI card problems"
date: 2006-12-30
forum: General Help
---

### Post by nick holme on 2006-12-30
I had a problem with my ATI card drivers causing openoffice to not work with dapper. I found the cure for this was to install an older version of libGL.so.1.2. Since installing edgy, I have found a similar problem, but this also causes Totem to crash on opening. The problems seem to revolve around the flgrx drivers which use LibGL.so.1.2. Unfortunately the workaround doesn't work with edgy. I tried sudo apt-get install --reinstall libgl1-mesa as suggested in the unoficial ATI site and this seems to have replaced some ati drivers with mesa and everything now seems to work. I'm not sure exactly why, but this may help others.

Nick

---

