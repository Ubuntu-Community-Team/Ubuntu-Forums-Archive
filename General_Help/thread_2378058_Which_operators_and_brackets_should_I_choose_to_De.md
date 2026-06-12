---
title: "Which operators and brackets should I choose to Decision Maker on Shell"
date: 2017-11-19
forum: General Help
---

### Post by sed_faster on 2017-11-19
Hello folks,

I am freaking out which operators on shell script. I never know which operators should I use when I need chain validation on Shell Decision Maker "IF".
I wrote this code:
```

while (( $divider <= $number ) || ( $amount == 1 ))

```
When this stretch it was run I receive this message on my terminal:
```

./exsh34.sh: line 31: =: No such file or directory
./exsh34.sh: line 31: 0: command not found

```
What this is means?

Thanks

---

### Post by sed_faster on 2017-11-19
Also I am trying do this:
```

elfi [ $divider -le $number ] -a  [ $((number%divider)) = 0 ]
        then
           ....................

```
but I receive this error
```

./exsh34_2.sh: line 38: syntax error near unexpected token `then'
./exsh34_2.sh: line 38: `        then'

```
Thanks

---

### Post by Holger_Gehrke on 2017-11-19
It means that the shell tried to evaluate the contents of the double parentheses as an arithmetic expression, failed, discarded the double parentheses, tried to redirect standard input to the file named '=' and execute the command given as the value of the variable $divider, failed, crashed and burned ...

What you probably wanted to do would read something like
```

while [[ ( $divider -le $number ) || ( $amount -eq 1 ) ]] ; do whatever-you-want; done

```

And while I will admit that it's dense and dry as tinder, I still think the manual page of the bash is quite good.
```

man bash

```

Holger

---

### Post by sed_faster on 2017-11-19
This works. I need learn more about bash and which singnals I should use on shell script. I will read more about this theme.
Thanks

**Off-topic:**
What is the value max I can handle on shell script? If I intend calculate which number primes exist until 10000000000, this is possible? Which is the limit?
thanks

---

### Post by sisco311 on 2017-11-19
Check out: 
[http://mywiki.wooledge.org/BashGuide/TestsAndConditionals](http://mywiki.wooledge.org/BashGuide/TestsAndConditionals)
[http://mywiki.wooledge.org/BashGuide/CompoundCommands](http://mywiki.wooledge.org/BashGuide/CompoundCommands)

It's a common misconception that the "brackets" are part of the syntax of the if/while statements. They aren't!

For example, the syntax of if is:
```

if COMMANDS
then
    OTHER COMMANDS
fi

```

So the "brackets" are commands. **[** is the synonym for the **test** builtin command. **[[** is a more advanced version of **[** or **test**. **(( EXPRESSION ))** is equivalent to **let EXPRESSION**

---

### Post by Holger_Gehrke on 2017-11-19
> **Edgar_Oliveira said:**
> 
**Off-topic:**
What is the value max I can handle on shell script? If I intend calculate which number primes exist until 10000000000, this is possible? Which is the limit?
thanks

The manual doesn't say but warns that bash won't catch errors due to overflowing integer variables. So I ran
```
for (( i=0 ; i - 65 ; i++ )) ; do echo $(( 2**i )); done
```
and the last three line of output read
```
4611686018427387904
-9223372036854775808
0

```so I'd say that looks like signed 64 bit integers on a 64 bit processor. But please don't try to implement the "sieve of Eratosthenes" as a shell script for that kind of number; it would need horrifying amounts of RAM and run slower than molasses.

Holger

---

