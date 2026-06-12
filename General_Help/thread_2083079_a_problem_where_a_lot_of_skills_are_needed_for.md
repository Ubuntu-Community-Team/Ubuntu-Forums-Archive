---
title: "a problem where a lot of skills are needed for"
date: 2012-11-11
forum: General Help
---

### Post by then_dude on 2012-11-11
hello everybody. 
 i got a problem, i would like to ask for help.   

SITUATION: 
Years ago i was busy trying to get everybody to work together at university. As a student i asked everybody to send in his notes, and then i distributed them again to make textbooks of it. So i have a huge pile of small text files form a lot of people.   PROBLEM:  a few guys already asked me years later if i had their stuff, cause their computer broke down...  

QUESTION: 
Is it possible that i send to these guys a print of that directory and that they pick the documents they need, send that txt file back and that i put it in a script file which automaticaly puts those files in a directory on my harddisk and the directory carries their name...  

SOLUTION 
i guess there are many solutions to this problem, there might even be a software for that.  But i want to learn a bit. so here i go.   1)i would like to print the content of a directory: 3 levels down and only the directories... i did this with the command : tree -d -l 3 > output.txt this gives me very nice the directory structure, but maybe if i want to put that in script it might be problematic..... so i guess having an overview where the complete directory structure per line is showed might be better ? when i try to do this with ls command i only succed in doing it this was: ls -R -d -l */*/* | grep "^d"   : but this shows all the info offcourse which i would not like to see.....

so can anybody help me a bit with tackling the first problem and indicating if it is possible to write a script that does such complex task.   thanks guys

---

### Post by steeldriver on 2012-11-11
you could start with 

```
find . -maxdepth 3 -type d
```beyond that it's hard to help much until you spend a bit more time defining exactly what you want to do - try to break it down into steps

---

