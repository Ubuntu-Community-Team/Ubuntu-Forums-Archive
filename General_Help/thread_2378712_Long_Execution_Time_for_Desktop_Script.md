---
title: "Long Execution Time for Desktop Script"
date: 2017-11-26
forum: General Help
---

### Post by electrosteam on 2017-11-26
I use LibreCad 2.1.2 on Lubuntu 17.04 with the mouse on the LHS, so the Escape key in the top LHS of the keyboard is not convenient.
I wrote a Desktop Entry script to re-allocate the Menu key, the top RHS key on my 2002 build Dell Inspiron laptop 5150, to Escape to allow the right hand to cancel an operation that the left hand on the mouse had started.

Actually two scripts, one to swap and the other to swap back.
They work a treat, but, they seem to take an excessively long time ( 11 secs ) to execute considering the simple script.
The first script:

```

[Desktop Entry]
Name = Menu to Escape
Exec=/bin/bash -c ' xmodmap -e "keycode 135 = Escape" '
Type = Application
Terminal = True
# copy in $Home/local/share/applications

```

The second script exchanges 'Escape' and 'Menu'.

Note the reminder about copying to .../share/applications.

Can anyone shed any light on why so long ?
Have I got something wrong ?
John.

---

