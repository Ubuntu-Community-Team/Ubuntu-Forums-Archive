---
title: "Script to batch rename files and make links"
date: 2019-04-14
forum: General Help
---

### Post by freeflyjohn on 2019-04-14
I want to write a script that will perform the following steps:

1. Starting in the source folder, store the name of the file
2. Remove a string of characters from the filename
3. Move the renamed file to a destination folder
4. Make a link to the renamed file in the destination folder
5. Rename the link to the stored file name 
6. Move the link back to the source folder
7. Repeat for remaining files in the source folder

As an example:

In folder SOURCE I have 5 files called:

[LIST]
[*]abcd_FILE1_xyz.txt
[*]abcd_FILE2_xyz.txt
[*]abcd_FILE3_xyz.txt
[*]abcd_FILE4_xyz.txt
[*]abcd_FILE5_xyz.txt
[/LIST]

Starting with the first file in the folder, the script needs to....

1. store the filename 'abcd_FILE1_xyz.txt' 
2. remove the string 'abcd_' and '_xyz' from the filename so that it becomes 'FILE1.txt' 
3. move the renamed file 'FILE1.txt' to the DESTINATION folder
4. make a link to 'FILE1.txt' 
5. rename the link to the stored filename 'abcd_FILE1_xyz.txt'
6. move the link to the SOURCE folder
7. repeat for the remaining 4 files so that:
[LIST]
[*=1]DESTINATION folder has the renamed files:
[LIST]
[*=1]FILE1.txt
[*=1]FILE2.txt
[*=1]FILE3.txt
[*=1]FILE4.txt
[*=1]FILE5.txt
[/LIST]

[*=1]SOURCE folder has links to the renamed files in the DESTINATION folder:
[LIST]
[*=1]abcd_FILE1_xyz.txt (link to FILE1.txt in DESTINATION folder)
[*=1]abcd_FILE2_xyz.txt (link to FILE2.txt in DESTINATION folder)
[*=1]abcd_FILE3_xyz.txt (link to FILE3.txt in DESTINATION folder)
[*=1]abcd_FILE4_xyz.txt (link to FILE4.txt in DESTINATION folder)
[*=1]abcd_FILE5_xyz.txt (link to FILE5.txt in DESTINATION folder)
[/LIST]
[/LIST]

There might be more efficient ways of doing this, like removing the string during the move command etc

How can I implement this in a script file so its all done automatically ?

---

### Post by TheFu on 2019-04-14
It this a trick question?
a) Learn to script in a language that does what you need.  bash, perl, python, ruby, awk will all do this. Probably others as well.
b) pay someone else to write a script that does what you need.

How are duplicate filenames handled?  
How are filenames that contain disallowed characters handled?
How do really full directories get handled?  Any directory with over about 500 files has too many and gets slow. Best to split them up into a tree of some sort. This can make for efficiencies.

If you already know a scripting language, that would probably be where I started.
Personally, I'd use perl, but I know perl already.
I could do this in bash as well, though it would be harder for me to accomplish.

"link" is vague.  Hard link or soft-link?  Will the other directory be on a different physical disk?
Do you really need the links or just access to the original name?  Could metadata stored inside the file header solve that instead?  I do this with photos all the time.
Keeping the original name is a hassle, best avoided, if possible.

BTW, it is usually best to show what you have and what you want, nothing more.  The actual processing doesn't matter, does it?  I think you have many extra steps.
Also, doing this for 500 files one time is very different from doing this for 500,000 a day for the next 10 yrs.  I would solve it completely diferently.

But only you know the real requirements vs the self-inflicted requirements.

Google "ABSG bash" for a bash learning site. [http://www.tldp.org/LDP/abs/html/abs-guide.html](http://www.tldp.org/LDP/abs/html/abs-guide.html)
There are beginner and intermediate guides too.

---

### Post by oldfred on 2019-04-14
We do not do homework.

If you have a script that is not quite working someone may give clues on fixes.

---

### Post by freeflyjohn on 2019-04-14
No its not a trick question !

Im an electronics/software engineer by trade and use embedded C and MATLAB simulink but have little experience with bash etc

[COLOR=#000000]How are duplicate filenames handled? 
[/COLOR] - There are no duplicate file names so it doesn't need to be advanced enough to handle this situation
[COLOR=#000000]How are filenames that contain disallowed characters handled?
[/COLOR] - There are no file names that contain disallowed characters so it doesn't need to be advanced enough to handle this situation
[COLOR=#000000]How do really full directories get handled? Any directory with over about 500 files has too many and gets slow. Best to split them up into a tree of some sort. This can make for efficiencies.
- There are less than 20 files in a folder (the files are .mkv files with seasons and episodes)
[/COLOR][COLOR=#000000]Hard link or soft-link? Will the other directory be on a different physical disk?
[/COLOR][COLOR=#000000] - I've never got my head around what the difference between hard and soft links are (I understand short-cuts on Windows).  Normally when I make these links I use Ubuntu desktop and right click->make link.  The directories are all on the same physical disc

Im simply trying to arrange my media library, nothing more.  I could do it manually but thought it would be quicker and more useful to write a script.

Ive managed to use 'rename' to strip out strings from the filename and I know how to copy and move files.  Ive also used '[/COLOR]sudo ln -s' to link files.

Im not asking for someone to write the script for me, just some guidance/tips on how to handle the other things I need to do.

And I am aware the method I described is probably long winded and inefficient etc.  I was just trying to explain what I want to do, which I expect should be simple enough once you know how.

---

### Post by TheFu on 2019-04-14
Perhaps writing a script that generates a script is what you need?  I do this type of thing all the time.

Windows "shortcuts" are GUI objects, not file system objects like both symlinks and hardlinks.  Hardlinks are limited to a single file system. You can learn the difference at wikipedia. Hardlinks have the same data, just different inodes with a reference count.  Symlinks are an inode that points to the location of another inode anywhere (there are limitations, but not within the same file system). If the location being addressed is removed/deleted, then the symlink is orphaned.  Backup tools trying to maintain multiple versions of a backup set commonly use hardlinks.

Post some code for the different functions.  Bash has functions.

IMHO, symlinks for purposes like this are a mistake.  There are almost certainly better solutions for whatever this symlink complexity is meant to address.

---

