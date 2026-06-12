---
title: "Flashplayer"
date: 2008-03-11
forum: General Help
---

### Post by SpenceMakesSense on 2008-03-11
Ever since I've started using Ubuntu flash always seemed to be buggy. I would be surfing the web and if i went to a site like myspace or youtube eventually  Firefox just gives up and goes into that gray mode forcing me to force quit. Does anyone have a solution to this. I installed the latest version of flash from the adobe website.

---

### Post by zozobra on 2008-03-12
The last couple versions of Firefox have been crashing more than normal for everyone. I'm not sure if this is the cause of your issue, but it's a thought. You may want to reinstall Firefox and test it with no add-ons and gradually add onto it.

---

### Post by jseiser on 2008-03-12
You could always try using kazehakase, and installing flash from source.  When i ubuntu'd that seemed to be the best way to surf the web on a gecko engine and have flash.


sudo apt-get remove flashplugin-nonfree
sudo apt-get install kazehakase

then go to adobes website and download their tarball.  Then this guide will walk you through installing from source. [http://www.psychocats.net/ubuntu/flashmanual](http://www.psychocats.net/ubuntu/flashmanual)

---

### Post by SpenceMakesSense on 2008-03-12
kazehakase worked fine for me. It may eventually do it again but for now I'll stick with it and see how Firefox is on Hardy. Thanks!

---

