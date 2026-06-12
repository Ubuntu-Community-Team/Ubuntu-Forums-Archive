---
title: "bash redirection"
date: 2007-11-23
forum: General Help
---

### Post by go_beep_yourself on 2007-11-23
$ echo 0>$1
bash: $1: ambiguous redirect

What's that?

---

### Post by mali2297 on 2007-11-23
> **go_beep_yourself said:**
> $ echo 0>$1
bash: $1: ambiguous redirect

What's that?

Not what you had expected? Is there something you want to do with that command?

$1 is probably unset.

---

### Post by ChameleonDave on 2008-07-02
I came across this thread because I was searching to the answer to the same problem.  The thing about $1 being "unset" gave me a clue, and I worked it out.  My problem was that I didn't realise that functions don't automatically inherit parameters.  That may be the problem you're having.

The following script demonstrates the behaviour.  Save it as "demo.sh", make it executable, and run it with "./demo.sh HELLO".


[PHP]#!/bin/bash
## Demonstration of positional parameters

#Functions
function reportparams
{
  echo "Within this function, the text you entered is reported as" $1
}

#Main
echo "The text you entered is" $1

echo "I will now try to print that again, first without passing the positional parameter, and then actually passing it."

reportparams

reportparams $1

[/PHP]

---

