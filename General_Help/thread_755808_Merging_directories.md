---
title: "Merging directories"
date: 2008-04-15
forum: General Help
---

### Post by dsnyders on 2008-04-15
Over the course of many upgrades, hard drive failures, and poor backup planning, I've wound up with many directories which contain essentially the same files. I have about a dozen home/dsnyders directories scattered in various locations. I'd like to merge them into a definitive folder. I've looked at a number of utilities, but they all seem deficient in some way. Either they are too manual, or they consider files to be identical based solely on content, and not by filename.

I'm looking for a tool to merge directories as follows:

merge source destination
If a filename exists in source but not in destination, move it from source to destination.
If a filename exists both in source and destination, compare the two files. If the files are identical, remove the file from the source directory. If the files differ, do nothing.
If there is a subdirectory that exists in the source, but not in the destination, then move it from the source to the destination.
If there is a subdirectory that exists in both the source and the destination, then merge them.
If the source directory winds up empty, remove it.

I'm sure this could be handled with a handful of scripts, but I lack the skill.

---

### Post by diaa on 2008-04-15
I think you need a folder synchronizer, I don't know any for Linux except for [Unison]("http://www.cis.upenn.edu/%7Ebcpierce/unison/")
It'll help you compare the files and take actions accordingly

**Update**: I forgot to mention that Unison is available in Ubuntu repos, to install it:
```
sudo apt-get install unison
```

---

### Post by dsnyders on 2008-04-16
I just tried unison, and it is far too manual.  It goes through file by file prompting for an action.  I have almost a quarter of a million files.  I need an automatic process.

---

### Post by dsnyders on 2008-04-17
Is anybody goog at scripting?

---

### Post by dsnyders on 2008-04-19
*Bump*

---

### Post by ibuclaw on 2008-04-19
Ok, I'm gonna step up and have a go at this (I've been watching this thread for two days now, I've been curious on any development.)
And since that obvious hasn't happened, I thought that I might chip in.

It shouldn't be too difficult. And from first glance. The list of functions shouldn't extend beyond.

du
awk
stat -c %y

Though, I may not get a "barely working" through till late Monday Evening or Tuesday.
As I'm rather flooded by work at the moment.

But keep your ears up.

I'll let you know when I have something

Regards
Iain

---

### Post by dsnyders on 2008-04-19
I'm looking forward to giving your solution a go.  I'm curious as to what you plan to do with the du command.

---

### Post by ghostdog74 on 2008-04-20
```

#!/bin/bash
awk 'BEGIN{
    ################## Simple File/Dir Synchronizer #################
    ## Author: GhostDog74                                       #####
    ## Date: Now
    #################################################################
    q="\047"
    
    # Modifiable variables.
    source="/home/user/peter" 
    destination="/media/usbdisk"
    
    #### Remove all empty source directories #####
    FindEmptyDir = "find "source" -type d -empty -exec rm -rf "q "{}" q " \\;"
    print "Find empty directory command: " FindEmptyDir
    # system(FindEmptyDir) ## uncomment to use
    
    ####  Check all directories first #####
    FindSrcDirCmd = "find "source" -type d" 
    while ( FindSrcDirCmd | getline flinesrc ) {   
        olddir=flinesrc                        
        gsub( source,destination,flinesrc)
        tcmd = "test -d "q flinesrc q
        r = system(tcmd)
        if ( r == 1) {            
            create = "mkdir -p "flinesrc
            print "Create directory command: "create
            #system(cmd)            #uncomment to use.
        }else if ( r==0 ){
                print "Directory "flinesrc" exists"
        }
    }
    #####  Then check the files #########
    FindSrcFilesCmd = "find "source" -type f"
    while ( FindSrcFilesCmd | getline flinesrc ) {
        orgfile = flinesrc
        gsub( source,destination,flinesrc)
        tcmd = "test -f "q flinesrc q
        r = system(tcmd)
        if ( r == 1) {          
            print "Moving source file: "orgfile " to destination " flinesrc  
            movefilecmd = "mv "q orgfile q" "q flinesrc q
            print "move command: "  movefilecmd
            #system(movefilecmd)            #uncomment to use.
        }else if ( r==0 ) {
            print "File "flinesrc" exist..."
            
            ### Start to compare files using md5sum###
            md5cmd1 = "md5sum <"orgfile
            md5cmd2 = "md5sum <"flinesrc
            md5cmd1 | getline md5r1
            md5cmd2 | getline md5r2
            if ( md5r1 == md5r2 ) {
                print "File "orgfile "and file "flinesrc" are the same"  
                print "removing original file "orgile
                rmcmd = "rm "q orgfile q
                print rmcmd
                #system(rmcmd) ## uncomment to use
            }
            close(md5cdm1)
            close(md5cmd2)
            close(rmcmd)            
        }
    }
}'

```

---

### Post by vanadium on 2008-04-20
You outlined a couple of "rules" in your post. I guess that with rsync, you will be able to have it apply some of these rules, but you will need to run it a couple of times for that. You will need to study the manual for that (man rsync).

Unison is excellent to keep two trees, where you work at one moment in one directory tree, another moment in the other, syncronised. Unison does only prompt in situations where it is impossible to take a decision automatically. It does so if both sides contain updated files since the last run: it is then impossible for Unison to know which of both you prefer to keep. Because you run unison for the first time, all files that exist in both trees and that are different will be in that situation. Thus, unison will be your tool of choice once you are done with the "cleanup¨ .

---

### Post by dsnyders on 2008-04-20
rsync may be of help going forward.  However it has a serious drawback which make it unsuitable for untangling the mess I've gotten myself into.  Mainly, it tries to make two directories the same.  I don't have the space on the drive for that.

---

### Post by vanadium on 2008-04-21
> Mainly, it tries to make two directories the same
That is only one of the things rsync can do. Essentially, rsync is a fast and flexible copy tool.

---

### Post by ibuclaw on 2008-04-21
> **dsnyders said:**
> I'm looking forward to giving your solution a go.  I'm curious as to what you plan to do with the du command.

Well... Not **du** on its own, of course :)
I was thinking of putting it through a **pipe**.

It is also a good way to grab all folder/files within the directory too.
ie:
```
 du ~/Documents 
```
outputs all folders in your Documents folder.
But we get a horrible number infront. So we use **awk** to remove it.
```
 du ~/Documents | awk '{print $2}' 
```
Voila!
Now, **du** has a certain flaw in that it prints the list of directories backwards.
ie:
    /Documents/the/very/last/folder
will be printed before
    /Documents/the

But **cat**, his sister CLI tool (**tac**) can solve that.
```
 du ~/Documents | awk '{print $2}' | tac 
```
But why just the folders?
We can find files too with it
```
 du -a ~/Documents | awk '{print $2}' | tac 
```
In some cases, we want to exclude hidden folders/files. Especially when it comes to syncing your home directory.

You'll find that your desktop background has changed here, you suddenly can't click on this button there.
The altering of your personal settings (or hidden files and folders) can cause quite disastrous effects.
So we put in something like this:
```
 du -a --exclude='.*' ~/Documents | awk '{print $2}' | tac 
```
And what is the point of this?
Well, we can trim the new lines and store the output into a string.
Then using a **while** loop with **shift** in a function, we can chronologically go through the hierachy file by file.
```
 du -a --exclude='.*' ~/Documents | awk '{print $2" "}' | tac | tr -d '\n' 
```
There is only one flaw in the above line that is really left to address, and that is the fact that the above code assumes that all your files or folders have no spaces in them.
So, we use **sed** to add an asterisk (*) to fill ALL the spaces.
```
 du -a --exclude='.*' ~/Documents | sed 's/ /*/g' | awk '{print $2" "}' | tac | tr -d '\n' 
```
At long last (after a sizable tutorial all about the wonders of **du**) we have a (half) decent solution.

But lets go for a realworld example.
Lets go for your last option in your request:
> If the source directory winds up empty, remove it.

Using **du**, I would have something like this written to solve that problem.
```

#!/bin/bash

check-empty()
{
    echo "Searching Empty Directories..."
    while [ $# -gt "0" ]
    do
        # In simple terms. "ls" the folder
        # If ls exited successfully (not empty) then we execute the AND "&&" command.
        # If the program didn't (empty) then we execute the OR "||" command.
        [ "$(ls -A "$1")" ] && echo "Not Empty" > /dev/null || echo "Found Empty ($1)"
        shift
    done
}

### Main Logic ###
# The "du" command
export srcdir=$(du ~/Documents | sed 's/ /*/g' | awk '{print $2" "}' | tac | tr -d '\n')
check-empty $srcdir

```
Of course. the **rmdir** command would be used instead of **echo "Found Empty"**

Regards
Iain

---

### Post by dsnyders on 2008-04-22
tinivole,

I really appreciate the tutorial.  I never knew about the tac command.  I was vaguely aware of awk, but you and ghostdog74 have shown me some great stuff.

I did find a small problem with your script, though. The awk '{print $2}' statement returns the second, and only the second, word on the line.  If it hits a filename with blanks then it's going to misfire.

---

### Post by ibuclaw on 2008-04-22
As much as as I'd like to say you're incorrect (in the context of the script I've given)...
I will allow you to prove me wrong, though :)

If you can make that error happen, tell me how to reproduce it.
Then I might consider whether or not it is a possible bug in the script I've produced above.

Regards
Iain

---

### Post by ibuclaw on 2008-04-22
OK!
Here is my collection of scripts.

Sorry for the delay, I did say I'd get it done by Tuesday.
It's just been a bit of a nuance working on the jelly that holds the scripts together.

I also created a fool proof script to edit the config file too. (Took me a full day to write).
You'll figure out what you need to do to edit it.
Although you may have a few warning or error messages on the first time you try to save the file. :)

You'll also be happy to hear that I've followed everything to the letter.
Anything that I wasn't sure about I've put in the "TODO" file.

And I hope that you'll be happy to hear that this script can handle an infinite number of source directories too.

Although I've done my homework and tested it throughly, If you feel that you must test it before you use it on your real files, go ahead.
Infact, I recommend that you make two copies of your files. Backup one lot to a tarball. And then run the script.
If you find that the script has behaved in the way you like and carried out your wishes. Then all I can say it "BRILLIANT!":KS

The only thing that I haven't done yet is embed all the scripts into one consolidated file.

But it shouldn't be too much of a hassle, and besides; each script has it's own unique purpose when ran on it's own.

And lastly, because files are being moved and removed across the filesystem, like you asked. This script will be finished in no more than 10 seconds too.

Anyway, the download is attached below.

Hope you find it of great use.

Regards
Iain

---

### Post by ghostdog74 on 2008-04-22
> **dsnyders said:**
>  The awk '{print $2}' statement returns the second, and only the second, word on the line.  If it hits a filename with blanks then it's going to misfire.

```

du | awk 'NF>2{ $1="";print}{print $2}'

```

---

### Post by dsnyders on 2008-04-23
> **tinivole said:**
> As much as as I'd like to say you're incorrect (in the context of the script I've given)...
I will allow you to prove me wrong, though :)

If you can make that error happen, tell me how to reproduce it.
Then I might consider whether or not it is a possible bug in the script I've produced above.

Regards
Iain

Well, to be honest, I didn't test this within the context of the script.  All I did was try the du | awk '{print $2}' command from your tutorial:

dsnyders@main:/storage$ ls
[Snipped for brevity]
s03e06 The Ark
s03e07 The Celestial Toymaker
s03e08 Gunfighters
s03e09 The Savages
s03e10 The War Machines
s04e01 The Smugglers
s04e02 The Tenth Planet

dsnyders@main:/storage$ du  | awk '{print $2}'
[Snipped for brevity]
./s03e06
./s02e09
./s03e02
./s02e07
./s01e02
./s03e03
./s02e03
.

From that I concluded that there might be a problem.

---

### Post by ibuclaw on 2008-04-23
> **dsnyders said:**
> Well, to be honest, I didn't test this within the context of the script.  All I did was try the du | awk '{print $2}' command from your tutorial:

dsnyders@main:/storage$ ls
[Snipped for brevity]
s03e06 The Ark
s03e07 The Celestial Toymaker
s03e08 Gunfighters
s03e09 The Savages
s03e10 The War Machines
s04e01 The Smugglers
s04e02 The Tenth Planet

dsnyders@main:/storage$ du  | awk '{print $2}'
[Snipped for brevity]
./s03e06
./s02e09
./s03e02
./s02e07
./s01e02
./s03e03
./s02e03
.

From that I concluded that there might be a problem.
[QUOTE=tinivole]
There is only one flaw in the above line that is really left to address, and that is the fact that the above code assumes that all your files or folders have no spaces in them.
So, we use sed to add an asterisk (*) to fill ALL the spaces.
Code:
```

 du -a --exclude='.*' ~/Documents | sed 's/ /*/g' | awk '{print $2" "}' | tac | tr -d '\n'

```
At long last (after a sizable tutorial all about the wonders of du) we have a (half) decent solution.
[/QUOTE]
I did address, that. Try:
```
du | sed 's/ /*/g' | awk '{print $2" "}'
```
fills spaces with asterisks.
Big bonus about asterisks is that when you pass the argument to a function, it ignores them.
So. say if I wanted to make a folder, it would be named "a folder" instead of "a*folder"
Although, in order for that to work, you need quotations around the "$string".
Which, to be honest should be the defacto for BASH scripts. As it flattens out 90% of errors you will encounter.

But, woah! I'm detouring completely.

Back on subject, I've made it so a path will be supplied with the command too to get riddance of the "./" part of the output.
```
du /path/to/folder | sed 's/ /*/g' | awk '{print $2" "}'
```
Don't worry, I've found it all out before.

I know how to make things work in a predictable manner.;)

Version 0.2 is down below (now I'm definitely finished with it) :popcorn:
I've added ghostdog's "du | awk 'NF>2{ $1="";print}{print $2}'" command as a safety feature.
And I've also gotten round to making it one complete script.

Tell us what you think.

Regards
Iain

---

### Post by dsnyders on 2008-04-23
[QUOTE=tinivole;4770488]I did address, that. Try:
```
du | sed 's/ /*/g' | awk '{print $2" "}'
```

Oops!  My bad.

*dsnyders hangs head in shame*

I suppose I should have read the WHOLE tutorial.

Anyways, I am eager to try your scripts once I get the time.

---

### Post by ibuclaw on 2008-04-23
Don't worry.
In the world of logic and science. Everyone is right until proven wrong.

If you were to address me with evidence that something doesn't work, something that I don't have evidence for.
Or you show me a better way to carry out the task (similiar to what ghostdog did earlier) then I will accept my wrongfulness and I will start using your proposed script in future writings instead of my own.

We learn through each other, as a community we are smarter than what we are learning alone.

Regards
Iain

---

### Post by dsnyders on 2008-06-11
Hi All.

I'm sorry to take so long since my last post.  I've going through a boatload of 12-16 hr days at work.  I haven't had a chance to try the scripts to see if they solve the problem.

---

