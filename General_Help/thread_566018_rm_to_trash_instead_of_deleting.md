---
title: "rm to trash instead of deleting?"
date: 2007-10-02
forum: General Help
---

### Post by bone2006 on 2007-10-02
On my ubuntu server I'm running everything command line and noticed that rm doesn't take it to the trash can. What is a good way of changing rm so that it will move to a directory?
I was thinking of changing the alias, but then how would I dump the directory?

I saw this posted 

run:
mv /usr/bin/rm /usr/bin/rm.bak

then create this script for rm

#!/bin/bash

mkdir ~/.Trash &> /dev/null

while [ ! -z "$1" ]; do
    mv "$1" ~/.Trash/
    shift
done

problem is that rm doesn't seem to be in the usr directory.   Any help is appreciated or what most people do if they run just the command line with rm

---

### Post by prince_niceguy on 2007-10-03
you can find where rm is located by typing the following

$ locate rm

once found you can replace the same.

---

### Post by prince_niceguy on 2007-10-03
on my comp it is in /bin/

---

### Post by scruff on 2007-10-03
To find a program, use:

```

which foo

e.g.:
sean@sean-laptop:~/scripts$ which rm
/bin/rm

```

But **do not** replace the actual command there. An alias is just that. Edit your ~/.bashrc file and put this in there:

```

alias mrm="mv $1 ~/Desktop/Trash"

```

Or make it more similar to the stuff you listed to handle more than one agrument at a time. I used "mrm" to mean, 'my rm'. You don't want to mess around with such a fundamental command such as rm itself.

---

### Post by slimdog360 on 2007-10-03
mv whatever ./trash

---

### Post by FranMichaels on 2007-10-03
Hello :)

First off I really wouldn't replace rm... But if you must
*which rm*
Will return the location. Using *locate* would find every file with the letters 'rm' in it...

I usually do
*mv  the_file_or_folder_you_want_to_delete ~/.Trash*

I'm still a novice with bash... but you could create a simple script

in the home folder

*mkdir bin*
*cd bin*

put your rm script in there (you may need to restart)
let's call it my_rm

then you can just type

my_rm whatever

And you'll still have the default rm ;)

P.S. Don't forget to chmod your script, or it won't be executable.

EDIT: Nevermind, read Scruff's post. My post looks like a rehash. Oh well, I don't like to edit my .bashrc, just a personal preference I guess... I rather just stick my stuff in ~/bin.

---

### Post by bone2006 on 2007-10-03
thank you all for the help
I'll change the alias to mrm instead, really appreciate the help.

---

### Post by bone2006 on 2007-10-03
For some reason it's not working and somethings aren't making since to me.  I'm using ubuntu server, so there isn't a Desktop folder nor Trash folder.  I created a hidden folder in the home directory called .trash and then used this alias

alias mrm="mv $1 ~/user/.trash"

does the $1 mean to take the argument and place it before the path?  I'm just not sure what the $1 does, but eitherway here's the results I'm seeing


user@server:~/upload$ mrm FileZilla_3.0.1_i586-linux-gnu.tar.bz2.bak
mv: cannot overwrite non-directory `FileZilla_3.0.1_i586-linux-gnu.tar.bz2.bak' with directory `/home/user/.trash/'
user@server:~/upload$

When I try sudo and then mrm it says the command cannot be found, but when I do just mrm and the file name the results are above.

Thanks in advance.

---

### Post by scruff on 2007-10-03
Sorry. Maybe alias does not support variables like that (i had never tried it so...).

Replace your alias with this instead:

```

mrm()
{
    mv $1 ~/user/.trash
}

```

Then issue this command:

# source ~/.bashrc 

to pick up the new changes. Try that and let me know if it works.

---

### Post by scruff on 2007-10-03
Better yet - get fancy with your original function so it can process multiple arguments:

```

mrm()
{
    while [ ! -z "$1" ]; do
        mv "$1" ~/user/.trash/
        shift
    done
}

```

---

### Post by foobark on 2008-04-03
Hi there, 

I tried to make the best solution I could for this problem and have made a bloated script. But it works well. It not only moves files to the trash bin but it also makes it show up in the kde trash applet  so that you can restore what you've rm'd. 

I've looked over my script as many times as I can and if there's something wrong with it I'm not going to find it. I'm the only one that has tried/used this script so use at your own peril.  That being said, I've tried to make it as benign as possible and have tested it on a few kubuntu machines. 

Get it at: 
[http://slowburn.net/projects/trash_rm/trash_rm.tgz](http://slowburn.net/projects/trash_rm/trash_rm.tgz)
( I would have posted it in-line here but it is full of comments and tops out at 200 or so lines ) 
 
To use  this script you can do the following: 

tar zxvf trash_rm.tgz 
cd trash_rm-v.95
touch foo1 foo2 foo3  # create some test files 
mkdir bar1 bar2 bar3  # create some test directories
./trash_rm -v foo1 foo2 foo3   #use the verbose option
./trash_rm -r bar1 bar2 bar3   #use the -r option for directories

# Check your trash can applet thingee and see if you can restore it. 

Use a -h option to see what options are available. Let me know if any one tries this and has any problems. I may try to find a different thread to post this at.

---

