---
title: "installing zlib - atmospheric model"
date: 2014-06-20
forum: General Help
---

### Post by moehbon on 2014-06-20
Hi everyone, 

I am about to configure a atmospheric model, however I need to install some libraries before I move on to the next level. Thus, I have been strugling to configure zlib, because I need to configure it using prefix /opt/intel. However, this is not happening and it keep me showing this error:

Compiler error reporting is too harsh for ./configure (perhaps remove -Werror).
** ./configure aborting.

I was doing these steps: 
 e x p o r t    C C = g c c
 e x p o r t    C F L A G S = '  O 3    x H o s t    i p '
 tar -xf zlib-1.2.8.tar
 c d    zlib-1.2.8
 . / c o n f i g u r e    --p r e f i x = / o p t / i n t e l

Does anybody know what is going on? 

thanks a lot

---

