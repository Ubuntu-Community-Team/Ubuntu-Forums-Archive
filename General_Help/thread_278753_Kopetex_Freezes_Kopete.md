---
title: "Kopetex Freezes Kopete"
date: 2006-10-16
forum: General Help
---

### Post by sonmez on 2006-10-16
Hello,

I have a problem with Kopetex. when I enter $$\sum$$ kopete freezes. 
I use it in Dapper. Can anyone help?

Thanks

---

### Post by KedDeK on 2006-10-22
I posted the same here: [http://ubuntuforums.org/showthread.php?t=263993](http://ubuntuforums.org/showthread.php?t=263993)
But got no reply.

I hope someone has a solution for this.

---

### Post by Hikaru79 on 2006-11-10
I'm having the same problem here; tetex and imagemagick are both installed and working fine, but kopetex crashes.

Help would be greatly appreciated :)

---

### Post by KedDeK on 2006-11-15
Seems nobody knows, or nobody uses KopeTeX :(

---

### Post by environ314 on 2007-01-06
from : [http://bugs.kde.org/show_bug.cgi?id=135997](http://bugs.kde.org/show_bug.cgi?id=135997)

The problem is that /bin/sh is specified as the shell in the kopete_latexconvert.sh script, while /bin/bash really should be used. sh is linked to bash in most distributions, but in Ubuntu it is linked to dash.
It seems that the scripts creator assumed that it would work with any standard shell, while it actually requires bash.

Simply change the first line of /usr/bin/kopete_latexconvert.sh from "#!/bin/sh" to "#!/bin/bash" to make the script work properly.


Anyway, if you enjoy KopeteX, may-you vote for this wish ?
[http://bugs.kde.org/show_bug.cgi?id=107094](http://bugs.kde.org/show_bug.cgi?id=107094)

(The KopeTeX plugin renders LaTeX equations on the fly, but the image rendered is only displayed on the local machine.  For most situations, the other contact is using the MS' official MSN client.  They only see a strange string on the screen, but not the rendered image.)

---

### Post by sienkiwicz on 2007-08-03
That change "!/bin/sh" to "!/bin/bash" thing doesn't work for me, my system is xubuntu 6.06.
I found that the image from tex file is already under my tmp directory, but kopetex can not put it in the message box, i don't know why! i feel maybe some kde package is missing???

---

### Post by Hikaru79 on 2007-08-03
> **sienkiwicz said:**
> That change "!/bin/sh" to "!/bin/bash" thing doesn't work for me, my system is xubuntu 6.06.
I found that the image from tex file is already under my tmp directory, but kopetex can not put it in the message box, i don't know why! i feel maybe some kde package is missing???

Try updating to 7.04; whatever the problem with KopeTeX was, it seems to have been fixed there because I haven't had any more problems with it since Feisty :)

Enjoy!

---

