---
title: "Building rsync on Lucid"
date: 2013-01-17
forum: General Help
---

### Post by mholmes on 2013-01-17
Hi all. 

I'm having problems with rsync, caused by using the 3.0.7 client against a server running 3.0.8. (A recent upgrade on the server precipitated problems which I see in bug reports dating back years.) 

I'm on Lucid and not ready to upgrade, and there's no backport or ppa for rsync, so I'd like to build rsync 3.0.8 or 3.0.9 on Lucid. Does anyone have any experience with this? Is it feasible?

All help appreciated,
Martin

---

### Post by dcstar on 2013-01-19
> **mholmes said:**
> Hi all. 

I'm having problems with rsync, caused by using the 3.0.7 client against a server running 3.0.8. (A recent upgrade on the server precipitated problems which I see in bug reports dating back years.) 


See if you can install the **rsync** package from later releases:

[http://packages.ubuntu.com/search?keywords=rsync&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=rsync&searchon=names&suite=all&section=all)

---

### Post by mholmes on 2013-01-19
It looks as though rsync 3.0.8 depends on libpopt0 1.16, and Lucid only has 1.15, so I might be getting into a dependency nightmare there. I'm looking for another solution before I go down this road. Any advice appreciated!

Cheers,
Martin

---

