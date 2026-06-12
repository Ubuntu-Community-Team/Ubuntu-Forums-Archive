---
title: "$PATH: howto add all subdirs in a branch?"
date: 2006-10-24
forum: General Help
---

### Post by quixote on 2006-10-24
How can I add a whole set of directories to my $PATH, without having to enumerate each one?

I tried to install Photoshop under Wine, and it tries to start, but then says it can't find its plugins, fonts, etc etc, and craps out.  Everything is there, so it must be that the path info is missing.  If I add a specific dir to the $PATH in my bash_profile, then it can find that dir.  However, there are dozens of directories under Photoshop. I don't want to have to laboriously type out each one!  How do I add /home/me/.wine/Programs/Photoshop[and everything including that dir and all the subdirs below it] ?  

I tried /home/me/.wine/drive_c/Programs/Photoshop*  and /home/me/.wine/drive_c/Programs/Photoshop/* but neither of those seemed to do it.

I've looked everywhere on the Ubuntu forums, linuxquestions.org, and even including my three fat Linux books trying to find an answer to what has to be a simple question with an obvious answer.  It's driving me nuts.  Help, please!

---

### Post by IYY on 2006-10-24
I don't know the answer to your problem, but I know what I would do to fix it if I encountered it. I'd make a single directory, call it photoshop_bins for example, and write a script to create links to all plugins in the photoshop subdirs.

You can use the following command to find all executable files in the current directory and its subdirectories:

```
find . -perm /+x -type f
```

---

### Post by quixote on 2006-10-25
That's an interesting approach.  I hadn't thought of that, and I'll have to try it, if I can.  I'm not good at scripts. :(   

I'm still very eager to hear if anyone knows how to solve the $PATHS issue.

---

### Post by quixote on 2006-10-25
PS.  I like your sig.  Great link.)

---

### Post by IYY on 2006-10-25
Here's a script for you:

create a directory called 'bins' at the top level of your tree (/home/me/.wine/drive_c/Programs/Photoshop/bins) and then, while in 

```
mkdir /home/me/.wine/drive_c/Programs/Photoshop/bins
cd /home/me/.wine/drive_c/Programs/Photoshop/
 find . -perm /+x -type f -exec ln -s .{} bins/ ';'
```

That is it! 'find' lists all files of type f ("file" as opposed to "directory") with execute set on (+x) and on each filename it executes 

```
ln -s .{} bins/
```

where {} is the filename in the form ./path/to/some/file. The way it works is a bit of a hack: the dot before the {} changes the form to ../path/to/some/file.

---

### Post by quixote on 2006-11-03
Thanks for responding!  I'm supposed to get email thingies when that happens, but none came, so I didn't check.  Pleasant surprise to find this when I checked back by chance.

I have some very vague idea what you're doing here, but not enough.  When I tried entering the "find" line, I got the error message "find: missing argument to -exec"  I don't know enough about it to figure out how to fix it.  I looked at the man page for find, and that implied maybe the curly braces also needed single quotes around them.  But when I tried it, I got the same error message.

One problem is maybe that it's very hard to see spaces.  Maybe I didn't enter the line right.  Using ' _ ' for a space, what I have is:
find _ .-perm _ /+x _ -type _ f _ -exec _ ln _ -s _ .{} _ bins/';'

Thanks for your help!

---

### Post by quixote on 2006-11-03
Actually, on re-reading the thread, I thought I'd try your first suggestion (find . -perm /+x -type f).  That went zipping through all the subdirs.  Unfortunately, it's been a couple of weeks since I was playing with the photoshop-under-wine install, and now I can't remember how to start Photoshop.  How dumb can I get? :redface: 

So, until I figure that out, I won't know whether the find command solved the problem or not.  Will post again after taking some 'smart' pills.

---

### Post by quixote on 2006-11-03
Well, the command apparently is "sudo wine [path to Photoshop]/Photoshop.exe"  So far, so good.  But it did exactly the same thing as before, i.e. being unable to find all the files it wants.  Quite possibly, I'm wrong thinking it's a $PATH problem.  It may well be something in the whole way Photoshop interacts with wine.  (Plus, just to make things better--or worse--I've since installed Edgy, so that's another complicating factor.)

Anyway, I think I'll give up for now, and just boot into Windows when I absolutely need Photoshop, which is about twice a year. ...

---

### Post by Azerthoth on 2006-11-03
Well to answer one question you can add to your path simply by editing it into your ~/.bash_profile.

A second option would be to alias the command in your ~/.bashrc with something like:

alias photoshop='wine /absolute/path/to/the/photoshop/exe'

---

### Post by quixote on 2006-11-11
Azerthoth, I know I can add to the path by editing bash_profile.  But I don't know how to add a path **and all its subdirectories**.  If you can give me the actual line I should input for that, I'd be most grateful!  When I add a path, e.g. to /home/me/docs, it adds only the dir "docs" and not its subdirs, ~/docs/nastydocs, ~/docs/betterdocs, and ~/docs/beautiful_pics. It does that whether I enter ~/docs, ~/docs/, or ~/docs/*  

The suggested alias gives me the same error messages I've been getting, saying it can't find the necessary font files, plugins, and so on, which are all in subdirectories.  I figured those messages meant I was having path troubles, but I'm not so sure anymore.  It may simply be something flaky in trying to run PhotoShop CS2 under Wine.  The program almost loads: the main window is there, with the typical menu bar, and the tool dock, but after lots of messages saying it can't find this and that, I get a final error message saying it couldn't load because of a missing font resources file, and the whole window disappears.  Meanwhile, the console, has repeated error messages all saying "err:shell:HCR_GetFolderAttributes HCR_GetFolderAttributes should be called for simple PIDL's only!"  Whatever that means.  But that's what makes me think the problem may lie deeper than mere paths.

Thanks for your help!

---

### Post by David_T on 2006-11-11
Putting this in your .bashrc will do what you want, but I think the tutorials you get when you google ``install photoshop wine'' will serve you better.  Out of curiosity which version of ps are you installing?

```

original_path_list=`echo $PATH | tr ":" " "`
for directory in $original_path_list
do
    for subdirectory in `find $directory -type d`
    do
        export PATH=$PATH:$subdirectory
    done
done

```

---

### Post by quixote on 2006-11-16
I'm trying to install Photoshop CS2.  I've let it slide the last couple of weeks, since Gimp does almost everything I need.  I use Photoshop a couple of times a year, so, really, my interest in this is more to learn how to use wine and run things under it than to do "real work."  (Anything, to avoid real work.;) )

---

