---
title: "How to read the first 3 lines of text into separate vars from a variable in shell?"
date: 2013-11-19
forum: General Help
---

### Post by sarah-kho on 2013-11-19
Hi,

I am receiving a text variable inside my shell script from the user. The variable is stored into $1. Now I want to read the first 3 lines of this variable and place them into 3 separate variables named v1, v2 and v3. Any hint on how can I do this?

Thanks.

---

### Post by Lars Noodén on 2013-11-19
You could pipe [head](http://manpages.ubuntu.com/manpages/saucy/en/man1/head.1.html) into [tail](http://manpages.ubuntu.com/manpages/saucy/en/man1/tail.1.html) or use the variable NR in [awk](www.grymoire.com/Unix/Awk.html).  Maybe there are better ways, too.

What are you trying to do?

---

### Post by sarah-kho on 2013-11-19
Thanks for the reply. After getting each line I will need to check for presence of specific words in each of those lines and that helps me decide whether the script should exit 1 or it should exit 0.

---

### Post by Lars Noodén on 2013-11-19
I think you can save a few steps by using awk.  What kind of task is this for, school or work?

---

### Post by sarah-kho on 2013-11-19
It is for work.

I thought head and tail only operate on files; in my case the input is text that is being passed to my script so I cannot do it with tail or head unless I save the text into a file and then perform tail and head on the file.

---

### Post by Lars Noodén on 2013-11-19
Can you show a sample of the 3 lines and point out the text to look for and what factors are in the decision?  

head, tail and the others work on streams of text.  Whether that stream comes from a file or from stdin does not matter so much.  
 
```

for i in {1..4};do echo $i;done | head -n 3 | tail -n 1

```

But awk is probably the way to do it all in one go.

---

### Post by steeldriver on 2013-11-19
If you're not hung up on using 3 separate variables v1, v2, v3 you could use a bash [I]associative array
[/I]
```

for i in {1..3}; do IFS=$'\n' read line; v[i]="$line"; done < myfile

```

and then access them as v[1], v[2], v[3] e.g.

```

echo "${v[1]}"

```

---

### Post by sisco311 on 2013-11-19
If you are going to use an array, then you can do something like:
```
unset array
array=( $1 )

```

Or in Bash >= 4 you can use mapfile (readarray) and a here string:
```
mapfile -c 3 array <<< "$1"
printf '%s\n' "${array[0]}" "${array[1]}" "${array[2]}"
```

---

