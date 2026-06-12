---
title: "How does lightdm-session call ~/.profile with bash as opposed to /bin/sh"
date: 2013-11-17
forum: General Help
---

### Post by helloworld1215 on 2013-11-17
It is specified in lightdm-session that it is a #!/bin/sh. 
1. It appears that for some users lightdm-session is called with bash and for  others it is with some other shell that errors on bash statements.
  2. When does the user's shell get called?
3. Please specify what the designated shell on the latest revision is for lightdm-session. I am running 12.04

[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/962270](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/962270)

RESOLVED: X session profile execution is done by lightdm-session which is  executed by /bin/sh by default. I made a mistake in observing behavior  of some users allegedly executing with /bin/bash.

---

