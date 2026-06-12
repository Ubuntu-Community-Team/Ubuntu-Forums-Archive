---
title: "compiling kritasketch"
date: 2015-02-02
forum: General Help
---

### Post by monkeybrain20122 on 2015-02-02
Hi,

I am trying to compile krita 2.8.7 following this tutorial [http://www.davidrevoy.com/article193/guide-building-krita-on-linux-for-cats#c1422760448-1](http://www.davidrevoy.com/article193/guide-building-krita-on-linux-for-cats#c1422760448-1) (adding 'git checkout calligra /2.8' after cloning the git repo would switch to the 2.8 branch) While krita is built successfully I cannot build kritagemini and kritasketch. The krita website says these are now paid applications available from steam, but the repo have them (can be installed seperately) and in Fedora they are installed along with kritaso they should complied from the same source codes. Tried the cmake option  -DPRODUCTSET=GEMINI it said  unknown productset compile with the option -DPRODUCTSET=CREATIVE doesn't produce kritasketch either.

Any idea? Thanks.

Edited: Can a moderator please change the title to kritasketch instead of kitrasketch. I made a typo, thanks.

---

### Post by monkeybrain20122 on 2015-02-02
From the krita forum 'Sketch and Gemini are broken due to Multiple Documents at the moment.  We'll get them back up and running as soon as possible, but for now only  desktop works. ' Also, it seems that only for Ubuntu kritasketch is required for sketch brush because of the way that Ubuntu/Debian packages krita, it is not needed if one compiles from source.

---

