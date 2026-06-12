---
title: "wxdownload fast not working any more"
date: 2007-09-04
forum: General Help
---

### Post by eklektik on 2007-09-04
hi to the community!

i installed wxdownload fast 0.6.0 from the [http://getdeb.net](http://getdeb.net) and started to test it. after trying to download rapidshare.com file (im not premium), the program crashed... i went to the start menu to start the program, but all it does is starts for about half a second (way little time to actually do sth) and crashes every time when i want to use it. i manage to catch a glimpse of the gui and im able to see that the url i wanted to download in the first place is still there causing somehow the program to collapse. tried to reinstall, but the problem remains exactly the same, which led me to conclusion(!?) that the possible problem could be in some library or package dependent to wxdfast. of course, i dont know which one...:confused:
i did some googling and find the guy with the same unresolved problem [http://sourceforge.net/tracker/index.php?func=detail&aid=1728900&group_id=106901&atid=645951](http://sourceforge.net/tracker/index.php?func=detail&aid=1728900&group_id=106901&atid=645951)
i thought that maybe wxdfast has some queue file which can be edited in order to flush the current download job which is causing problems. or performing complete removal of the program with the download jobs.
if only i knew where the queue file or something similar is, so i could delete or edit it...

hope that some ubuntu guru will come with the solution to this riddle. :guitar:

thnx :)

---

### Post by Happy_Man on 2007-09-04
Could you try starting the application from a terminal (Applications --> Accessories --> Terminal) and post the output here? ```
wxdownload
```

---

### Post by eklektik on 2007-09-04
btw, bash command is **wxdfast**  :)

[I]ekle@server:~$ wxdownload
bash: wxdownload: command not found
ekle@server:~$ wxdfast
wxdfast: relocation error: wxdfast: symbol _ZlsR8wxStringRK16wxLongLongNative, version WXU_2.6 not defined in file libwx_baseu-2.6.so.0 with link time reference
ekle@server:~$ [/I]

m8, thnx 4 help

---

### Post by eklektik on 2007-09-10
the solution is compiling your own deb package from source code... 
there is great howto on this page -> [http://forum.digital-digest.com/archive/index.php/t-81066.html](http://forum.digital-digest.com/archive/index.php/t-81066.html)

i hope i helped some1!

bye

---

