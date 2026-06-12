---
title: "Bash &quot;function {  }&quot; call ignored.... ?"
date: 2008-05-05
forum: General Help
---

### Post by OldGaf on 2008-05-05
Any idea why this will work on a Redhat system, but not on my Kubuntu?

It's like it doesn't understand the function { } at all..... It should go right to the case and only use the function when called. Instead it dies right away with: 

> This is the first choice
test: 9: Syntax error: "}" unexpected



#!/bin/bash

function first {

clear

echo "This is the first choice"

}

function second {

clear

echo "This is the second choice"

}

clear

echo "What do you want to do?"
echo
echo "1 Print the first message"
echo "2 Print the second message"
echo "3 Quit"

read pick

case $pick in
        1 ) first;;
	2 ) second;;
        3 ) exit;;

esac

---

### Post by Monicker on 2008-05-05
I think your functions should look like this


```
function () {

 <do something>

}
```

Doesn't seem that you are passing any variables so just "()" is sufficient.

---

### Post by davidpbrown on 2008-05-05
That worked for me in Ubuntu.

One issue I came across recently was running scripts, under cron for example, sometimes forces dash not bash.

I don't know where you're running what, or how Kubuntu differs to suggest more..

---

### Post by rubicon on 2008-05-05
No clue.

Just copypasted it in gedit and ran. Everything works. There could be brackets after function names (e.g. function first () {...), but for me it runs anyway.

What's your bash version?
```
$ /bin/bash --version
GNU bash, version 3.2.33(1)-release (i486-pc-linux-gnu)
Copyright (C) 2007 Free Software Foundation, Inc.
```

---

### Post by OldGaf on 2008-05-05
> **Monicker said:**
> I think your functions should look like this


```
function () {

 <do something>

}
```

Doesn't seem that you are passing any variables so just "()" is sufficient.


Nope.... If I add () I get:

> test: 3: Syntax error: "(" unexpected

---

### Post by Monicker on 2008-05-05
> **OldGaf said:**
> Nope.... If I add () I get:

Hrmm. It worked for me using Ubuntu 7.10.

I copied and posted from your first post, and just added the () to each function.

```

arkaic@purgatory:/tmp$ ./function.sh




What do you want to do?

1 Print the first message
2 Print the second message
3 Quit
1





This is the first choice
arkaic@purgatory:/tmp$

```


```
arkaic@purgatory:/tmp$ bash --version
GNU bash, version 3.2.25(1)-release (i486-pc-linux-gnu)
Copyright (C) 2005 Free Software Foundation, Inc.



```


Maybe it really is something different about kubuntu.

---

### Post by OldGaf on 2008-05-05
> **rubicon said:**
> No clue.

Just copypasted it in gedit and ran. Everything works. There could be brackets after function names (e.g. function first () {...), but for me it runs anyway.

What's your bash version?
```
$ /bin/bash --version
GNU bash, version 3.2.33(1)-release (i486-pc-linux-gnu)
Copyright (C) 2007 Free Software Foundation, Inc.
```


Sigh.... and it works at work... (actually a much larger script, this is just  a test to figure this out)

How did you run it.... sh <filename> ?

---

### Post by davidpbrown on 2008-05-05
./filename
having made it executable obviously..

---

### Post by davidpbrown on 2008-05-05
Trying 
sh ./filename
just gave the error you had initially.

---

### Post by davidpbrown on 2008-05-05
and reading briefly man sh suggests it uses dash.

---

### Post by rubicon on 2008-05-05
What's the point in running it via sh <filename> while you clearly directed this file to be interpreted by /bin/bash?? D'OH!

---

### Post by Monicker on 2008-05-05
> **davidpbrown said:**
> and reading briefly man sh suggests it uses dash.

Yup.


[http://www.ubuntu.com/getubuntu/releasenotes/804]("http://www.ubuntu.com/getubuntu/releasenotes/804")

*/bin/sh is now dash*

---

### Post by OldGaf on 2008-05-05
> **rubicon said:**
> What's the point in running it via sh <filename> while you clearly directed this file to be interpreted by /bin/bash?? D'OH!


D'OH is right!

I can run it if I ./test (at work I can just run test... no sh or ./)

It will only work with #!/bin/bash. If I use dash I get 

> This is the first choice
./test: 9: Syntax error: "}" unexpected

Anyway... my brain fart!!

Thanks all for holding my hand!

Another thing that doesn't work on this notebook is tput rmso, but tput bold and tput smso work fine. I have to use tput reset to get back to normal text, but that clears the screen.... not what I want in the middle of a script.

Having these differences between home and work is most annoying. Any ideas on how to resolve these differences? I am using feisty.

Thanks again to everyone.

---

### Post by OldGaf on 2008-05-05
Found the fix for tput rmso. tput sgr0 resets without clearing the screen. Anyone know the difference between the shells or a good site that explains it? ie why some shells work with tput rmso and others ignore it. Standards are a good thing! We are using ksh at work.

---

### Post by davidpbrown on 2008-05-05
I don't know much of different shells.. maybe look at chsh to change the shell to ksh if that's what you're more used to?

---

### Post by OldGaf on 2008-05-05
> **davidpbrown said:**
> I don't know much of different shells.. maybe look at chsh to change the shell to ksh if that's what you're more used to?


From what I have been reading, it looks like it is better to stay with bash. I can't change what I use at work, so I will have to get used to the differances.

---

