---
title: "Preventing KDM startup"
date: 2007-01-20
forum: General Help
---

### Post by hotpurple on 2007-01-20
Hi all,

I have a dapper based server, but I'd love to have it boot up without a gui for performance reasons. Without removing the kubuntu-desktop package (I'd still like to have access to the gui through the startx command), how can I get the system to boot into a command line interface?

I've looked at /etc/inittab which already has run level 2 as it's default, but I know it boots to run level 3, so I'm very confused. ](*,) 

I've also tried changing the S99KDM in rc3.d to K99KDM, but it still boots to kdm.

Can anyone shed any light on this?

Cheers

Chris

---

