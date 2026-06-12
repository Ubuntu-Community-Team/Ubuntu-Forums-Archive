---
title: "Renaming multiple files"
date: 2019-08-03
forum: General Help
---

### Post by smelheim85 on 2019-08-03
I'm trying to use the utility rename to look for a year, right now 20??.  And add parentheses around it without dropping off the 06, 16, or 18.  Eventually I will be renaming things that are 19??. The issue I'm running into is that the replace section will either add the parentheses are the brackets with the character group in it instead of just adding the parentheses and keeping the numbers.  

Does anyone have suggested because that's just the start but I think I can remove everything from between the year or resolution and the file extension.

---

### Post by Holger_Gehrke on 2019-08-03
```
rename -n 's/\b(20[01][0-9]|19[0-9]{2})\b/($1)/' *
``` should cover both the 20xx and the 19xx case. The option '-n' makes rename print out what it would do without actually renaming anything. Use it  as written (with the option) until you're certain it will do what you want. 
'rename' is written in Perl and uses Perl regular expressions. You can find details (lots and lots of 'em) in the man pages 'perlretut', 'perlrequick', 'perlfaq6', 'perlre', 'perlrebackslash', 'perlrecharclass', and 'perlreref' from the package 'perl-doc'.

Holger

---

### Post by coffeecat on 2019-08-04
*Thread moved to **General Help**.*

The Multimedia Software sub-forum is for help with - well - multimedia software.

---

