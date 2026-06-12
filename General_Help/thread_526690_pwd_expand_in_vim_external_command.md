---
title: ":pwd expand in vim external command"
date: 2007-08-15
forum: General Help
---

### Post by svenskmand on 2007-08-15
I am trying to use the following command in vim

:!ctags -f ~/.vim/.tags -R .  $JAVA_HOME/src

where the "." should be expanded to "/home/svenskmand/Desktop/Backgammon" as this is the directory that :cd points to, but it apparently doesn't because an entry of ".tags" read

AlphamonDiceStrategy	src/backgammon/domain/alphamon/AlphamonDiceStrategy.java

where it should be

AlphamonDiceStrategy	/home/svenskmand/Desktop/Backgammon/src/backgammon/domain/alphamon/AlphamonDiceStrategy.java

I tryed to use :!ctags -f ~/.vim/.tags -R expand(: pwd)  $JAVA_HOME/src

and variants of this, because : pwd (There should be no space between : and pwd, but there is else the smiles get shown) contains the string that i need, but without luck :(

Any help would be greate as this is very annoying :mad:

---

### Post by manimal on 2007-08-22
Does just `pwd` (without the "expand") work? That's the "`" that is below the ~.

---

