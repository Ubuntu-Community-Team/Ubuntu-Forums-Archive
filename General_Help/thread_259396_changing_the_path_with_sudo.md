---
title: "changing the path with sudo"
date: 2006-09-17
forum: General Help
---

### Post by rjs on 2006-09-17
G'day,

I like to keep my own scripts in ~/local/bin which is usually fine, however for scripts that i need to execute as root i come up against a problem - the path that i use is not the same one as is used by sudo (that is it uses the standard path rather than /home/foo/local/bin:<standard path>).I have created a root session with sudo -s and changed the path there - even exported it but when i exit and go back to my normal shell it still says it can't find my sudoed script in the path.

Any ideas why this isn't working? If i created a root user and changed thier path would that fix it? I thought since sudo is executing something on my behalf AS IF i were root it would use my path rather than roots. And why doesn't changing the path with sudo -s work?

paz,
-rjs.

---

### Post by christhemonkey on 2006-09-17
Hmm, possibly, sudo uses the root home folder.

i.e. /root

---

### Post by rjs on 2006-09-17
yeah, but i added /home/foo/local/bin to root's path not ~/local/bin so that shouldn't matter. And anyway if i exit the root session then start a new root session and say echo $PATH then i get the path without /home/foo/local/bin or /root/local/bin added.

paz,
-rjs.

---

