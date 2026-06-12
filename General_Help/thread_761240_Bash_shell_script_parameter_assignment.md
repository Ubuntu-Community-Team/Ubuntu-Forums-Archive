---
title: "Bash shell script parameter assignment"
date: 2008-04-21
forum: General Help
---

### Post by dizwell on 2008-04-21
My shell script accepts two run-time arguments. I want to be able to force the value of one of those arguments to be something of my choosing if it is some specific value or other.

For example, if the first supplied argument is the word "red", I want to be override the value to make it "green" and have the rest of my script behave accordingly.

I could do it by assigning variables, I realise, but I would like to know if it is possible, conceptually at least, to do something like

if [[ $1 = "red" ]]
then
  $1 = "green"
fi

Unfortunately, that code snippet fails to assign the value properly and the rest of the script bombs out accordingly. I've tried things like "let $1 = "green", too, but to no avail.

Any insights on how to conditionally force a user-supplied argument to be a particular value directly would be gratefully received!

---

### Post by bingoUV on 2008-04-21
In general, when you assign values to variables, you skip the leading $. i.e. 
```

varName="varValue";
echo $varName

```I am not sure if this will work if variable name is a number like $1. You could assign a different variable which  will then be used in your script
```

if [[ $1 = "red" ]]
then
  color="green"
else
color="$1"
fi
echo $color

```

---

### Post by dizwell on 2008-04-21
Thanks, but that's the 'I could use variables' route I don't particularly want to take.

I want to make the $1 "placeholder" (I'm not sure of the precise term to use at that point) acquire a value *directly*, not use its value to determine the value of some intermediate variable.

In your code, for example, I get to affect that value of the $color variable... but the rest of my script has no knowledge of that variable, and is only aware of the existence of $1 (i.e., the first argument supplied by the user when invoking the script in the first place). I would prefer not to have to edit the 900+ lines of this script which knows all about $1 already but nothing about some newly-invented $color variable.

I'm not sure if I've explained that clearly enough or not. It comes down to my earlier code example: I want to force $1 to have a particular value, regardless of what the user actually typed in. I don't want to use the value of $1 to determine the value of something else.

---

### Post by trwrt on 2008-04-21
Just have the script call itself with the parameter substituted and exit afterwards, otherwise it falls through.

#!/bin/bash
if [[ $1 == "red" ]]; then
  ./$0 green $2
  exit
fi
echo $1 $2

The $0 parameter is set to the name of the script file.

---

### Post by bingoUV on 2008-04-21
trwrt is right. It has the risk of infinite loop in case of coding mistake, but maybe acceptable. Another method is to push existing code in a function. Precede with 
```

doWork()
{

```Put the following at the end of your script 
```

}

```Indent the existing code a bit to the right if you like indentation. Now
, when you call doWork, it will take $1, $2 etc as the ordered arguments
```

doWork "first" "second" 

```

$1 in doWork will be "first" , $2 will be "second"

---

### Post by -Zeus- on 2008-04-21
I don't understand why you don't just do this?

```
color=$1
[ "$color" = "red" ] && color='green'
```

---

### Post by bingoUV on 2008-04-21
What does this accomplish? How does this eliminate the need to edit the hundreds of lines of code that is already written using $1, $2 ?

---

### Post by -Zeus- on 2008-04-21
hundreds of lines won't take you that long.  Shouldn't you have probably tested the code as you wrote it and saw that it doesn't work?

Besides, you can just do a find-and-replace and replace $1 with $arg_1, $2 with $arg_2, etc

---

### Post by bingoUV on 2008-04-21
Customer is king. Customer says no edit earlier code, that means no edit earlier code. Once the customer has said that already written code is not to be modified, it is against the rules of the game to suggest such solutions. 

For you and me, it could be just a little intellectual exercise. For the customer, it might be religious reasons / superstitious reasons / curiousity for laying these conditions.

---

### Post by dizwell on 2008-04-21
Thank you all for your comemnts. To Zeus, who said, "Shouldn't I have tested this code as I wrote it?", the answer (obvious I would have thought) is "Yes, of course... which is precisely what I DID do and it works just fine, thanks all the same".

However, it's over 900 lines in length. And it's precisly because all that code works, works well and has been tested to death that I'd rather not re-write it (or even change it) just because a new business requirement has come along that can be accomodated quite adequately via other means.

bingoUV was 100% right. When a requirement has been stated, the general support aim would be to help the person achieve that requirement, unless it's totally insane, not arbitrarily re-write the requirement to suit your own agenda as though it simply didn't exist!

Thanks especially, anyway, to trwrt for providing the solution to my actual requirement I have now implemented. It works just fine. For the record, it actually reads:

[FONT="Courier New"]if [[ $1 = "ubuntu8" ]]
then
  $0 ubuntu7 $2
  exit
fi[/FONT]

...which does the trick nicely: it installs a piece of software onto Ubuntu 8.04 just exactly as it did on Ubuntu 7.10, but the user doesn't have to pretend they're using a distro version that they're not to make it happen. And I don't have to re-write the Ubuntu 7 code that's worked fine for the past six months, either.

---

