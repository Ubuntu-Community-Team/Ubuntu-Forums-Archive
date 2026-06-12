---
title: "Reading file with loops"
date: 2014-10-19
forum: General Help
---

### Post by prohank on 2014-10-19
Hi guys,
I don't understand how loops can be used to process one line from a file at a time.
Used for loop of C language for iterating but obviously that is not working.
I have a file with the following format:
:Header
:Line A
:Line B
:Line A1
:Line B1
...
:Line An
:Line Bn

And, I want it in the form of:
 :Header
:Line A,
:Line B_modified
:Line A1
:Line B1_modified
...
:Line An
:Line Bn_modified
**in a new file.**

The modification on line B is nothing but an address of a file that I wish to check if it exists, if not then remove that line. But that I could do the only problem is with iterating the lines and saving lines to another file.
Any ideas?

---

### Post by steeldriver on 2014-10-19
In bash, you should be able to use something like

```

while read -r line; do
  *something with* "$line"
done < file

```

---

### Post by prohank on 2014-10-19
> **steeldriver said:**
> In bash, you should be able to use something like

```

while read -r line; do
  *something with* "$line"
done < file

```

Yes I have tried this but how do I know which line to edit from the above code? Because the file has atleast 50 lines and it would be troublesome to work on every line.
Let me edit the question to make it more clear.
Well thanks for the reply.

---

### Post by sudodus on 2014-10-19
***for loops*** are also available in bash.

See ```
help for
```

and this (maybe easier to use)

from ***man bash***:

```
       for name [ in word ] ; do list ; done
              The list of words following in is expanded, generating a list of
              items.  The variable name is set to each element of this list in
              turn,  and  list is executed each time.  If the in word is omit&#8208;
              ted, the for command executes  list  once  for  each  positional
              parameter that is set (see PARAMETERS below).  The return status
              is the exit status of the last command that  executes.   If  the
              expansion of the items following in results in an empty list, no
              commands are executed, and the return status is 0.

       for (( expr1 ; expr2 ; expr3 )) ; do list ; done
              First, the arithmetic expression expr1 is evaluated according to
              the  rules  described  below  under  ARITHMETIC EVALUATION.  The
              arithmetic expression expr2 is then evaluated  repeatedly  until
              it  evaluates  to zero.  Each time expr2 evaluates to a non-zero
              value, list is executed and the arithmetic expression  expr3  is
              evaluated.   If  any  expression is omitted, it behaves as if it
              evaluates to 1.  The return value is the exit status of the last
              command in list that is executed, or false if any of the expres&#8208;
              sions is invalid.

ex.
for i in *.txt;do echo textfiler: $i;done

for (( i=1; i<=20 ; i++ )) ; do echo $i;done

for i in *.TXT;do mv $i ${i/\.TXT/}.txt; done  # "move *.TXT *.txt"


```

---

### Post by steeldriver on 2014-10-19
> **prohank said:**
> Yes I have tried this but how do I know which line to edit from the above code? Because the file has atleast 50 lines and it would be troublesome to work on every line.
Let me edit the question to make it more clear.
Well thanks for the reply.

What do you want to do **exactly**? a minimal example would help

---

### Post by prohank on 2014-10-19
Ok lets try again ..
I have a file which has some contents of which some lines need special operation and others are to be simply copy pasted.
The contents of file1.txt  are as follows:

Contents:
text1
/abc/def/ghi.pdf
text2
/abc/gfd.pdf
text3
/abc/deg.pdf
and so on...

Now, I want to copy first 2 lines as it is to file2.txt
then check if ghi.pdf exists or not(i.e. operation on line 3)if exists then copy line3 to file2.txt (otherwise don't) and move on to next line.
Now copy 4th line to file2.txt and again check if gfd.pdf file exists and so on...just notice the pattern that's all.

I am really sorry that I couldn't make it more simpler to understand.
Thank you.

---

### Post by steeldriver on 2014-10-19
Well you could do

```

n=1
while read -r line; do 
  # test odd lines starting from the 3rd
  if ((n>1 && n%2)); then 
    if [[ -e "$line" ]]; then 
      echo "$line"
    fi
  # print 1st and all even lines
  else 
    echo "$line"
  fi
  ((n++))
done < file1.txt > file2.txt

```

---

### Post by prohank on 2014-10-20
Well that was :cool:.
Thanks a lot man.
Cheers!

---

