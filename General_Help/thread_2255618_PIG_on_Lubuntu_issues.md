---
title: "PIG on Lubuntu issues"
date: 2014-12-06
forum: General Help
---

### Post by Shamik_Biswas on 2014-12-06
Hi,

I am trying to run PIG on Hadoop. I have installed it and updated the .bashrc file accordingly. Now :

If I run Pig in local file system...it successfully enters the Grunt shell...

[B][I]hduser@shamik-HP-Pavilion-g6-Notebook-PC:~$ pig -x local
grunt> ...[/I][/B]


However, when I do : 

hduser@shamik-HP-Pavilion-g6-Notebook-PC:~$ ***[COLOR=#ff0000]pig -x mapreduce[/COLOR]***
2014-12-06 19:13:54,346 [main] [COLOR=#ff0000][B]ERROR org.apache.pig.Main - ERROR 2999: Unexpected internal error. Failed to create DataStorage
Details at logfile: /home/hduser/pig_1417873434085.log[/B][/COLOR]

[B]I got the above error.

Please help. Thanks in advance.
[/B]

---

### Post by nerdtron on 2014-12-06
Well, what does the log file say? 
[COLOR=#ff0000]**Details at logfile: /home/hduser/pig_1417873434085.log**[/COLOR]

---

