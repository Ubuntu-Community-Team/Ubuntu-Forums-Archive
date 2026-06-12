---
title: "[SOLVED] Store funtions in a directory...."
date: 2008-06-13
forum: General Help
---

### Post by jeroensd on 2008-06-13
Hello,

I'm working on this exercise:

[I]Create a subdirectory in your home directory in which you can store function definitions. Put a couple
of functions in that directory. Useful functions might be, amongs others, that you have the same
commands as on DOS or a commercial UNIX when working with Linux, or vice versa. These
functions should then be imported in your shell environment when ~/.bashrc is read.[/I]

Right now I have this code so far:

```

if [ -d /home/functions]
then
    sudo rm -r /home/functions
fi
sudo mkdir /home/functions

```

So everytime this script runs it checks if the directory 'functions' already excists. If so, it will be deleted and a new folder will be created.

But how can I store functions in that folder and import them in the shell environment when ~/.bashrc is read?


Is it true to define a function this way:

```

function *functname{*
         *shell commands}*

```

Or so:

```

[I]functname()
{
     shell commands}[/I]

```

How does this work?

Greetings,
Jeroen :)

---

### Post by bingoUV on 2008-06-13
if you want to **store** functions in this directory, why are you deleting the directory everytime? How will you be able to store anything in such a situation?

What do you mean by functions?

---

### Post by ibuclaw on 2008-06-13
Hello there.

To answer your Previous and PM questions first.

1) $@ prints ALL arguments.

ie: If you have a script with just "**echo $@**" in the file.
Running:
```
./foo.sh this is all the arguments
```
Will produce the output
```
this is all the arguments
```


2) echo $10 simply does not work in BASH.
BASH only supports the echoing of arguments $0 to $9.

It treats the rest of the line as a literal string.
ie: If you edit that same test file to have "**echo $10**" instead.
Running:
```
./foo.sh hello
```
Will produce the output
```
hello0
```
Thus, why I used awk to print "$10" in my previous example.





Now, back on this thread...

I agree with bingoUV. It does seem very odd that you want to remove the "functions" folder if you want to store files in it.

Personally, I would remove the all of what you have already and just put in the line:
```
mkdir -p /home/functions
```
Then argument "-p" creates parent directories if non-existance, and is silent when you try to make a directory that already exists.

Yes, that is exactly how you write functions in BASH.
ie:
[PHP]
#!/bin/bash

# Declaration of a function #1
hello()
{
    echo "hello"
}

# Declaration of a function #2
function goodbye
{
    echo "goodbye"
}

# Test the functions to see if they work.
hello
goodbye
[/PHP]

If you wish to store them inside a separate file, you can!
Then when you need to use them, you put in
[PHP]. /path/to/file[/PHP]
To include them in your script/bashrc file.

Example:
Create two files in the same directory with these scripts inside them.
FILENAME: **script.sh**
[PHP]
#!/bin/bash

. include

echo "I'm in here"
hello
echo "Now I'm back again"
goodbye
[/PHP]
FILENAME: **include**
[PHP]
hello()
{
    echo "Hello, I'm in there now"
}

function goodbye
{
    echo "Goodbye..."
}
[/PHP]
Set **script.sh** as executable. Then run.

You'll get the output
```

I'm in here
Hello, I'm in there now
Now I'm back again
Goodbye...

```

Regards
Iain

---

### Post by jeroensd on 2008-06-18
Hi! Thanks for your examples.

I now have a script that creates a directory 'functions'. Is it possible to put already some functions in that directory.

So if i run the bash script, a directory called 'functions' will be created and already has a bunch of functions in it. Is that possible or do I need to create another bash script and save it in that directory?

Greetz,
Jeroen

---

### Post by jeroensd on 2008-06-19
Right now I have something like this:

```

#!/bin/bash

if [ -d /home/functions]
then
    sudo rm -r /home/functions
fi
sudo mkdir /home/functions

cat > /home/functions/functions.sh <<FUNCTIONS
function hello
{
  echo "Hello world"
}

function goodbye
{ 
  echo "goodbye"
}
FUNCTIONS

```

But it goes wrong on de cat line. It sais 'Permission Denied', even if i am logged in as superuser. Why is that?

tinivole helped me a bit with this (thanks!) but I don't know how to fix the permissen denied warning.

I want this to happen if the script runs:

1. A directory called "functions" will be created in the home directory.
2. A file called "funtions.sh" should be created inside the directory with all the functions in it.

Are their other ways to do that?

Greetings,
Jeroen

---

