---
title: "Shell"
date: 2007-08-22
forum: General Help
---

### Post by The Wisedude on 2007-08-22
I got two questions In a shell script this is what it looks

[PHP]#!/bin/sh
sleep 3s
xvkbd -text "STRINGHERE"
[/PHP]

Now here are the 2 qs.

If i wanted it to repeat untill I end the process what is the command for that? What do I make it look like?


Second Question.

What is the command for the 'Return' key or commonly known as the enter key?

---

### Post by The Wisedude on 2007-08-22
BUMP need help!

---

### Post by The Wisedude on 2007-08-22
Bump

---

### Post by The Wisedude on 2007-08-22
Bump

---

### Post by praet on 2007-09-14
Hey The Wisedude, 
Welcome to the world of bash scripting.

First question:

You could write a script to repeat the action a number of times, with a delay in between, or indefinitely. 
Save this as a file repeatenter.sh and mark it as executable (chmod +x repeatenter.sh):
```

#!/bin/sh
while true ; do	

        # send the enter key
        xvkbd -text "\r"

        # print some text to the console
	echo "*** Press Ctrl+C to quit." 

        # pause for 6 seconds
	sleep 6  

        # endlessly repeat
done

```

Second question:
see: 
[http://ubuntuforums.org/showthread.php?t=527974](http://ubuntuforums.org/showthread.php?t=527974)

So to send the enter key you could use xvkbd and this string "\r" :
```
xvkbd -text "\r"
```

I added the code to send enter in the script above already as an example.
Good luck.

---

