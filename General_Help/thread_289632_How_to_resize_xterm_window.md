---
title: "How to resize xterm window"
date: 2006-10-31
forum: General Help
---

### Post by pinoyskull on 2006-10-31
I use xterm as my terminal choice.  The default xterm window when envoking it thru Run... is small (in my perspective). How do i change the window size of xterm?

---

### Post by karlbowden on 2006-10-31
try putting in you: ~/.bashrc

```
alias xterm='xterm -geometry 200x80'
```

Experiment with the size you prefer. The size is in characters. Ie. 200 chars wide and 80 chars high.

That will work if the run command respects alias'. You may need to log out and then back in for the changes to take effect though.

*edit: spelling mistake

---

### Post by pinoyskull on 2006-10-31
thanks a bunch **karlbowden** that was helpful :)

---

### Post by RichJacot on 2006-10-31
Putting the above alias .bash_aliases file will also work.

---

### Post by kent41 on 2006-10-31
> **karlbowden said:**
> try putting in you: ~/.bashrc

```
alias xterm='xterm -geometry 200x80'
```

Experiment with the size you prefer. The size is in characters. Ie. 200 chars wide and 80 chars high.

That will work if the run command respects alias'. You may need to log out and then back in for the changes to take effect though.

*edit: spelling mistake

Hi I need to enlarge the xterm but when I add your code it did not work.
Is there a certain place in the script to add the code?

In my application a script starts xterm.

Thanks

---

### Post by streeto on 2006-10-31
Find if you have a .Xdefaults file in your $HOME. Create it if you don't have one. Add this line:

```
XTerm.*.geometry:80x59
```

or

```
XTerm.*.geometry:80x59+482+0
```

That is, WIDTHxHEIGHT+XOFFSET+YOFFSET, with your own values. WIDTH and HEIGHT are in chars, and X/YOFFSET are in pixels. Then, make sure a this file is honoured by your window manager, some just ignore it. If it is your case, find your 'autostart' equivalent and add this line:

```
xrdb ~/.Xdefaults
```

That's it. This makes sure ALL xterms open with the correct geometry, even if it was not called from a shell. Every X program may have some of its options --generally the ones related to display-- configured by Xdeafults. Just 'man xterm' or 'man your_x_program' to find which options are available.

---

### Post by kent41 on 2006-10-31
I did not have a .Xdefaults in my $HOME dir so I created one as you suggested  and put the code in the .Xdefaults file
```

XTerm.*.geometry:100x40
```
and it works great.

Thank you soooo much for the help I have many icons that run scripts to provide me with info on my computers health.

---

