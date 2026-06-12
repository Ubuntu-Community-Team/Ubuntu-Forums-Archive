---
title: "Ubuntu &amp; F@H: Can't get GPU to fold..."
date: 2020-06-12
forum: General Help
---

### Post by jw-middleton on 2020-06-12
**UPDATE**: Never mind. There are some dependencies that are messed up with the install and it isn't worth it to try and fix. I'll waiting a month and try it again as GitHub is working on updating the package.

I hope this is in the right place.

I installed F@H on Ubuntu 20.04 LTS. It never asked how I wanted to run  it. I noticed that it is only running on 1 core on 15-3590. I have gone  nutz trying to get it to run on GPU, which is a GTX 1650 OC D6. I  Googled and tried stuff for hours with no luck. I could not get  FAHControl to work!! I even created a fake Gnome-phython2 package based  on one persons experience on 19.04. I stopped the client, edited  /etc/fahclient/config.xml to change <gpu v='false'/> to <gpu  v='true'/>, then rebooted. I found that config.xml had been reset. I  did chmod on the file to give rw permissions to the file before editing.  The permissions had reverted as well.

Any idea?

John

---

### Post by CatKiller on 2020-06-12
After you've said that it can use the GPU, you also need to add a GPU slot. You've not said that you did that.

---

