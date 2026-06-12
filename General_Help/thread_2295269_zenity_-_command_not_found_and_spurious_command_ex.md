---
title: "zenity - command not found and spurious command execution"
date: 2015-09-17
forum: General Help
---

### Post by drm200 on 2015-09-17
I've been having some problems with my zenity scripts ... and I have figured out when it is happening but don't know if it is a feature, a bug or my programming.  It originates from my desire to pass the values of a listbox back to the calling function.

So I have created a simple script:

```
#!/bin/bash
exec 5> debug_output.txt
BASH_XTRACEFD="5"
set -x
PS4='$LINENO: '


listbox ()
{

    ans=""
    ans=$(zenity  --list  --title="Test" --text="Select handling method" --column= --hide-header "no echo" "echo")

    if $ans
    then
        #cancel pb depressed
        echo "cancel"
        zenity --info --text="Cancel depressed"
    else
        #cancel pb not depressed
        echo $ans
        zenity --info --text="Cancel pb NOT depressed.  Selection: $ans"
    fi
}

listbox
#end of script
```

There are 3 script options:

1. Cancel pb was pushed ... this seems OK.
2. "no echo" was selected from this list box ... and then "OK" depressed.... In this case the script seems to work, but their is an error in the terminal "Command not found"
3. "echo" was selected from the list box ... and "OK" depressed. .... In this case there is no "Command not found" error but the script executes the "echo" command.

Normally, I am getting these "command not found" errors ... and the script is not working correctly. But if the text in the listbox is a command, the script tries to execute it.  

Some things I've tried:
if i change the calling function "listbox" to
ret=$(listbox)

then the results are different.  In this case the script always thinks I am depressing the "cancel" button ... even if I am actually depressing the "OK" button

I also tried calling with this method:
ret="$(listbox)"

In this case, if I select "no echo" and "OK" ... I still get the error "command not found" but the script correctly determines that i have depressed the "OK" button.
However, if I select  "echo" and "OK'... the script thinks I have depressed the "Cancel" button ... even though I depressed the "OK" button.

what is wrong here?  Can someone explain what is going on and why?

---

### Post by sudodus on 2015-09-17
ans will be either "echo" or "no echo" or "" (blank).

and you should check for those values instead of checking as if ans were a logical variable (true or false).

If you want to check for the 'cancel' button and 'OK' without anything selected, you should check for the exit status

```
if [ $? -eq 0 ]
then
 ...
elif [ $? -eq 1 ]
 ...
else
 ...
fi
```

---

### Post by drm200 on 2015-09-17
I had started out with something similar to your suggestion.  But it wasn't working and before posting here, I had spent several hours looking at other posts.  In the end it seemed the correct method for handling this was given in this reply in another post:

"A common problem. Zenity does not return an actual character (0 or 1) it returns a boolean operator (true, false). Therefore, you only need to use:"

Code:
if $RenameAnswer
then
     blah blah
else
    blah blah
fi


so, I had thought that the above method was always correct.  I believe your suggestion is using "integer comparison" ... and not boolean.  But I will try your suggestion and report back.

But I am still confused why zenity would be giving out the "command not found" based upon my listbox text .. it was precisely because I kept getting this error I decided to use "echo" in my listbox text as it is a command. .... And voila it stopped complaining about the "command not found" when "echo" was selected ... and it executed the command.


thanks

---

### Post by sudodus on 2015-09-17
You should also provide a finishing curly parenthesis '}' between fi and listbox.

if the content of 'ans' is executable, "$ans" will run that executable code, and the same with

```
if $ans
then
...
```

-o-

Compare the following command for two values of 'ans'

```
ans="echo 'Hello World'"
if $ans;then echo success;else echo failure;fi
```

Assume that there is ***no command*** with the name 'dont-say'.

```
ans="dont-say 'Hello World'"
if $ans;then echo success;else echo failure;fi
```

Edit: ***Run*** those command lines :-)

---

### Post by drm200 on 2015-09-17
... There is a "}" in my actual code ... I just missed it in the cut and paste to the forum... Sorry for that misdirection but the problems I'm having have the correct ending curly parenthesis.  I'll see if I can still edit that in my original post so that others do not spend time thinking that is the problem.  The code just doesn't run if it is missing (I just verified that).





> **sudodus said:**
> You should also provide a finishing curly parenthesis '}' between fi and listbox.

if the content of 'ans' is executable, "$ans" will run that executable code, and the same with

```
if $ans
then
...
```

-o-

Compare the following command for two values of 'ans'

```
ans="echo 'Hello World'"
if $ans;then echo success;else echo failure;fi
```

Assume that there is ***no command*** with the name 'dont-say'.

```
ans="dont-say 'Hello World'"
if $ans;then echo success;else echo failure;fi
```

Edit: ***Run*** those command lines :-)

---

### Post by sudodus on 2015-09-17
Good that '}' is there :-)

How to use "$ans" and $?

```
if [ $? -eq 0 ]
then
 ...
elif [ $? -eq 1 ]
then
 ...
else
 ...
fi
```

```
if [ "$ans" == "echo" ]
then
 ...
elif [ "$ans" == "no echo" ]
then
 ...
elif [ "$ans" == "" ]
then
 ...
else
 ...
fi
```

---

### Post by drm200 on 2015-09-17
```
if [ $? -eq 0 ]
then
    echo "OK key depressed"
    zenity --info --text="OK key depressed"
elif [ $? -eq 1 ]
then
   .......

else
 ...
fi
```


With the above code, when the "cancel" button is depressed, it triggers the condition ( -eq 1).  

But there is never an event for "-eq 0" .... I'm expecting when the "OK" key is depressed for it to return "-eq 0".   But that never happens.  So, I don't know how to trap the "OK" key.

All I can come up with is:

```
if [$? -ne 0] #anything but the "OK" key
then # assume cancel 
      .....
else # it must have been the "OK" key
     .....
fi

```

but this code is not so far from the boolean I originally had and doesn't seem/feel correct  .... but when using this code I no longer have the "command not found" error.



> **sudodus said:**
> Good that '}' is there :-)

How to use "$ans" and $?

```
if [ $? -eq 0 ]
then
 ...
elif [ $? -eq 1 ]
then
 ...
else
 ...
fi
```

```
if [ "$ans" == "echo" ]
then
 ...
elif [ "$ans" == "no echo" ]
then
 ...
elif [ "$ans" == "" ]
then
 ...
else
 ...
fi
```

---

### Post by sudodus on 2015-09-17
This is going around in circles. I think because we are misunderstanding each other.

Please describe what you want to do with your script! Not the test case with 'no echo' and 'echo', but the real task. The I might be able to help you get further with it :-)

For example, you can make a list of the tasks (alternatives) to select in the zenity window, just a list of lines (no programming).

---

### Post by sudodus on 2015-09-17
This is going around in circles. I think because we are misunderstanding each other.

Please describe what you want to do with your script! Not the test case with 'no echo' and 'echo', but the real task. The I might be able to help you get further with it :-)

For example, you can make a list of the tasks (alternatives) to select in the zenity window, just a list of lines (no programming).

---

### Post by Habitual on 2015-09-18
```
if [[ $ans = "Hello World" ]] ; then echo success;  else do stuff ; fi
```

---

### Post by drm200 on 2015-09-18
> **sudodus said:**
> This is going around in circles. I think because we are misunderstanding each other.

Please describe what you want to do with your script! Not the test case with 'no echo' and 'echo', but the real task. The I might be able to help you get further with it :-)

For example, you can make a list of the tasks (alternatives) to select in the zenity window, just a list of lines (no programming).

Originally, I was using the zenity list and only working with the "OK" response ... and that was straightforward to code.  But when I needed to also consider the user depressing "Cancel" i ran into problems.

The "Cancel" button returned a value of 1 ... but the "OK" response from zenity was to provide the selected text. (I was expecting zenity to provide a "0" response to "OK"... but that just doesn't happen for this list box configuration)

So if code is waiting for a "1" when "Cancel" is depressed ... and instead a text response is supplied because "OK" is depressed ... the code bombs.  So, I've recoded to handle this.

The other problem of "command not found" was remedied by following your suggestion to no longer test using this format: 

 ```

ans=$(zenity  --list  --title="Test" --text="Select handling method" --column= --hide-header "no echo" "echo")

   if $ans

    then
        #cancel pb depressed
        echo "cancel"
        zenity --info --text="Cancel depressed"
    else
        #cancel pb not depressed
        echo $ans
        zenity --info --text="Cancel pb NOT depressed.  Selection: $ans"
    fi

```

 Although it is interesting to discover that I can execute commands via the button label using the above method .... It seems quite easy with zenity to do "unintentional" things because of not following the argument structure perfectly. I think zenity needs to be parsing/filtering the inputs to eliminate unwanted dangerous reactions.  

thanks for the help.

---

### Post by HermanAB on 2015-09-19
The list box returns "" when you press cancel.

---

### Post by sudodus on 2015-09-19
zenity provides a way to identify what the user selects in a menu list. It must be your responsibility as a programmer to use that information in a correct way. zenity would be crippled, if it would be parsing/filtering the inputs to eliminate unwanted dangerous reactions.

---

### Post by drm200 on 2015-09-21
> **HermanAB said:**
> The list box returns "" when you press cancel.

I had not figured that out ... but is good to know.  Thanks

---

