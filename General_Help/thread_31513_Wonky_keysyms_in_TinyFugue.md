---
title: "Wonky keysyms in TinyFugue"
date: 2005-05-03
forum: General Help
---

### Post by rch on 2005-05-03
No matter what term I try to run Tinyfugue in, the keysyms seem wonky. When I press numpad 1-9 I get this:

% #442: key_nkp1: no such command or macro                                     
% #440: key_nkp5: no such command or macro                                     
% #441: key_nkp9: no such command or macro                                     
% #434: key_f5: no such command or macro                                       
% #435: key_f6: no such command or macro                                       
% #436: key_f7: no such command or macro                                       
% #438: key_f9: no such command or macro                                       
% #290: key_nkp8: no such command or macro                                     
% #292: key_nkp9: no such command or macro

nkp1,8, and 9 seem the only ones that are in the right places. 

The strange f-keys on the numpad don't correspond to my real F keys:

% #310: key_f5: no such command or macro                                       
% #312: key_f6: no such command or macro                                       
% #314: key_f7: no such command or macro                                       
% #318: key_f9: no such command or macro

The problem here is(aside from the ...wonkiness), I can't bind the "numpad-f9" without also binding the real f9 key to something. 

Anyone had a problem like this in any application?

---

### Post by rch on 2005-05-11
-bump-

Anyone?

---

### Post by b-llwyd on 2008-06-18
Hmm, i just bumped into this problem myself, although we must be years and ubuntu/tf versions apart. It used to work ok for me in ubuntu 7.10/openbox/urxvt, but now with 8.04/gnome/urxvt, it shows the same syndrome as your setup.

The numeric pad didnt work at all in Gnome-terminal, but this is a half-way success at least.

Could it be something about the TERM environment?

---

