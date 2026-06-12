---
title: "Sed Command with -n"
date: 2006-07-19
forum: General Help
---

### Post by pat270881 on 2006-07-19
hello,

I am looking at an example for the sed command which uses the option -n:

$ sed -n -e '/regexp/p' /path/to/my/test/file | more

I read as explanation for the -n opption: Note the new '-n' option, which tells sed to not print the pattern space unless explicitly commanded to do so.

I don't understand this explanation in the right way. What does this -n option exactly do?:( 

Regards

---

### Post by Ramses de Norre on 2006-07-19
Well normally sed prints all output to stddout, so your terminal by default. But this option tells sed not to do this.

---

### Post by pat270881 on 2006-07-19
So when I use -n in the sed command nothing is printed to the stdout. For what reason do I need this -n??

---

### Post by Ramses de Norre on 2006-07-19
You can for example tell sed to print only the lines matching your addressing
So ```
sed -n -e '/^#/p' test.txt
```
will print (the p command) all lines in test.txt starting with an # to stdout, all lines which don't start with an # aren't printed.

---

