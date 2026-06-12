---
title: "tab completion mystery"
date: 2007-05-10
forum: General Help
---

### Post by giosue_c on 2007-05-10
I start a terminal window and tab completion for ant doesn't work.

I source my bashrc and tab completion for ant does work.

I have tried moving the following lines 
if [ -f /etc/bash_completion ]; then
            . /etc/bash_completion
fi
to bashrc, bash_profile, and /etc/bash.bashrc

after I change one of these files i do a ctrl+alt+backspace and try again.  Nothing.  I still have to manually source my bashrc for this tab completion to work.

any ideas what could be wrong?

---

### Post by HadroLepton on 2007-05-23
i asume you are using gnome and gnome-terminal.

try following:
open terminal -> edit -> current profile -> title and command -> check "run command as a login shell"

i forgot why i checked that option, but i remember vaguely that it was a similar problem.

---

