---
title: "Midgard CMS on edgy?"
date: 2007-10-29
forum: General Help
---

### Post by mwhite41 on 2007-10-29
Hi

I'm trying to check out the latest midgard CMS release on a home server.

I tried to follow the (simple) instructions at:

[http://www.midgard-project.org/documentation/ubuntu/](http://www.midgard-project.org/documentation/ubuntu/)

And added the appropriate lines to sources.list.

After I did the apt-get update, i tried to:

apt-get install midgard-data

And got the following errors:

Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  midgard-data: Depends: php5-midgard (>= 1.8.1) but it is not going to be installed or
                         php4-midgard (>= 1.8.1) but it is not going to be installed
E: Broken packages

Has anyone successfuly installed midgard on Ubuntu using binary releases?

Thanks in advance

Mark

---

