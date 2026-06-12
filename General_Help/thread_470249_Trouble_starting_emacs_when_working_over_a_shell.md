---
title: "Trouble starting emacs when working over a shell"
date: 2007-06-10
forum: General Help
---

### Post by infernon on 2007-06-10
Hello, 

I have installed emacs and am trying to start it after opening an SSH session into my remote Ubuntu box.  I am receiving the following error message:

emacs: Terminal type xterm-256color is not defined.
If that is not the actual type of terminal you have,
use the Bourne shell command `TERM=... export TERM' (C-shell:
`setenv TERM ...') to specify the correct type.  It may be necessary
to do `unset TERMINFO' (C-shell: `unsetenv TERMINFO') as well.

I have tried uninstalling and reinstalling emacs to see if it corrects the problem, but it does not.

---

### Post by infernon on 2007-06-11
I failed to mention one important thing and that was central to this problem.

I was using iTerm from a Mac.  I had the common sense to start up Terminal after I posted this (finally) and found that the problem didn't exist when trying to start emacs.  After looking at the Preferences tab in Terminal, I realized that the terminal emulation was set to xterm-color.

I then Googled and found this page:

[http://www.unixguide.net/linux/faq/09.02.shtml](http://www.unixguide.net/linux/faq/09.02.shtml)

The command at the very bottom resolved my issue when working with iTerm.  I hope that this is helpful for someone else.

---

