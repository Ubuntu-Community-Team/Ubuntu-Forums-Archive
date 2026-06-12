---
title: "Bash script to check user input?"
date: 2008-05-20
forum: General Help
---

### Post by ffasolt on 2008-05-20
I am trying to write a shell script which accepts user input and then checks whether it's a certain length or if it starts with a number. I have Googled till the cows come home, but I haven't found anything approaching descriptions on how to do either. So far, I've got this:

[FONT="Courier New"]#/bin/bash
echo "Please type something"
read MYVAR
`startchar=${MYVAR:0:1}`

echo "First character was:" $startchar

if [ `expr length "$MYVAR"` > 8 ]; then
  echo "Too long!"
fi

if [ `expr length "$MYVAR"` = 0 ]; then
  echo "No input, so defaults will apply"
fi[/FONT]

Unfortunately, none of that works, and I can't pin down why: when it's run and I enter anything or nothing at all, it puts up both the 'too long' *and* the 'no input' errors *and* fails to identify the first character!

Besides, I don't just want to display the first character, I want to test whether it's a number, and I haven't the first clue how to do that. And on top of all that, I also want the whole thing wrapped in a loop that says, until you've typed something, and it's less than 8 characters, and it doesn't start with a number, please keep on trying.

Can anyone please point out what I'm doing wrong and give me some pointers so I don't do it again?!

---

### Post by sdennie on 2008-05-20
Something like this might get you moving in the right direction:

```

#!/bin/bash

echo "Type something"
read A

LENGTH=`echo -n $A | wc -m | sed -e s/^\s+//`
echo $LENGTH

FIRST_IS_NUMBER=`echo $A | sed -e s/^[0-9]//`

if [ "$A" != "$FIRST_IS_NUMBER" ]; then
    echo "First character is a number"
else
    echo "First character is not a number"
fi

```

---

### Post by ffasolt on 2008-05-20
That is wonderful. Thankyou. Works entirely as advertised.

Now I can do my checks... I'm probably pushing my luck, but any clues as to how to loop round this until the user gets the input correct? I only know how to throw an echo 'you got it wrong' and 'exit' statement in there at the moment!

---

### Post by sdennie on 2008-05-20
Just a quick hack but:

```

#!/bin/bash

OK=0

while [ "$OK" != 1 ] ; do
    echo "Type something"
    read A
    
    LENGTH=`echo -n $A | wc -m | sed -e s/^\s+//`
    echo $LENGTH
    
    FIRST_IS_NUMBER=`echo $A | sed -e s/^[0-9]//`
    
    if [ "$A" != "$FIRST_IS_NUMBER" ]; then
        echo "First character is a number"
        OK=1
    else
        echo "First character is not a number"
    fi
done

```

---

### Post by ffasolt on 2008-05-20
Genius, sir. Thank you. I do know while...do loops. Why on Earth I didn't think to use them in this case, I can't image. Sometimes, it needs a fresh pair of eyes, I guess.

Much obliged to you: everything is now working as needed. I am very grateful.

---

