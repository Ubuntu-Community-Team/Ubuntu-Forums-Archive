---
title: "Upgraded to Ubuntu 14.10. Now git clone fails"
date: 2014-12-30
forum: General Help
---

### Post by redmage123 on 2014-12-30
Hello all, 

I just upgraded to Ubuntu 14.10 on my X86-64 system.  However, when I try to do something like:

git clone [https://github.com/sontek/dotfiles.git](https://github.com/sontek/dotfiles.git)

I get the following error:

Cloning into 'dotfiles'...
git-remote-https: symbol lookup error: /usr/lib/x86_64-linux-gnu/libhogweed.so.2: undefined symbol: __gmpn_cnd_add_n

I googled for this.  The problem appears to be that git is looking for a symbol defined in libgmp.6.0 and the current
library in /usr/lib/x86-64-linux-gnu is libgmp10.2.0.  I am therefore assuming that the libgmp upgrade removed the
symbol that is causing the git clone error.  

Is there a fix for this? 

Thanks

 -- redmage123

---

### Post by mc4man on 2014-12-30
I don't use 14.10 but out of curiosity what does this show?
```
ldd /usr/lib/x86_64-linux-gnu/libhogweed.so.2
```

---

### Post by redmage123 on 2014-12-30
ldd /usr/lib/x86_64-linux-gnu/libhogweed.so.2

	linux-vdso.so.1 =>  (0x00007fff89958000)
	libnettle.so.4 => /usr/lib/x86_64-linux-gnu/libnettle.so.4 (0x00007ffe48c29000)
	libgmp.so.10 => /usr/local/lib/libgmp.so.10 (0x00007ffe489b2000)
	libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007ffe485ec000)
	/lib64/ld-linux-x86-64.so.2 (0x00007ffe490a6000)

---

### Post by mc4man on 2014-12-30
> libgmp.so.10 => [COLOR="#FF0000"]/usr/local[/COLOR]/lib/libgmp.so.10 (0x00007ffe489b2000)
While that's the currently correct version it was user installed.
Try removing the libgmp libs in /usr/local/lib (& any other libgmp files in /usr/local/*, if any
Then run a 
```
sudo ldconfig
```
and recheck

You want to use Ubuntu repo version - 
> ~$ ldd /usr/lib/x86_64-linux-gnu/libhogweed.so.2
	linux-vdso.so.1 =>  (0x00007fff8666f000)
	libnettle.so.4 => /usr/lib/x86_64-linux-gnu/libnettle.so.4 (0x00007f53e7a4c000)
	libgmp.so.10 =>[COLOR="#0000CD"] /usr/lib/x86_64-linux-gnu/libgmp.so.10[/COLOR] (0x00007f53e77d8000)
	libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f53e7411000)
	/lib64/ld-linux-x86-64.so.2 (0x00007f53e7ecc000)

---

### Post by redmage123 on 2014-12-30
Yep.  That fixed it.  Thanks for your help.

---

### Post by mc4man on 2014-12-30
Great - Do make sure that all gmp files in /usr/local/* are gone. You don't want any sources you build to use any .h or a .pc for a now non-existent .so

---

