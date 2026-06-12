---
title: "Aliases that are permanent....how?"
date: 2014-02-08
forum: General Help
---

### Post by bc.haynes on 2014-02-08
I use a few long commands and I have used aliases for them, but, when I close the Terminal, they go away. I have tried editing .bash_aliases and .bash_aliases~ but it has no effect (and .bash_aliases~ is read-only). I do have one alias in these files that comes back when I re-enter Terminal....just one. Can I do more? Or will I have to leave the Terminal open all dya (& then have to reload them the next day)?

I found this:[http://ubuntuforums.org/showthread.php?t=204382&highlight=Aliases+permanent....how%3F](http://ubuntuforums.org/showthread.php?t=204382&highlight=Aliases+permanent....how%3F) but it is from 2006, and I don't know if it is up-to-date. Can I go by this? :confused:

---

### Post by Bashing-om on 2014-02-08
bc.haynes; Hey ;

Sure that link should still be valid to make an alias.
do:
```

cat ~/.bashrc

```
(or open it in gedit !) and see:
> 
# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

It appears "/usr/share/doc/bash-doc/examples" is no longer extent, or has been moved !

But the idea is the same.

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by Dennis N on 2014-02-08
**~/.bash_aliases** is where you write your alias definitions to reuse them. Example of an alias definition:

**[FONT=Courier New]alias dosgames='dosbox /home/dn/dosgames/'[/FONT]**

here, dosgames is the alias I would type in the terminal to run the command on the right of the =

When you close the terminal, all aliases are forgotten by bash. When the terminal is started again, **~/.bash_aliases** is read again by bash and these definitions are restored.

---

### Post by Dennis N on 2014-02-08
Some more examples from my ~/.bash_aliases

```
alias acl='wine "c:\program files\Litsoft\Across Lite\ACROSSL.EXE"'
alias fo='wine "c:\program files\Parsons Technology\Family Origins\FOWin32.exe"'
alias ds='wine "c:\program files\DST_SUNS\dst_suns.exe"'
alias dosgames='dosbox /home/dn/dosgames/'
alias tcv='dosbox /home/dn/dosgames/TCV/COVE.EXE'
alias castle='dosbox /home/dn/dosgames/brain/BRAIN.EXE'
alias island='dosbox /home/dn/dosgames/brain2/BRAIN2.BAT'
alias brix='dosbox /home/dn/dosgames/brix/BRIX1.EXE'
alias orion='dosbox /home/dn/dosgames/moo/ORION.EXE'
alias chess='dosbox /home/dn/dosgames/chess/GMCHESS.EXE'
alias pcft='dosbox /home/dn/dosgames/pcft/ENFT.BAT'
alias midimusic='timidity ~/music/midi/ultima8'
alias ranwhen=ranwhen.py
```

---

### Post by bc.haynes on 2014-02-08
Thank you both for your input.

This was [SOLVED] by using the instructions in the above link in Post #1.

---

### Post by Bashing-om on 2014-02-08
bc.haynes; No problem !

We are all in this together.
One of these days as you keep studying - you will shed light our way !

[INDENT]all for one and 1 for all
[/INDENT]

---

### Post by bc.haynes on 2014-02-08
Great philosophy.

---

### Post by deadflowr on 2014-02-08
Added, you don't need to close the terminal for the aliases in .bash_aliases to take affect.
simply run
```
source .bashrc
```
and bash will reload with the newly added aliases available.

---

