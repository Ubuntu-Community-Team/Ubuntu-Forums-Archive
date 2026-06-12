---
title: "ATI binary x.org driver"
date: 2007-11-03
forum: General Help
---

### Post by Unicycle on 2007-11-03
Hi folks.  I am on a continuing pursuit to make my *AGP ATI Radeon X1600 512mb Pro* work on Gutsy (or any other version, for that matter).

Vesa, of course, works, but doesn't offer what I want -- 3D acceleration!

So, I recently discovered the "*ATI binary x.org driver*" listed in the Add/Remove Applications app.  What is this?  Is it the new-ish proprietary ATI driver, packaged and ready to go for Ubuntu?  If so, is it wise to install it, and then how do I make it work?

I need all the help I can get.  Finally, how do I remove it if it doesn't work?  Is the usual "uncheck" method sufficient?

Thanks sooo much, guys.  I would be tempted to send a thank-you card to whoever can make this work. ;)

---

### Post by Light- on 2007-11-03
Yep, install it to get 3D acceleration on your card. If you want Compiz, install xserver-xgl too otherwise Compiz wont work. If you want to uninstall, you can just uncheck it in the restricted drivers manager or edit your xorg.conf back to "vesa"

---

### Post by strabes on 2007-11-03
I **strongly** recommend **against **installing xserver-xgl. It's highly unstable, very slow, etc. If you want compiz without using xgl you'll have to use ATI's newly-released 8.42 drivers but I also recommend against them because they have many problems with video playback, etc. Your best option is to simply follow the instructions [here](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-db58a7f32e6242b004c62062227bd1557d184218) for installing the proprietary ATI drivers located in the ubuntu repositories.

---

