---
title: "Confused after 2 installs?"
date: 2007-07-06
forum: General Help
---

### Post by sTo0z on 2007-07-06
Hello Ubuntu forumers!

I just ran an install of the server distro for 6.06, I was going through some apt-get installs without any problems, after awhile I decided I wanted to go a completely different route with a project and didn't feel like having all those packages in there anymore so I just decided to reformat and reinstall.

After what seemed like a normal install I am now confused at some behavior going on...

Every time I try to install a package from apt-get it now tells me:

```
Install these packages without verification [y/N]?
```

It never said this before. :\

And if I run apt-get update:

```
W: GPG error: http://security.ubuntu.com dapper-security Release: Unknown error executing gpgv
W: GPG error: http://us.archive.ubuntu.com dapper Release: Unknown error executing gpgv
W: GPG error: http://us.archive.ubuntu.com dapper-updates Release: Unknown error executing gpgv
W: GPG error: http://us.archive.ubuntu.com dapper-backports Release: Unknown error executing gpgv
W: You may want to run apt-get update to correct these problems
```

Yet running apt-get update yields the same results.

This is the same install as before with the same CD, same machine, why are these two problems now occurring?

Any help is appreciated, thank you.

---

