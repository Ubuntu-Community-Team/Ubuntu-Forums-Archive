---
title: "Scripting help - mkdir with output from grep"
date: 2014-07-17
forum: General Help
---

### Post by getut2 on 2014-07-17
I know this is super simple, but all the articles I have googled seems geared toward a different scenario.

I have grep output that give me lines of text that I want to use as  subfolder names and create the folders with mkdir. The grep portion is  working and giving me the output I need. It is basically a string that  exists before the first and only comma in each line of a text file.

```
grep -o '^[^,]*' textfile
```

How can I iterate through those lines and build folders.. pseudo code below:

mkdir -p rootfolder/(line1 of grep output)
mkdir -p rootfolder/(line2 of grep output)

etc.

---

### Post by steeldriver on 2014-07-17
I would do something like

```

while read -r dir; do
    mkdir -p "rootfolder/$dir"
done < <(grep -o '^[^,]*' textfile)

```

or just use bash's built in string manipulations to strip off everything after the first comma

```

while read -r dir; do
    mkdir -p "rootfolder/${dir%%,*}"
done < textfile

```

---

### Post by Lars Noodén on 2014-07-17
You could wrap the grep portion in $(...) for command substitution which allows the output to be used as data, say for a loop: 

```

for directory in $(grep -o '^[^,]*' textfile);
do mkdir -p "${directory}";
done

```

Of course that depends on there being nothing mischievous in the input text file.

---

### Post by getut2 on 2014-07-17
Wow.. that second one using built in string manipulation is nice. Can you explain a little about what is going on there. I don't even know what to search on about that to find out more about what you did.

The $ is the parameter, but what is the dir%%? I guess the ,* is the end of the same regex string but not even sure about that.

---

### Post by steeldriver on 2014-07-17
```

${parameter%pattern}

```    

tries to match 'pattern' against the end portion of shell variable named 'parameter'. The result is the expanded value of 'parameter' with the shortest match deleted.

```

${parameter%%pattern}

```

tries to match 'pattern' against the end of 'parameter'. The result  is the expanded value of 'parameter' with the **longest **match deleted (useful for cases like something.other.extension) 

The # and ## sequences do the same thing but matching against the initial portion of 'parameter' - see [http://mywiki.wooledge.org/BashGuide/Parameters#Parameter_Expansion](http://mywiki.wooledge.org/BashGuide/Parameters#Parameter_Expansion)

These are handy tricks especially for filename manipulation (e.g. processing a file with a .jpg extension and saving the result to a filename with a .pdf extension)

---

### Post by sedawk on 2014-07-17
Try
grep -o '^[^,]*' textfile |xargs mkdir

---

### Post by getut2 on 2014-07-22
Oh man.. stuck again.

How can I do the same thing but only with the 2 characters before the comma?

Take the string

12345,ABC

I need to grab the 45 as the input for the mkdir command. I can't believe I'm not understanding this enough to find it myself. I've spent 3 days testing this and can't get it to work with a negative look behind in any way I have tried.

I can get it to work all day as a simple regex that gets EVERYTHING before the first comma, but not just 2 characters.

---

### Post by steeldriver on 2014-07-22
You could do it in grep with a look*ahead* - but that requires PCRE mode

```

grep -Po '..(?=,)'

```

To do it natively in bash, you'd need to take it in two bites I think i.e. remove the trailing portion like before, and then take the last 2 characters of what remains e.g.

```

while read -r dir; do
    tmp="${dir%%,*}"
    mkdir -p "rootfolder/${tmp:(-2)}"
done < textfile

```

---

