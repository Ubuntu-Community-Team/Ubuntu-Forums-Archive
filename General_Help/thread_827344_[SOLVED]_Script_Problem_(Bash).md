---
title: "[SOLVED] Script Problem (Bash)"
date: 2008-06-12
forum: General Help
---

### Post by jeroensd on 2008-06-12
Hi everyone!

I must write a script that does the following:

[LIST]
[*]Display the name of the script being executed.
[*]Display the first, third and tenth argument given to the script.
[*]Display the total numbers of arguments passed to the script.
[*]If there were more than three positional parameters, use shift to move all the values 3 places to the left.
[*]Print all the values of the remaining arguments.
[*]Print the number of arguments.
[/LIST]

So, i'm stuck at the first point. How do I display the filename? I tried $filename and $tty but those didn't work. I searched on the internet but could not find anything.

How can I give arguments to a script? And can someone tell me what arguments are exactly? And how can I move them 3 places to the left?

Greetings,
Jeroen

p.s. I'm getting better with Bash! Learning everyday more stuff. I never worked with Linux so I have big trouble with the syntaxes and stuff but it's much more stable and faster then Windows so maybe Ubuntu will be my favorite OS soon. Also thanks for all the help I get here...I'm really learning a lot from it. Thanks!

---

### Post by h0me5k1n on 2008-06-12
try "echo $0" in the script to get the filename
$1 is the first argument, $2 the second and so on.... 

Some useful links
[http://www.ibm.com/developerworks/library/l-bash2.html]("http://www.ibm.com/developerworks/library/l-bash2.html")
[http://tldp.org/LDP/abs/html/]("http://tldp.org/LDP/abs/html/")

---

### Post by ibuclaw on 2008-06-12
In BASH, the filename/arguments/number of arguments are stored as numbers and special characters.

You use the String symbol ($) and a number (123) to show the filename and arguments.

Filename = $0
Argument 1 = $1
Argument 2 = $2
Argument 5 = $5
Argument 10 = $10

You use the Hash symbol (#) to show the number of arguments.

No. of arguments = $#

Shift by default moves 1 parm, but specify a number with it and it shifts that many arguments.

Shift 1 argument = shift
Shift 2 arguments = shift 2
Shift 5 arguments = shift 5

To show all the arguments/print the remaining, use the @ symbol

Show all arguments = $@

Hope that helps.

But I can write up a quick demo script if you're still struggling.

Regards
Iain

---

### Post by ibuclaw on 2008-06-12
Here you go, take it and learn from it.
[PHP]
#!/bin/bash

# Display name of script.
printf "%-10s" "Name: "
echo "$0"

# Display 1st, 3rd and 10th arg if present.
printf "%-10s" "Arg 1: "
[ "$1" ] && echo "$1" || echo "NONE"

printf "%-10s" "Arg 3: "
[ "$3" ] && echo "$3" || echo "NONE"

printf "%-10s" "Arg 10: "
[ "$#" -ge 10 ] && echo "$@" | awk '{print $10}' || echo "NONE"

# Display total number of args.
printf "%-10s" "No. Args: "
echo "$#"

# If there are more than three, shift them.
[ "$#" -ge 3 ] && shift 3

# Print remaining args.
printf "%-10s" "All Args: "
[ "$#" -gt 0 ] && echo "$@" || echo "NONE"

# And the number of args again.
printf "%-10s" "No. Args: "
echo "$#"
[/PHP]
Also, notice that I've used a very Perlish method to compose the script.

To break it down for you:
> 
Check if statement is true and run true command ("&&"), else run false command ("||")
ie:
[ CHECK ] && TRUE || FALSE

An easy example would be:
[PHP][ 4 -eq 5 ] && echo YES || echo NO[/PHP]
If 4 is equal to 5, then echo YES, else echo NO.
Obviously, the above line will always return FALSE, so "echo NO" will always be executed.
Whereas:
[PHP][ 4 -le 5 ] && echo YES || echo NO[/PHP]
Will return TRUE and "echo YES" will be executed. Because 4 is Less than or Equal to 5.

We can also use the NOT character ("!") which does the exactly reverse of the command.
[PHP][ ! 4 -eq 5 ] && echo YES || echo NO[/PHP]
The statement now returns as TRUE, because 4 is not equal to 5.

And lastly, we can also use this to check whether or not a String Exists.
[PHP][ $hello ] && echo YES || echo NO[/PHP]
If $hello exists, then "echo YES", else "echo NO".
Usually, this would return FALSE, as the variable does not exist/have a string size greater than 0.
Whereas:
[PHP]export hello="hello"
[ $hello ] && echo YES || echo NO[/PHP]
Will now return TRUE.


Also notice the use of "printf", it is your friend! And exceedingly helpful when you need special instances of printing text. (In this script, it parses out the input so all appears to be in separate fields).

This is by no means the "standard" way of writing BASH scripts.
But it does means that if this is homework, your teacher won't believe that you wrote it :)

Good luck on your learning quest!

Regards
Iain

---

### Post by jeroensd on 2008-06-13
Hi! Thank you so much for your help! Displaying arguments isn't as hard as it seems!

But I have a question. What does this code:

```

[ "$#" -ge 10 ] && echo "$@" | awk '{print $10}' || echo "NONE"

```

and this:

```

[ "$#" -gt 0 ] && echo "$@" || echo "NONE"

```

Obviously the first one checks if the 10th argument is available. 
This [ "$#" - ge 10 ] checks if the total number of arguments is greater or equal to 10. If that is TRUE, then $@ will be printed, and awk searches for $10 in the printed results of $@.....

Is that correct? And why does echo "$10" not work? And what does $@ print exactly?

Thanks for the help! I really learned a lot from this one!

Thanks!

---

