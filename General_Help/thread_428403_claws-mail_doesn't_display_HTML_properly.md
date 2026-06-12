---
title: "claws-mail doesn't display HTML properly"
date: 2007-04-30
forum: General Help
---

### Post by QwUo173Hy on 2007-04-30
Claws mail manages to remove HTML tags before displaying the information in the mail. This is nice, but it doesn't do it very well.

This is how Claws does it;
(see image-claws.png, attached)

This is how Evolution does it;
(see image-evo.png, attached)

Is there a way to get HTML to display better? I've installed claws-mail-html2-viewer_2.9.1-1edgy1_i386.deb
but it makes no difference.

Thanks,
Jarlath

---

### Post by colinleroy on 2007-05-03
You have to select the HTML part of the mail, when it is a multipart email, to have Claws render the HTML using the html plugin. Also, installing it via apt-get only makes it available, but you have to load it from Claws (Tools/Plugins menu).

HTH

---

### Post by QwUo173Hy on 2007-05-03
Thanks Colin,

That did the trick!

Jarlath

---

