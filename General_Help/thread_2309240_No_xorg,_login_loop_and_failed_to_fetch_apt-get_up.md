---
title: "No xorg, login loop and failed to fetch apt-get update"
date: 2016-01-08
forum: General Help
---

### Post by lizpy66 on 2016-01-08
OK where to begin. Yesterday I tried logging in and got a login loop so opened up a tty using alt f3 and tried stuff people said. One problem I noticed off the bat was fglxr(might be a typo on my part ) always had an error. So I looked around and decided to uninstall xorg and reinstall. It's been Uninstalled but I can't install it because every time I hit y to install when it asks to it always says failed to fetch. I know I might have to do a fresh install but I'm hoping there's a chance to not as I have over a quarter of a terabyte alone of family pictures and engagement plans on my laptop so want to make sure first

Thanks in advance

---

### Post by Hodevah on 2016-01-08
hi. 
For when you say you "tried stuff people said" what exactly do you mean by that? What commands?
Did you try
> sudo chown lizpy66.lizpy66 .Xauthority
for the login loop. 

can also do with colon, instead of period between your username.

---

