---
title: "[SOLVED] Multiply two numbers from the command line"
date: 2007-12-30
forum: General Help
---

### Post by dje on 2007-12-30
Hi
How can i multiply two numbers from the command line eg. 
```
23 * 5
115
```
**I NEED IT TO BE EXECUTABLE FROM A SHELL SCRIPT WITH ONE OR TWO VARIABLES**

Thanks in advance

**SOLVED:**
```
echo "2*2" | bc
4
```
This will use decimals if necessary

You can also do:
```
echo $((2*2))
4
```
This will always produce a whole number

---

### Post by icheyne on 2007-12-30
python

---

### Post by dr.silly on 2007-12-30
# python
>>> 23 * 5
115
>>>

---

### Post by dje on 2007-12-30
Yes i thought i could do that but this is to put in a shell script, could i execute that with a variable from the shell script?

---

### Post by dagnabit dang doohickey on 2007-12-30
For quick calculations, I added the following function to my ~/.bash_aliases file. (Alternatively, it can be added to your ~/.bashrc file instead.)
```
function calc () { echo "$*" | bc ; }
```
Then call it as:
```
calc 23*5
```
or for more complicated calculations requiring parenthesis, use quotes:
```
calc '((5*5)-2)*5'
```

---

### Post by dje on 2007-12-30
Thanks but i just get this output
```
The program 'calc' is currently not installed.  You can install it by typing:
sudo apt-get install apcalc
Make sure you have the 'universe' component enabled
bash: calc: command not found
```
:(

---

### Post by dje on 2007-12-30
I got it to work, i just needed to restart my shell :oops:
Thanks its really great

---

### Post by dagnabit dang doohickey on 2007-12-30
Another option for quick calculations, but not on the command line: if you have Firefox open, enter the calculation in the Google search bar. The first suggestion will be the result.

---

### Post by dje on 2007-12-30
I modified dagnabit dang doohickey's command so the bashrc or bash_aliases file didn't need to be edited and so better for my shell script:
```
echo "2*2" | bc
4
```
This will use decimals if necessary

You can also do:
```
echo $((2*2))
4
```
This will always produce a whole number

Hope that helps anyone who wants to do basic calculations from the command line

---

