---
title: "sh/dash problem"
date: 2012-12-12
forum: General Help
---

### Post by BAWBCEN1TY on 2012-12-12
I began to look into bash scripting today, and naturally the first script I wrote was **helloworld.sh**. 
```
#!/bin/bash
echo "Hello, world!"
```

I put this file in **/bin**. And I can get it to run successfully when typing ```
**user@server:~$ bash helloworld.sh**
```

I then began to read that "dash" is another shell in Ubuntu. So I tried running it using dash, but it didn't work. ```
**user@server:~$ dash helloworld.sh**
dash: 0: can't open helloworld.sh
```

But when doing it as follows, ```
[B]user@server:~$ dash
$ helloworld.sh[/B]
Hello, world!
```
it executes it perfectly. 

So, I am just wondering why it fails the first way with **dash**, but succeeds the second?

---

### Post by vasilisc on 2012-12-12
maybe need
#!/bin/**dash**
echo "Hello, world!"

---

### Post by rnerwein on 2012-12-12
> **BAWBCEN1TY said:**
> I began to look into bash scripting today, and naturally the first script I wrote was **helloworld.sh**. 
```
#!/bin/bash
echo "Hello, world!"
```I put this file in **/bin**. And I can get it to run successfully when typing ```
**user@server:~$ bash helloworld.sh**
```I then began to read that "dash" is another shell in Ubuntu. So I tried running it using dash, but it didn't work. ```
**user@server:~$ dash helloworld.sh**
dash: 0: can't open helloworld.sh
```But when doing it as follows, ```
[B]user@server:~$ dash
$ helloworld.sh[/B]
Hello, world!
```it executes it perfectly. 

So, I am just wondering why it fails the first way with **dash**, but succeeds the second?
hi
it's your:[COLOR=Red] #!/bin/bash[/COLOR] in your script - shell mismatch.

---

### Post by CaptainMark on 2012-12-12
As an unrelated but useful tip you shouldn't add your script to the /bin directory, this is a folder meant to contain binaries for all of your installed programs, your computer has a list of directories to check inside when its given a program name to execute, you can add to this list by opening the file .profile that is hidden in your home directory and finding the line that should look like this     PATH="$HOME/bin:$PATH" and adding any directory to the colon seperated list so it looks like this     PATH="$HOME/bin:$PATH:[COLOR="Red"]/home/mark/Documents/bash[/COLOR]"

EDIT: Bear in mind this does not work recursively so the directory you add must contain your scripts, it cant contain directories containing scipts

---

### Post by drmrgd on 2012-12-12
Just to add on to Mark's excellent advice, the default behavior of the shell (based on what's in the .profile file that Mark described) is to automatically add ~/bin to your $PATH.  There is no ~/bin folder by default, though.  However, if you create a ~/bin folder and then reload your session (just exit out of the terminal window and start a new one), you'll see that ~/bin is now in your path.  You can check by running this before and after you create ~/bin:

```
echo $PATH
```

What this means is that you can also add your custom scripts to ~/bin and run them just like system programs (i.e. just type the name of the program from anywhere rather than adding the full path and/or the interpreter to the execution command).  This is a better way than to add them to /bin.

---

### Post by rnerwein on 2012-12-12
> **drmrgd said:**
> Just to add on to Mark's excellent advice, the default behavior of the shell (based on what's in the .profile file that Mark described) is to automatically add ~/bin to your $PATH.  There is no ~/bin folder by default, though.  However, if you create a ~/bin folder and then reload your session (just exit out of the terminal window and start a new one), you'll see that ~/bin is now in your path.  You can check by running this before and after you create ~/bin:

```
echo $PATH
```What this means is that you can also add your custom scripts to ~/bin and run them just like system programs (i.e. just type the name of the program from anywhere rather than adding the full path and/or the interpreter to the execution command).  This is a better way than to add them to /bin.
hi
i agree that the script should not stored in /bin but i think there is another problem may be a problem with dash.
my script bla.sh is stored in my ~/bin
contents is:

#!/bin/bash
echo "my permissions are:-rwxr-xr-x 1 richi richi 22 Dez 12 18:54 /home/richi/bin/bla.sh"
echo "my PATH is:/home/richi/bin:/home/richi/scripts:/bin:/sbin:/usr/bin:/usr/sbin:/usr/local/bin:/usr/local/sbin"

1. when i call it from ~/          --> [COLOR=Red]dash[/COLOR] bla.sh --> i get: dash: 0: Can't open bla.sh
2. when i call it from ~/          --> bla.sh            --> it works
3. when i cd to           ~/bin      --> dash bla.sh  --> it works

i am not a unix/linux noob but i think i missed something.
can anybody explain me what's going on.

by the way - man das gives me: dash is the standard command interpreter for the system.

---

### Post by drmrgd on 2012-12-12
Not sure why the second case works.  That shouldn't work as the file is not located in ~/.

Dash is not the same as Bash.  You've already indicated you want the script to be interpreted by Bash (hence the #/bin/bash at the start).  Why try to launch with dash <script>?  It works in this case because you've overridden the shebang and forced dash to interpret the script, and since there's no bash specific syntax in there, it works OK.  Not the best way to do it, though.

In the first case, you're asking dash to run a file that's not there (the file is not in ~/, but rather ~/bin if I understand you).  In the second case, you've asked the script to be run by either dash (if no shebang was indicated as dash is the default) or the interpreter indicated by the shebang. Again, not sure why that works as the script is not in that location.

---

### Post by steeldriver on 2012-12-12
Don't forget that when you do

```
dash bla.sh
```at the command line, the current shell only knows that you are invoking a command with an argument - it can't know that 'dash' is itself a command interpreter or the 'bla.sh' is a shell script. In other words, the fact that bla.sh is on your current shell's PATH is irrelevant because it treats 'bla.h' as a parameter (and won't attempt to expand it to ~/bin/bla.sh or whatever).

What matters is the *dash* search path - and there the difference seems to be that:-

```
dash -c bla.sh
```explicitly treats 'bla.sh' as a **c**ommand, and searches its $PATH (inherited from the invoking shell); whereas

```
dash bla.sh
```treats 'bla.sh' as a plain file *containing* commands - and does not use $PATH to find it if it cannot do so in the current directory

That's the best I can come up with...

---

### Post by drmrgd on 2012-12-12
> **steeldriver said:**
> Don't forget that when you do

```
dash bla.sh
```at the command line, the current shell only knows that you are invoking a command with an argument - it can't know that 'dash' is itself a command interpreter or the 'bla.sh' is a shell script. In other words, the fact that bla.sh is on your current shell's PATH is irrelevant because it treats 'bla.h' as a parameter (and won't attempt to expand it to ~/bin/bla.sh or whatever).

What matters is the *dash* search path - and there the difference seems to be that:-

```
dash -c bla.sh
```explicitly treats 'bla.sh' as a **c**ommand, and searches its $PATH (inherited from the invoking shell); whereas

```
dash bla.sh
```treats 'bla.sh' as a plain file *containing* commands - and does not use $PATH to find it if it cannot do so in the current directory

That's the best I can come up with...

Excellent explanation!  I didn't think of it that way, and this makes a lot of sense.  Thanks for the clarification!

---

### Post by rnerwein on 2012-12-13
> **steeldriver said:**
> Don't forget that when you do

```
dash bla.sh
```at the command line, the current shell only knows that you are invoking a command with an argument - it can't know that 'dash' is itself a command interpreter or the 'bla.sh' is a shell script. In other words, the fact that bla.sh is on your current shell's PATH is irrelevant because it treats 'bla.h' as a parameter (and won't attempt to expand it to ~/bin/bla.sh or whatever).

What matters is the *dash* search path - and there the difference seems to be that:-

```
dash -c bla.sh
```explicitly treats 'bla.sh' as a **c**ommand, and searches its $PATH (inherited from the invoking shell); whereas

```
dash bla.sh
```treats 'bla.sh' as a plain file *containing* commands - and does not use $PATH to find it if it cannot do so in the current directory

That's the best I can come up with...
hi
ok that's the way i understand it.
thanks

---

### Post by CaptainMark on 2012-12-13
This is exactly right

---

