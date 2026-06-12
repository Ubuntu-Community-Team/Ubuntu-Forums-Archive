---
title: "How to comment a line in python file using bash?"
date: 2019-03-19
forum: General Help
---

### Post by suaro on 2019-03-19
[FONT=arial]Hi Everyone,

I'm trying to insert a remark '#' character at the beginning of a line where the first character starts - and have everything else automatically moved over by 1.
For example:  Below is line 83 in a file called Syncqueue.py.  The number to the left is just showing the line number and not part of the file itself:
[/FONT][FONT=courier new][FONT=arial]
**Original**[/FONT]

[/FONT]
[FONT=courier new] 83      logger.debug("Syncqueue: %s", pformat(syncqueue))[/FONT]
[FONT=courier new]
[FONT=arial]Now I want to place a remark at the 'l' location which is the position of the first character on the line.

When I issue the following:[/FONT]

[/FONT]
[FONT=courier new]      sed -i '83 s/^/#/' Syncqueue.py[/FONT]

[FONT=courier new]
[FONT=arial]It adds the '#' to the beginning of the line rather than at column 4 where the characters actually start.[/FONT]
 [/FONT]
[FONT=courier new] 83 **#**    logger.debug("Syncqueue: %s", pformat(syncqueue))[/FONT]

[FONT=courier new]
[FONT=arial]I'm trying to determine how to add the '#' at the place where the first characters starts rather than at the beginning of a line.  

[/FONT][/FONT]
[FONT=arial] Goal:[/FONT]

[FONT=courier new]  83     **#**logger.debug("Syncqueue: %s", pformat(syncqueue))[/FONT]
[FONT=courier new] 
[FONT=arial]Any tips greatly appreciated!
Thank you so much[/FONT][/FONT]

---

### Post by suaro on 2019-03-19
I've figured out an easier way by just replacing the word 'logger' with '#logger', rather than getting caught up with explicitly adding the '#'

[FONT=courier new]sed -i '83s/logger/#logger/' Syncqueue.py[/FONT]

---

