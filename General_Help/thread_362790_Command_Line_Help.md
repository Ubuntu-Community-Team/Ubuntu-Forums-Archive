---
title: "Command Line Help"
date: 2007-02-16
forum: General Help
---

### Post by subiet on 2007-02-16
I need help to make shell script.

say, i  need to 
*Delete the first character of line number 'n' in a text file ~/sample.txt
*Insert a character to line number 'n' in a text file ~/sample.txt


what are the ways to do it? (ofcouse without using a gui)

---

### Post by gradedcheese on 2007-02-16
I don't have a solution off the top of my head, but I will think about it.  Meanwhile, take a look at sed ("man sed") and see if you can use it to do something like this.  The brute-force way is pretty easy (as usual), just read line by line until you find the line number you're looking for, do the insert or delete, and keep going, meanwhile you write to an output file.

---

