---
title: "Easy way to delete all hidden files bar those on a white-list?"
date: 2015-05-18
forum: General Help
---

### Post by Rytron on 2015-05-18
Hi.

Is there a way to delete all hidden files bar these below (just a sample from a much bigger list)? Like a script or single line command? Unneeded hidden files build up overtime.

Thanks.

[I].cache/medit
.config/artha.conf
.config/bleachbit
.linuxmint
.local/share/0ad
.local/share/liferea
.moonchild productions
.mozilla
.zsnes[/I]

---

### Post by Keith_Helms on 2015-05-19
This sounds like a good way to get yourself in trouble.  For example, you install a new package and forget to add its config directory to your list of "wanted" files or you forget to add some standard file or directory to the list, like say .profile

If you REALLY want to do it, put the whitelist in a file -  I used filelist.txt in my example - and run the following script:

```
#/bin/bash

IFS=$'\n'
cd ~
for file in .[a-zA-Z0-9]*
do
    echo "checking $file"
    badfile=`echo "$file" | xargs -I{} grep "{}" filelist.txt`
    if [ "$badfile" == "" ]
    then
        if [ -d "$file" ]
        then
            echo "removing directory $file"
            #rm -rf "$file"
        else
            echo "removing file $file"
            #rm "$file"
        fi
    fi  
done
exit
```

This script will find any files or directories that start with . followed by at least one letter or number in your home directory and that are not listed in the whitelist file, which is filelist.txt unless you change the name.  Once you're sure you have all the names set up correctly in your whitelist, you can uncomment (remove the #) the two lines in the script that will actually delete the unwanted files or directories.

---

### Post by Rytron on 2015-05-23
> **Keith_Helms said:**
> This sounds like a good way to get yourself in trouble.  For example, you install a new package and forget to add its config directory to your list of "wanted" files or you forget to add some standard file or directory to the list, like say .profile

If you REALLY want to do it, put the whitelist in a file -  I used filelist.txt in my example - and run the following script:

```
#/bin/bash

IFS=$'\n'
cd ~
for file in .[a-zA-Z0-9]*
do
    echo "checking $file"
    badfile=`echo "$file" | xargs -I{} grep "{}" filelist.txt`
    if [ "$badfile" == "" ]
    then
        if [ -d "$file" ]
        then
            echo "removing directory $file"
            #rm -rf "$file"
        else
            echo "removing file $file"
            #rm "$file"
        fi
    fi  
done
exit
```

This script will find any files or directories that start with . followed by at least one letter or number in your home directory and that are not listed in the whitelist file, which is filelist.txt unless you change the name.  Once you're sure you have all the names set up correctly in your whitelist, you can uncomment (remove the #) the two lines in the script that will actually delete the unwanted files or directories.

Hi Keith.

I backup everything onto an external HDD. So if something did go wrong, I can go back to an old backup.

I ran the script in Xubuntu inside VirtualBox.

I made a sample white-list containing:
[LIST]
[*].config/Mousepad
[*].xsession-errors
[*].local/share/keyrings/
[/LIST]

Everything in the main home directory was deleted - (.bashrc, .profile, etc.). However nothing was deleted in the .config or .local subdirectories.

---

### Post by Keith_Helms on 2015-05-23
> **Rytron said:**
> Everything in the main home directory was deleted - (.bashrc, .profile, etc.). However nothing was deleted in the .config or .local subdirectories.

Is that what you expected/wanted it to do? :p

---

### Post by Rytron on 2015-05-23
> **Keith_Helms said:**
> Is that what you expected/wanted it to do? :p

Not exactly.

For example, in the .config and .local folders -- I only want to keep what's on the white-list - nothing else in those 2 folders is wanted.

---

### Post by Keith_Helms on 2015-05-23
> **Rytron said:**
> Not exactly.

For example, in the .config and .local folders -- I only want to keep what's on the white-list - nothing else in those 2 folders is wanted.

I see.   So you are looking for something that will go down multiple directory levels.  The little script I listed just handles dot files that are directly under your home directory.  It would let you whitelist .config, but not just .config/mozilla for example.

I'll think about it, but making it keep .a/b while deleting .a/c and .a/d might be tricky.

---

### Post by Rytron on 2015-05-23
> **Keith_Helms said:**
> I see.   So you are looking for something that will go down multiple directory levels.  The little script I listed just handles dot files that are directly under your home directory.  It would let you whitelist .config, but not just .config/mozilla for example.

I'll think about it, but making it keep .a/b while deleting .a/c and .a/d might be tricky.

Yes, recursively. I greatly appreciate the code you've done so far -- it's excellent and is still very useful. I hope others can also add their expertise.

---

### Post by Rytron on 2015-05-24
Here's a thought.

I only whitelist files in:
[LIST]
[*]the main home folder (.mozilla, etc.)
[*].config/...
[*].local/...
[/LIST]
So can you modify the script and I could cd to .config and run it and then cd to .local and run it again. Then I could just mass delete all other files and folders easily.

---

### Post by Rytron on 2015-05-31
I put the text file named 'whitelist_local.txt' in '.local/share' and added its own file name to its whitelist (although I could just add the full path of ~/scripts/bash). I also removed the dot in the code to work within the .local and .config dirs. All works fine. Of course I will never run this until I do a full backup first. I also changed the location after 'cd' in the original code (for the .config and .local scripts). So I have 3 white lists and 3 corresponding bash files for them.

Thanks again Keith.

---

### Post by Keith_Helms on 2015-06-01
I'm glad you got it working.   It probably would have taken 3 times as much code to get it to do what you wanted with a single execution.

---

### Post by Rytron on 2015-06-01
> **Keith_Helms said:**
> I'm glad you got it working.   It probably would have taken 3 times as much code to get it to do what you wanted with a single execution.

Thanks to your code and a little tweaking of my own. ;)

Since I would use it rarely - running 3 scripts is no problem.

By the way, is there a way to remove everything to trash instead of outright deleting them? If not, it's ok but it would add a layer of safety.

---

### Post by Keith_Helms on 2015-06-01
> **Rytron said:**
> Thanks to your code and a little tweaking of my own. ;)

Since I would use it rarely - running 3 scripts is no problem.

By the way, is there a way to remove everything to trash instead of outright deleting them? If not, it's ok but it would add a layer of safety.

There are utilities that do that.  A couple of them are described in this posting:

[http://askubuntu.com/questions/213533/command-to-move-a-file-to-trash-via-terminal](http://askubuntu.com/questions/213533/command-to-move-a-file-to-trash-via-terminal)

You would change the rm commands in the script to use one of these commands.

You could also just do it yourself by changing rm to instead mv the file to ~/.local/share/Trash

---

### Post by Rytron on 2015-06-02
Nice one Keith.

---

