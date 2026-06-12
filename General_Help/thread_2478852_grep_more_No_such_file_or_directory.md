---
title: "grep: more: No such file or directory"
date: 2022-09-06
forum: General Help
---

### Post by raleigh3 on 2022-09-06
This is not working.

```
read -p "Enter text to search for : " n1
read -p "Enter directory to start seach at. " n2

grep -r $n1 $n2 more
```

```

```
andy@7 ~/Downloads> test.sh
Enter text to search for : fax
Enter directory to start seach at. /home/andy/Downloads 
grep: more: No such file or directory
Using ~/Downloads does not work either.

I am entering the right directory.

---

### Post by yetimon_64 on 2022-09-06
With respect to the last line of your code; try piping the output of grep to more.
Example...```
grep -r $n1 $n2 **|** more
```
If you are expecting a lot of output and want to pass it to the "more" command it needs the pipe "|" symbol. I suspect this is why your current command is failing; you have missed the pipe in the command.

Edit: I just noted the pipe symbol when posted here shows as a solid vertical line, on my keyboard it is a broken vertical line. It is above the backslash, ie. press "shift + backslash" to get the pipe symbol.

---

### Post by Bashing-om on 2022-09-06
raleigh3; Hello

Is "more" the utility to read the output of "grep" ? Or the name of some directory within /home/andy/Downloads ?

I suspect that you want "more" to page through grep's output.
In this case try to pipe [ | ] to more,
```

grep -r $n1 $n2 | more

```

see in terminal:
```

man pipe 

```

[INDENT]hope this helps
[/INDENT]

---

