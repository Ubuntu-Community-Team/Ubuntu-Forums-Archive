---
title: "postdrop: warning: unable to look up public/pickup: No such file or directory"
date: 2008-06-26
forum: General Help
---

### Post by josh.grossman on 2008-06-26
I'm having trouble sending mail with postfix sendmail. I get the message: 

postdrop: warning: unable to look up public/pickup: No such file or directory

I have two ubuntu machines on the same subnet. One that I set up can send mail no problem. The other was already built has this problem. The one I setup did not have postfix, so I installed it with apt-get. On the other, postfix was there, but not working, so I did:

sudo apt-get purge postfix
sudo apt-get install postfix

installing it as being directly on the net, so as to have an smtp server setup. I then then cat a file into sendmail -t and get the message listed above. The file is from the other system which works.

I tried telet to an external smtp server on port 25 and I can connect. I also tried ping mail.google.com. That also worked.

Any helpful hints would be gratefully appreciated.

Regards,

Josh

---

### Post by josh.grossman on 2008-06-26
problem solved. I checked ps for the postfix server and didn't see it. /etc/init.d/postfix seemed to behave correctly, but did not load it. I rebooted and all is good. hmmm, isn't that supposed to be how you fix a windoze machine. ;-)

---

