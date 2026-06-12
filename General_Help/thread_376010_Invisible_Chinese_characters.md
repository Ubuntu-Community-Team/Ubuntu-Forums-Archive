---
title: "Invisible Chinese characters"
date: 2007-03-04
forum: General Help
---

### Post by precinto on 2007-03-04
Hello. 

My scim was broken for some time, until I finally managed to fix it. However now something strange happens: some characters are not displayed in some apps. For example, if I were to write &#20320;&#22909; on gaim or gedit, the second character would be invisible, although scim lists it in the lookup table. The same character appears correctly on Firefox and, for example, the terminal.

Does someone have an idea of what may be going on?

Thanks.

---

### Post by dvstin on 2007-05-15
I had this exact problem, but i seemed to have fixed it by

[LIST=1]
[*]remove ttf-arphic-ukai ttf-arphic-uming
[*]restart X
[*]install ttf-arphic-ukai ttf-arphic-uming
[*]restart X
[/LIST]

not sure why it worked, or what the problem was, but give it a try.

---

