---
title: "Bash programming: RANDOM does not work?"
date: 2007-05-13
forum: General Help
---

### Post by wgw on 2007-05-13
This bit of code is supposed to produce a series of random numbers.... it doesn't (for me!). A tip on what I am doing wrong? (Is my bash broke?) Thanks!

```

#!/bin/bash
count=0;     # initialize x to 0
RANDOM=$$$(date +%s)

echo $RANDOM
while [ "$count" -le 10 ]; do
    number=$RANDOM
    echo "Current value of count: $count: $number"
    # increment the value of count:
    count=$(expr $count + 1)
    sleep 1
done

```

---

### Post by 454redhawk on 2007-05-13
Try this to see if it works on your computer.

```
#!/bin/bash
# This is a bash script to create a fourteen character string of random numeric digits.
echo -n "The random number is "
for ((i=1; i<15; i++)) ; do
echo -n $(( $RANDOM / 3276 ))
done
echo

```

---

### Post by wgw on 2007-05-13
> **454redhawk said:**
> Try this to see if it works on your computer.

```
#!/bin/bash
# This is a bash script to create a fourteen character string of random numeric digits.
echo -n "The random number is "
for ((i=1; i<15; i++)) ; do
echo -n $(( $RANDOM / 3276 ))
done
echo

```


I get an error with your code: The random number is random_rename.bsh: 9: Syntax error: Bad for loop variable

Can't seem to get your for loop working, but that is not really the problem. When I put echo -n $(( $RANDOM / 3276 )) in my loop, I get the same unfortunate non-random results. Curious!

I got -301431-301431-301431-301431-301431-301431-301431-301431-301431-301431-301431

here is my loop with your echo:

```
#!/bin/bash
count=0;     # initialize count to 0
RANDOM=$$$(date +%s)
echo $RANDOM
while [ "$count" -le 10 ]; do #start of loop
    echo -n $(( $RANDOM / 3276 ))
    #echo "Current value of count: $count: $number"
    # increment the value of count:
    count=$(expr $count + 1)
    sleep 1
done
```

---

### Post by 454redhawk on 2007-05-13
From the man page.


Its worth a try

```
CONFIGURING
       If your system does not have /dev/random and /dev/urandom created already, they can  be  cre-
       ated with the following commands:

               mknod -m 644 /dev/random c 1 8
               mknod -m 644 /dev/urandom c 1 9
               chown root:root /dev/random /dev/urandom

```

---

### Post by bashologist on 2007-05-13
The problem is because you redefine the name "RANDOM". Also instead of the deprecated "$(expr $count + 1)" you should use "((count++))".

```
# Maybe you want something like this?
for ((i=1;i<11;i++)); do
    printf "\rcurrent value of count: $i: $RANDOM"
    sleep 0.2
done; echo

# Here's an example of to how increment a variable:
count=1; for i in {1..10}; do
    printf "\r$count"
    ((count++))
    sleep 0.2
done; echo

# Or increment in a printf command:
count=1; for i in {1..10}; do
    printf "\r$((count++))"
    sleep 0.2
done; echo
```

---

### Post by wgw on 2007-05-14
Well, here is my (noobie) problem: I was issuing the command as: sh test.bsh. 

Why? God only knows (actually I think it would be a mystery to Him as well...) I think it is because I tried the file name at the command line and it didn't work; then I tried sh filename and it did, sort of. So I continued with sh....

However, ./filename works. 

Sorry to have troubled you. Your loop works fine as well. :redface:


(In the future, I will include my command line as well -- would have resolved the question right away. )

---

### Post by hartz on 2007-05-14
I just tested this and I get the same result.

If I make the first line of the script read

```
#!/bin/sh
```

then it acts differently to having

```
#!/bin/bash
```

Note that ./scriptname causes the script to execute by means of the interpreter indicated on the first line.  The command "sh scriptname" causes the script to be executed by "sh" as interpreted, irrespective of what is specified as interpreter in the first line of the script.

In this light, you can also test this syntax:

```
bash scriptname
```

This is interesting in the light of /bin/sh -> /bin/bash... These two files are basically for all practical purposes one-and-the-same.  /bin/sh points to /bin/bash.

Strange, but probably defined and documented behavior somewhere in the annals.  (There are many instances of Unix/Linux commands behaving differently depending on which "name" you used to call them)

---

### Post by mcduck on 2007-05-14
> **hartz3 said:**
> 
This is interesting in the light of /bin/sh -> /bin/bash... These two files are basically for all practical purposes one-and-the-same.  /bin/sh points to /bin/bash.

Strange, but probably defined and documented behavior somewhere in the annals.  (There are many instances of Unix/Linux commands behaving differently depending on which "name" you used to call them)
Since Edgy, /bin/sh points to Dash, not Bash ;)

---

### Post by hartz on 2007-05-14
It doesn't in my fresh install of xubuntu 7.04, not in my upgraded over-and-over-since 6.04 Ubuntu.

I seem to recall seeing a note about this previously though...

---

### Post by mcduck on 2007-05-15
> **hartz3 said:**
> It doesn't in my fresh install of xubuntu 7.04, not in my upgraded over-and-over-since 6.04 Ubuntu.

I seem to recall seeing a note about this previously though...

Well, it *should* point to dash ;)

```
$ ls -la /bin | grep sh
-rwxr-xr-x  1 root root  700560 2007-04-11 01:32 bash
-rwxr-xr-x  1 root root   80500 2007-03-05 07:00 dash
lrwxrwxrwx  1 root root       4 2007-04-21 17:31 rbash -> bash
lrwxrwxrwx  1 root root       4 2006-11-12 18:05 sh -> dash
lrwxrwxrwx  1 root root       4 2007-04-21 17:31 sh.distrib -> bash
```

---

