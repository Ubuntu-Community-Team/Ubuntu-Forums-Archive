---
title: "What's faster, file globbing or a loop?"
date: 2008-07-05
forum: General Help
---

### Post by Meson on 2008-07-05
If I have a set of files, say file1, file2, file3, ..., file9

Which would be faster?
```

for i in `seq 0 99`; do
    cat file$i
done

```
or
```

cat file[0-9][0-9]

```
or even
```

cat file*
cat file??

```

Obviously the filename expansion is neater syntactically, but is the loop faster?  In general how does the expansion work... is it an internal loop of some sort?

---

### Post by scragar on 2008-07-05
I'm leaning towards the first one, since the way searches like the later 2 work as far as I can imagine would be something similar to

```
for i in `ls`; do
  if [ i =~ file[0-9][0-9] ]; then
    cat i
  fi
done
```

---

### Post by Vivaldi Gloria on 2008-07-05
I expect that 

```
1 slower than 2 = 3
```

Why don't you make a little experiment and report back your results. See

```
man time
```

Create a lot of files then use

```
time cat *
```

etc.

---

### Post by Meson on 2008-07-05
Yeah, that's what I was thinking.  It would either be some sort of loop or a series of tests.

I guess it depends on the situation.  For example if the only files in a directory were file20 and file30 then using globbing would probably be more efficient than writing my own loop to search for file00 to file99

---

### Post by lswb on 2008-07-05
When you use cat file?? then you are only starting a process 1 time and passing it lots of arguments. The looping over the different file names will be done internal to the single running process. 

When you use the for... loop, you are starting (and ending) a new process for each file. Probably the difference would be inconsequential for a modern system and a reasonable number of files, but my bet would be that the for... loop would take longer.

---

