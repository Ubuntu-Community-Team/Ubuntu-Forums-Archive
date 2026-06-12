---
title: "[SOLVED] Can't save Kate sessions"
date: 2008-01-25
forum: General Help
---

### Post by Jawnboy on 2008-01-25
Hi I am using Kubuntu 7.10 (KDE 3.5.8 ) and I can't seem to get Kate to save or load sessions?

Has anyone else run into this problem? 

Just to clarify, if I open a few documents and then click on the "Sessions" menu and save as with a session name it seems ok, but when I look under manage sessions or restart Kate and try to load my saved session it is no where to be found.

As a big fan of Kate I would love to be able to switch tasks this way and would appreciate any sort of help. While I am here anyway if anyone knows of any good resources to learn more about Kate that would be great too, other than [http://kate-editor.org/](http://kate-editor.org/) of course :-)

Thanks for your time,

---

### Post by Jawnboy on 2008-01-25
Ok now I just feel silly, I fought with this for half the day and then searched all of the Internet for an answer and ten seconds after posting a question here the answer dawned on me. 

For anyone else that is having a similar problem the owner and group was set to root for some reason, it was the only app directory that was.

So a quick fix;

Open konsole, type 
cd .kde/share/apps 
 ls -l
if the user and group show root then your problem is the same as mine was :-)

sudo chown -R {yourusername} kate
and
sudo chgrp -R {yourusername} kate

Then you are off to the races. 

Ok, I am going to slink off and feel silly some more, have fun everyone.

---

### Post by bowenmark on 2008-03-11
> going to slink off and feel silly some more, have fun everyone

No need to feel silly, same thing happening to me and you saved me lots of time, thanks for posting!

---

