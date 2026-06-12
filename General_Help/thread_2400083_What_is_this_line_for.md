---
title: "What is this line for?"
date: 2018-09-02
forum: General Help
---

### Post by webmiester on 2018-09-02
Hi everyone,

i was looking up how to disable the screen saver through command line or bash script...

I found someone posted this:

#!/bin/bash
sleep 10 &&
xset s 0 0
xset s off
exit 0

My question:  "What is the 'exit 0' for?"
is it really necessary?  Wont the program exit anyway once the script ends?

Thanks so much.

---

### Post by Holger_Gehrke on 2018-09-02
Yes, the script will exit after the last command. But the exit status of the script would be the status returned by the last executed command. So by ending with "exit 0" you're reporting successful completion, even if the last command before exit were to produce an error.

Holger

---

### Post by #&amp;thj^% on 2018-09-02
You can read here: [http://www.tldp.org/LDP/abs/html/exitcodes.html](http://www.tldp.org/LDP/abs/html/exitcodes.html)
```

Exit code 0        Success
Exit code 1        General errors, Miscellaneous errors, such as "divide by zero" and other impermissible operations
Exit code 2        Misuse of shell builtins (according to Bash documentation)        Example: empty_function() {}
```

---

### Post by webmiester on 2018-09-02
Hi Holger,

Thank you so much.  I think I understand it...

So if let's say a command or program I launched were to hang.  If I put exit 0, the bash script would still exit and close, wheras if I dont put exit 0, then the bach script would remain open because of that hanged program.  Did I get it right?

Also, does it have to be "exit 0", can it just be "exit", or maybe "exit 1" or "exit 2"

Thanks

---

### Post by Holger_Gehrke on 2018-09-02
No. Every program returns an exit value. A value of 0 means the program ran without encountering any problem, any other value means that there was a problem. The shell can tell you the last returned value if you enter 'echo $?'. Example: grep searches a text file for some specific text (actually for a regular expression, which is like shell-wildcards on steroids ...); if the sought for text can not be found in the file, grep returns a value of 1. The return value is used by all the conditional constructs in the shell (and by most of the loops). Example:
```

if grep 'Truth' myfile.txt >/dev/null 2>&1 ; then
  echo 'The Truth is in there, somewhere'
else
  echo 'nope'
fi

```
The '[' you usually see in if-constructs in scripts is actually a command which can execute various tests and returns 0 if they succeed.

If a program called in a script 'hangs', the script hangs right along with it.

Holger

---

### Post by webmiester on 2018-09-03
Ah ok.  So this exit 0 thing is more for logging.  It means I can also use it to see if a particular script was successfully executed.  What happens if I have additional lines of codes under "exit 0"?  Will these lines still be executed, or will the script exit without executing these lines?

Thanks

---

### Post by webmiester on 2018-09-03
Ok,  btw, what file will exit 0 log its "successful" entry?

---

### Post by Holger_Gehrke on 2018-09-03
It's not logged. It's returned to the calling process. If you call it from a shell, you will get that value in $?. If you call it from Python with 'a=os.system("name-of-script-here")' it will be stored in the variable a. The meaning of the returned value - except for 0 meaning 'program ran successfully' - is not fixed. There are the error codes in "/usr/include/sysexits.h" which could be used as a guideline, but mostly it's the individual programmer's decision what value to return when. To stay with grep as an example, 0 means it searched and found, 1 means it searched and didn't find anything and 2 means something was wrong - no permission to read the file, file not found or invalid regular expression would all produce a return value of 2.

Holger

---

### Post by webmiester on 2018-09-03
Thank you Holger.

---

