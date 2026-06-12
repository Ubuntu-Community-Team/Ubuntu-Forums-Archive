---
title: "Installing Firefox 3.0 RC2"
date: 2008-06-05
forum: General Help
---

### Post by Justgeoo on 2008-06-05
I would like to install the latest version of Firefox 3.0, which is a release candidate, but I haven't found any how-to's for installing this candidate. Is there anyone who has done this procedure yet? If so how? 

Any instructions will be greatly appreciated. 

Thank you

---

### Post by knavarathna92 on 2008-06-05
I would strongly advise you to wait until we get the official update.  I did something like this for RC1 and i ended up messing up xulrunner, which I was only able to correct by forcing the old version.  Btw, RC2 doesn't change much from RC1, just a minor security issue.  

That being said, if you want to completely ignore me, here's a link for RC2 

[http://blog.rosanegra.org/2008/06/02/how-to-install-firefox-3-rc-2-on-ubuntu-hardy/](http://blog.rosanegra.org/2008/06/02/how-to-install-firefox-3-rc-2-on-ubuntu-hardy/)

---

### Post by another_sam on 2008-06-06
from
[http://brainstorm.ubuntu.com/idea/8808/](http://brainstorm.ubuntu.com/idea/8808/)
[https://wiki.ubuntu.com/MozillaTeam/PreviewArchives](https://wiki.ubuntu.com/MozillaTeam/PreviewArchives)

wait until final release of firefox 3 or go to

System > Administration > Software Sources > Third-Party Software
and add
deb [http://ppa.launchpad.net/mozillateam/ubuntu](http://ppa.launchpad.net/mozillateam/ubuntu) hardy main universe

and then go to

System > Administration > Update Manager
Check, ... and Install Updates

---

### Post by Joeb454 on 2008-06-06
If I remember correctly - the LaunchPad ppa archive can cause issues. I know that FF3 RC1 is in hardy-proposed, so you could enable that repo - install firefox 3, and then disable it again :) This is what I did

---

### Post by Yellow Pasque on 2008-06-06
I suggest checking out Swiftweasel (link in sig).

The 3.0RC2 .deb should be out in a few days. He already has the .tar.gz packages.
> June 5, 2008
I have just started building 3.0 RC2 tarballs. The test build I did looks real nice.

---

