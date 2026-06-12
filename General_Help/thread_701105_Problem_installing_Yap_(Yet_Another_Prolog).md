---
title: "Problem installing Yap (Yet Another Prolog)"
date: 2008-02-19
forum: General Help
---

### Post by apach on 2008-02-19
Hi,

Did anyone have any experience installing Yap on Ubuntu?
I have no problem while making it, but "make install" throws errors.
...
% chr(start('chr_translate_bootstrap1.chr'))
% EXISTENCE ERROR- procedure datime/2 is undefined, called from context  prolog:get_time/1
%                  Goal was system:datime(_97294,_97295)
make[2]: *** [chr_translate_bootstrap1.pl] Error 1
make[2]: Leaving directory `/home/mohammad/ggp/ggp/Yap/LGPL/chr'
make[1]: *** [install_data] Error 2
make[1]: Leaving directory `/home/mohammad/ggp/ggp/Yap'
make: *** [.done_yap] Error 2

I'm using gcc version 4.1.2 .

I googled a lot, but I found no answer. Any answer, idea, or suggestion is highly appreciated.

---

### Post by apach on 2008-02-21
Using
   CFLAGS='-O3 -Wall -fno-stack-protector'
with ./configure resolved the problem.

It seems that it's a problem with Ubuntu Feisty Fawn.

---

