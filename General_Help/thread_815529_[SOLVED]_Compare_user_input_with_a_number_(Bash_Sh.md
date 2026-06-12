---
title: "[SOLVED] Compare user input with a number (Bash Shell)"
date: 2008-06-01
forum: General Help
---

### Post by jeroensd on 2008-06-01
Hello,

For I school project we do a Open Source minor. We need to learn how Ubuntu works and how we can write simple scripts with the Bash shell. I need to program 5 simple scripts but I'm already stuck with the 1st one.

The first script ask the user for his age. After the user entered his age the program should say whether he's allowed to drink alcohol or not.

So this is what I have so far:

```

clear
#!/bin/bash

echo "This program checks if you're allowed to drink alcohol. Please enter your age:"

read age

echo
echo "Your age is " $age "."
echo

if [$age >= 18]
then
echo "You're allowed to drink alcohol."
else
echo "You're not allowed to drink alcohol."
fi

```

But I get a error (command not found) at the "if" line.

What i'm doing wrong? How can I compare user input to a number?

Greetings,
Jeroen

---

### Post by rampageoberon on 2008-06-01
Hi, replace the line with the condition to

```
if [$age -ge 18]
```

Hope that helps

---

### Post by LaRoza on 2008-06-01
> **jeroensd said:**
> 
```

if [ $age -ge 18 ]

```

But I get a error (command not found) at the "if" line.

What i'm doing wrong? How can I compare user input to a number?


Remember, [ ] are not just fancy characters, they have to have spaces around them.

---

### Post by bollix47 on 2008-06-01
if [ $age -ge 18 ]

or 

if [ $age > 17 ]

The spaces after [ and before ] are important. ;)

---

### Post by jeroensd on 2008-06-01
> **bollix47 said:**
> if [ $age -ge 18 ]

or 

if [ $age > 17 ]

The spaces after [ and before ] are important. ;)


Ah right! It's working now! I tried everything but I forgot to put spaces around the [ and ]. But I was close :D

One more question, I bought this Bash book and it said that I should have a .bash_profile, .bash_logout and .bashrc files in my home folder but I can't see those in my home folder.

Did I deleted something or are these maps not vissible?

---

### Post by rampageoberon on 2008-06-01
those files are not normally visible from the file browser. If you do the following you will see themin your home dir.

```
ls -la | grep "bash"
```

---

### Post by bollix47 on 2008-06-01
Files that start with a period are hidden.

If using a terminal try:

ls -a

If using nautilus file manager try ctrl-h.

---

### Post by jeroensd on 2008-06-02
One more question. How can I use calculations in strings?

```

test=($age - 16) * 100
echo "The result of the test is $test"

echo "The result of the test is ($age - 16) * 100"

```

both options don't work. So how can put the result of a calculation in a variable and how can I calculate directly into a string?

Thanks for the help!

Greetings,
Jeroen

---

### Post by mali2297 on 2008-06-02
> **jeroensd said:**
> One more question. How can I use calculations in strings?

```

test=($age - 16) * 100
echo "The result of the test is $test"


Put calculations inside "$(( ))", like this:
[CODE]
test=$(( (age - 16) * 100 ))
echo "The result of the test is $test"

```

Also, check out [LinuxCommand.org](LinuxCommand.org), in particular:
[http://linuxcommand.org/wss0110.php#arithmetic](http://linuxcommand.org/wss0110.php#arithmetic)

---

### Post by jeroensd on 2008-06-02
> **mali2297 said:**
> Put calculations inside "$(( ))", like this:
```

test=$(( (age - 16) * 100 ))
echo "The result of the test is $test"

```

Also, check out [LinuxCommand.org](LinuxCommand.org), in particular:
[http://linuxcommand.org/wss0110.php#arithmetic](http://linuxcommand.org/wss0110.php#arithmetic)

Thanks! That worked! But is it also possible to calculate this directly in a string?

---

### Post by jeroensd on 2008-06-03
Hi everyone!

For my next script I need to write a program to make a backup of the /etc directory. Does anyone know good tutorial sites where I can see how to create such script?

---

