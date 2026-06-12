---
title: "Fix for &quot;no gcc compiler found&quot;"
date: 2007-06-14
forum: General Help
---

### Post by Annihilist on 2007-06-14
Recently I had this problem when trying to configure and make a program I was installing, and everything I found on the forums seemed to deal with the obvious solutions but not the one I ended up with. Basically it turned out that even thou I have build-essentials installed on my computer when I actually looked in the /usr/bin folder it turned out that the gcc link was broken (it was pointing to a version that I didnt have). So I used apt to remove gcc, then reinstalled and it worked. 

Hopefully this helps save at least one person the hour or so that I spent looking for the answer :)

---

