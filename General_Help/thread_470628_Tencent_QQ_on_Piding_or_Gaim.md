---
title: "Tencent QQ on Piding or Gaim"
date: 2007-06-11
forum: General Help
---

### Post by precinto on 2007-06-11
I can't log in, it keeps telling me my password is not correct. 

Does some know a way around this? I couldn't find anything on the forums or elsewhere. It seems "qq" is too short for a query.

Thanks.

---

### Post by precinto on 2007-06-12
In case anyone is having the same problem, it seems to be a change in the QQ protocol. 

To solve it you can download the file libqq.so from [this page]("http://blog.chinaunix.net/u1/39544/showart_317460.html") into your home folder and do "sudo cp ~/libqq.so /usr/lib/purple-2/libqq.so" to fix it.

---

### Post by Chang An on 2007-06-14
HI,
I have the same problem.  When I put in the script I get this error message

cp: cannot create regular file `/usr/lib/purple-2/libqq.so': No such file or directory

any ideas?  Thank you

---

### Post by precinto on 2007-06-16
&#20320;&#22909;, Chang An. I forgot to say that this will only work with Pidgin and won't with previous versions (I guess it's because of the renaming). You could install Pidgin 2.0.1 from getdeb.net and then apply the patch.

However two days ago version 2.0.2 was released, and according to the release notes it should be fixed on the new version. Unfortunately there aren't still .debs to install it AFAIK. You can [compile]("http://ubuntuforums.org/showthread.php?t=474863") it from source or wait for the debs.

---

### Post by Chang An on 2007-06-22
&#35874;&#35874; precinto, I got version 2.0.2 from getdeb and it worked fine for about a week and now the same problem came up.  Any ideas?

---

### Post by precinto on 2007-06-23
I'm glad it helped. I'm still using version 2.0.1 with the aforementioned patch applied and it *seems* to work (I still have no contacts... but I'm allowed to sign in=.

Give it a try. ; )

---

