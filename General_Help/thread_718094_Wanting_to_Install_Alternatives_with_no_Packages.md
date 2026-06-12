---
title: "Wanting to Install Alternatives with no Packages"
date: 2008-03-07
forum: General Help
---

### Post by KernelKing on 2008-03-07
I just discovered the[ lighttpd]("http://lighttpd.net") alternative to apache.  Up to date Ubuntu binaries exist.  Great.

Now, problem:  [mod_cache]("http://www.linux.com.cn/modcache/") for lighttpd is only supported as a patch to lighttpd or as a patched tarball.  No Ubuntu binaries exist.

Should I 

1) build and checkinstall the mod_cache patched lighttpd tarball,

or

2) try to patch the ubuntu (debian?) package source and rebuild the package

( or

3) submit a request for support of mod_cache to ubuntu lighttpd maintainers? )

I haven't had come across many situations where decently recent binary packages could be installed.  I'm stumped here.

Thanks.

---

### Post by dcstar on 2008-03-08
> **KernelKing said:**
> I just discovered the[ lighttpd]("http://lighttpd.net") alternative to apache.  Up to date Ubuntu binaries exist.  Great.

Now, problem:  [mod_cache]("http://www.linux.com.cn/modcache/") for lighttpd is only supported as a patch to lighttpd or as a patched tarball.  No Ubuntu binaries exist.

Should I 

1) build and checkinstall the mod_cache patched lighttpd tarball,

or

2) try to patch the ubuntu (debian?) package source and rebuild the package

( or

3) submit a request for support of mod_cache to ubuntu lighttpd maintainers? )

I haven't had come across many situations where decently recent binary packages could be installed.  I'm stumped here.

Thanks.

What is wrong with doing option 1?

---

### Post by KernelKing on 2008-03-08
1) checkinstall -ing the tarball would be my clear option if there wasn't a relatively up-to-date source distribution that i could patch and rebuild.

Since 2) seems to be viable -- and I don't really understand the difference between a maintained package and raw tarball make & install -- my conservative instinct is to stick as close to the distro process as possible.  As an example of my ignorance, when i read the changelog for the ubuntu lighttpd package, I see changes for specific memory problems.  Do these mirror bugs and fixes made by the original source developers??  I guess I need to understand -- probably in another thread -- what makes a ubuntu package a ubuntu package, aside from it as a means of managing and cataloguing the software installed.

---

