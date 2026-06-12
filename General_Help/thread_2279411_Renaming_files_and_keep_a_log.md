---
title: "Renaming files and keep a log"
date: 2015-05-23
forum: General Help
---

### Post by chuckie86 on 2015-05-23
[SIZE=3][FONT=arial narrow]I'm trying to keep a log of files i'm renaming, so i can look which file was the original one.

i'm using a bash command to rename [/FONT][/SIZE][COLOR=#000000][FONT=verdana][SIZE=3][FONT=arial narrow]for f in *.jpg; do mv $f $RANDOM.jpg; done

But now i want to log it, so i know that picturea is renamed to the random file now, how can i do that? 


[/FONT][/SIZE]
[/FONT][/COLOR]

---

### Post by TheFu on 2015-05-23
echo the mv command before doing it and use "tee" to create a log file.
```
 for f in *.jpg; do 
    echo mv $f $RANDOM.jpg; 
    mv $f $RANDOM.jpg; 
done
```

./script.sh |tee log.script

---

### Post by chuckie86 on 2015-05-27
Ok, thx for the help, thix worked! 

You maybe know how to take the first 2 letter from each word and use in the new word?

For example: having the best day.jpeg => hathbeda.jpeg

Is that possible?

---

### Post by TheFu on 2015-05-27
Of course it is possible.
You can write that script yourself using any language you know or can pick up enough to make it work.  I'd use perl, myself, but if you are just starting, python can do it just as easily. String handling is core to perl, python, ruby.

---

### Post by Lars Noodén on 2015-05-27
+1 for perl

If you use the 'rename' utility instead, it is already using perl so you can just add in the appropriate perl regular expressions (pcre).  

```

for f in *.jpeg; do 
    rename -n 's/\.([^\.]*)$//; $b = $1; s/\b(\w\w)\w*\b\s*/$1/g; s/$/.$b/;' "$f"
done >> /tmp/rename.log

```

There might be a way to shorten that, but here is how the above breaks down:

```

s/\.([^\.]*)$//;   # remove the filename extension (everything after the last dot) and save it in the temp variable $1
$b = $1;           # save temp variable $1 as $b
s/\b(\w\w)\w*\b\s*/$1/g;    # find and remove all but the first two characters of every 'word', anchored by word breaks \b 
s/$/.$b/;           # replace the filename extension to the end of the name

```

---

### Post by chuckie86 on 2015-05-28
> **TheFu said:**
> echo the mv command before doing it and use "tee" to create a log file.
```
 for f in *.jpg; do 
    echo mv $f $RANDOM.jpg; 
    mv $f $RANDOM.jpg; 
done
```

./script.sh |tee log.script


If i'm using this, it will rename the file to 4528.jpeg, but in the log it will say 8997.jpeg.. 

I need the log to say 4528.jpeg :)

---

### Post by Lars Noodén on 2015-05-28
> **chuckie86 said:**
> If i'm using this, it will rename the file to 4528.jpeg, but in the log it will say 8997.jpeg.. 

I need the log to say 4528.jpeg :)

It needs an intermediate variable, because $RANDOM will return a different random number each time it is called.  

```

 for f in *.jpg; do 
    r=$RANDOM;
    echo mv $f $r.jpg; 
    mv $f $r.jpg; 
done

```

---

