---
title: "Beagle with .DOC support"
date: 2005-10-25
forum: General Help
---

### Post by benplaut on 2005-10-25
the title says it all... how the heck to i get it to search through .DOC files? it [Beagle's site] says it's supported, but i think Ubuntu's "nothing but free" is keeping it out.

Any suggestions?

---

### Post by benplaut on 2005-10-26
bumpie?

---

### Post by evan1221 on 2005-10-27
From the beagle wiki ([http://beaglewiki.org/Optional_prerequisites](http://beaglewiki.org/Optional_prerequisites)) I gather that you need 'wv', version 1.0.3 and patched by this: [http://users.avafan.com/~fredrik/beagle/wv-libole2-readonly.patch](http://users.avafan.com/~fredrik/beagle/wv-libole2-readonly.patch)

checking with apt-cache shows version 1.0.2 in universe... So I guess you have to patch & compile yourself

hope this helps

Evan

---

