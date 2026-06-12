---
title: "Auto Delete Empty Folders?"
date: 2007-03-03
forum: General Help
---

### Post by Darko Beta on 2007-03-03
Does anybody know of a good app for deleting empty folders?  I have what I assume is a common problem: I have managed my music through various music programs that will delete files--but the artist and album folders are left there forever.  Google found me programs for Windows but I can't find a good Linux app.

---

### Post by zvacet on 2007-03-03
O.K.Obvius things first.Right click on folder and select &#733;move to trash&#733;.If that is not working option for you go to terminal and 
```
sudo -i
```
```
cd /directory_where_folder_is
```
```
rm -r foldername
```

---

### Post by po0f on 2007-03-03
zvacet,

I'm almost positive that Darko Beta is looking for a way to automate this task.  Music directories can contain hundreds of folders, it would be kinda tedious to manually delete all the empty directories.  :)

---

### Post by omrsafetyo on 2007-03-03
I think he is looking more for like a script that will cycle through and delete any and all empry folders - sort of like a clean-up, something like:

find dir2 -depth -empty -type d -exec rmdir {} \;


he doesn't want to use rm -r foldername, because that will accidentally delete full directories.  If he uses rmdir, non-recursively, it will only delete empty ones.

---

### Post by Darko Beta on 2007-03-03
Yes, this is correct.  I want to automate the task.  Here's an example of one of the Windows progs I found that do it:

[http://www.softpedia.com/get/Others/Miscellaneous/Remove-Empty-Directories.shtml](http://www.softpedia.com/get/Others/Miscellaneous/Remove-Empty-Directories.shtml)

It is a music directory with hundreds of folders, and I maintain my music by deleting stuff here and there that I don't listen to (almost all obtained from eMusic!) to avoid my collection swelling too big.  The folders for these files remain, empty.  It might be a bit fussy to want them gone, but aren't we Linux users all a little fussy?  :)

---

### Post by SuSUntu on 2007-03-03
**WARNING - The following contains code that deletes items from your computer. Understand what it does before using it. I also cannot be held responsible for its use or misuse.**

Here's an alternative to the other idea posted. 

```

 find /home/mymusic -type d -print0 | xargs -0 rmdir --ignore-fail-on-non-empty --parents

```

1. find = extremely powerful utility for searching all manner of items on your PC.

2. /home/mymusic = argument specifying starting directory for search; change it for your situation

3. - type d = option specifying that it should look for directories only

4. -print0 = when combined with xargs' option '-0', the command will properly handle unusual file names

5. | = pipe output

6. xargs = from the man page: "build and execute command lines from standard input"; this takes the output from the 'find' command in this case and passes it to 'rmdir'

7. -0 = handles unusual file names (see Item 4 above)

8. rmdir = removes empty directories

9. --ignore-fail-on-non-empty = without this option, rmdir will output messages indicating that  it could not delete a directory when a non-empty directory is encountered (this does not cause rmdir to delete non-empty directories, it just keeps rmdir from notifying you when it can't delete a directory for that reason)

10. --parents = causes rmdir to delete parent directories (as long as they are empty)

I recommend you read over the man pages for find, xargs and rmdir.

Also, before trying this command, create a dummy set of directories within directories placing dummy files inside a few, then run the command with the find starting path set to the topmost directory of these dummy directories. This will give you a good idea of how the command works before unleashing it on your real data.

Have fun.

---

### Post by omrsafetyo on 2007-03-03
That is probably a better solution than the command I posted.

Its also very safe, since it uses the rmdir, and has error checking (ignore delete failure with directories that are not empty).  The rmdir command will fail any time the directory is not empty; so it won't delete anything by accident - and the error checking will prevent this from needing user input.  It will also go less in depth than the one I posted.  I would prefer this script.

---

### Post by fakie_flip on 2007-03-03
here is a safe way to automate deleting of empty folders. the folders won't be deleted. instead, they will automatically be moved to your trash bin, incase there was something important, it wouldn't be deleted.

you can have cron run this automatically. in my example, cron will move the empty folders to the trash bin once every hour. start with this command.

```
crontab -e
```

next you should see this line.

```
# m h  dom mon dow   command
```

add something below it on a new line, so that you have this.

```
# m h  dom mon dow   command
0 * * * * find /home/user/music -type d -empty -exec mv {} ~/.Trash/ \; 
```

replace /home/user/music to the location of your music directory. now type "control + w" to save. hit enter when it asks you about saving the file. next push "control + x" to exit. using my example, at exactly every hour such as 1:00 am, 2:00 am, ... 6:00 pm, 7:00pm etc, all empty folders that are inside your music directory will be moved to the trash bin.

let me know if this helps.

---

### Post by omrsafetyo on 2007-03-03
> **fakie_flip said:**
> here is a safe way to automate deleting of empty folders. the folders won't be deleted. instead, they will automatically be moved to your trash bin, incase there was something important, it wouldn't be deleted.

you can have cron run this automatically. in my example, cron will move the empty folders to the trash bin once every hour. start with this command.

```
crontab -e
```

next you should see this line.

```
# m h  dom mon dow   command
```

add something below it on a new line, so that you have this.

```
# m h  dom mon dow   command
0 * * * * find /home/user/musicfind -type d -empty -exec mv {} ~/.Trash/ \; 
```

replace /home/user/music to the location of your music directory. now type "control + w" to save. hit enter when it asks you about saving the file. next push "control + x" to exit. using my example, at exactly every hour such as 1:00 am, 2:00 am, ... 6:00 pm, 7:00pm etc, all empty folders that are inside your music directory will be moved to the trash bin.

let me know if this helps.

fixed:
```
# m h  dom mon dow   command
0 * * * * find /home/user/music find -type d -empty -exec mv {} ~/.Trash/ \; 
```

---

### Post by Darko Beta on 2007-03-04
Thanks very much for these suggestions.  I will tinker with these today and, as recommended, learn how they work.

---

### Post by Darko Beta on 2007-03-04
susuntu:  Very cool solution, and thanks for taking the time to explain the commands that are being executed.  This illustrates to me just how powerful the command line can be--I'm just learning how to use it efficiently.

One unforeseen problem: The music programs I've used just delete the music files, and there are a fair amount of folders with the cover art jpg still sitting in there!  These were not deleted, of course.  

If anyone is interested in building onto the previous command to delete any directory which 
1. contains a jpg
2. does *not* contain any mp3s

I would be interested to see how that works (if it's possible).  I'm afraid I don't have the skill to figure this out yet.  And I am fascinated with how this is working so far-at this point I could clean out the remaining folders manually in nautilus in about 15 minutes.  I just want to make it clear that I'm not begging for help to fix my collection--I'm more interested in how one would do this at the command line.

---

### Post by omrsafetyo on 2007-03-04
Just off the top of my head, without testing it...

```
cd /home/mymusic
NUMFILES=`ls -Fld * | grep "^d" | wc -l`
ls -Fld * | grep "^d" | awk '{print $9}' > dirlist.txt

for ((i = 1; i < $NUMFILES; i++))
do
DIRNAME= head -i dirlist.txt | tail -1
MP3SEARCH=`ls -l DIRNAME | grep \.mp3`

if ($MP3SEARCH != "")
then
  rm -r $DIRNAME
fi

done
rm dirlist.txt

```

First, I cd to the directory that you store your music in.

Next, I do a count of directories by piping an ls command which filters using -F - puts a slash in front of a directory name, -d which shows directories, but not the files in them, and -l which shows the long format, which allows us to determine if it is a directory or not.  I grep that output for ^d to extract only the names of directories, and then grep that output to wc -l to count the lines - which gives me the number of directories in the parent.

Next, I use the same line, minus the word count, adding an awk statement, which outputs the 9th ($9) column only and output to a file "dirlist.txt", which will contain a list of directory names.

Next, I do a for loop to cycle through the number of directories, 1 at a time.
I use head to output the first i files in dirlist.txt, which will put the current directory to search at the end of the output, and pipe that to tail -1, which just outputs the last line - giving me just the name of the directory that I currently want to search.

I do an ls on each directory name, giving me the output of the files in that directory, which I search for ".mp3".  If there are no results, I assume this directory should be deleted - so I delete it, and go to the next directory (increment i by 1, which gives me the enxt dir in the list).

Last, I delete dirname.txt and we are done!

I really am not sure if this will work perfect - may want to get a second set of eyes on it.  Good luck.

P.S. - this would need to be saved as a text file, and then chmod 755, so you can execute it.

---

### Post by omrsafetyo on 2007-03-04
Oh.. mind you,

DO NOT RUN THAT SCRIPT anywhere except in a folder that has folders containing music.  If it encounters a folder that has ANY files of ANY type - but has no MP3s, it will delete the folder.

Also note that, it does not check to see if, say you had your artist folders subdivided into album folders.  If there are nested directories, and the parent directory doesn't have an mp3 - gone.  So be very carefuly where you use this.  It may not be exactly what you are looking for.

The script does cd to a specified folder (which you would have to modify) - but if that folder isn't found, it would probably start deleting your working directory.  :)

So best bet would be to move it to the folder that you want to run it from before running a chmod 755

---

### Post by fakie_flip on 2007-03-05
> **omrsafetyo said:**
> Just off the top of my head, without testing it...

```
cd /home/mymusic
NUMFILES=`ls -Fld * | grep "^d" | wc -l`
ls -Fld * | grep "^d" | awk '{print $9}' > dirlist.txt

for ((i = 1; i < $NUMFILES; i++))
do
DIRNAME= head -i dirlist.txt | tail -1
MP3SEARCH=`ls -l DIRNAME | grep \.mp3`

if ($MP3SEARCH != "")
then
  rm -r $DIRNAME
fi

done
rm dirlist.txt

```

First, I cd to the directory that you store your music in.

Next, I do a count of directories by piping an ls command which filters using -F - puts a slash in front of a directory name, -d which shows directories, but not the files in them, and -l which shows the long format, which allows us to determine if it is a directory or not.  I grep that output for ^d to extract only the names of directories, and then grep that output to wc -l to count the lines - which gives me the number of directories in the parent.

Next, I use the same line, minus the word count, adding an awk statement, which outputs the 9th ($9) column only and output to a file "dirlist.txt", which will contain a list of directory names.

Next, I do a for loop to cycle through the number of directories, 1 at a time.
I use head to output the first i files in dirlist.txt, which will put the current directory to search at the end of the output, and pipe that to tail -1, which just outputs the last line - giving me just the name of the directory that I currently want to search.

I do an ls on each directory name, giving me the output of the files in that directory, which I search for ".mp3".  If there are no results, I assume this directory should be deleted - so I delete it, and go to the next directory (increment i by 1, which gives me the enxt dir in the list).

Last, I delete dirname.txt and we are done!

I really am not sure if this will work perfect - may want to get a second set of eyes on it.  Good luck.

P.S. - this would need to be saved as a text file, and then chmod 755, so you can execute it.

rmdir is safer to use than rm -r because it wont delete folders that are non empty.

---

### Post by fakie_flip on 2007-03-05
> **Darko Beta said:**
> Does anybody know of a good app for deleting empty folders?  I have what I assume is a common problem: I have managed my music through various music programs that will delete files--but the artist and album folders are left there forever.  Google found me programs for Windows but I can't find a good Linux app.

Have you tried any of the suggestions yet? Did anything work or not work? You can run this and it will ask you before deleting to answer yes or no because of the -i option so that nothing important is automatically deleted.

```
find /path/to/music -depth -empty -type d -exec rm -irv {} \;
```

---

### Post by SuSUntu on 2007-03-05
**WARNING - The following contains code that deletes items from your computer. Understand what it does before using it. I also cannot be held responsible for its use or misuse.**

Here's my take on a solution to Darko Beta's problem. What follows is a "test" script and the test results from running the code. The code is deemed "test" for a number of reasons, but primarily because there are a lot of (uncommented) echo commands that output to the terminal. The echos are solely for debugging and reporting. A copy of the code with the echo statements removed will be posted shortly.

The testing was done by creating a hierarchy of folders containing a mix of *mpc, *ogg, *jpg and a couple plain text files. The purpose of the testing was to ensure that only the targeted files were deleted.

Please read the comments in the script for an explanation of the code and the the deletion criteria.

Also, you will note that the solution is broken down into two main parts:

1. Deleting stray JPGs (new code)
2. Deleting empty directories (using my original code posted previously for that purpose)

The two tasks can be run independently of each other, and they can be separated into two separate scripts if desired. In order to be most effective, however, the order of execution should be as shown in Item 1 and Item 2 above. 

```

#!/bin/bash
##----------------
##Script Name: 
##Description of Script:
##Date:
#-----------------

# USER SETTINGS ================================================================

# ****** Set Starting Directory - USER NEEDS TO SET THIS VARIABLE
startdir='/home/001/Desktop//test'

# ****** Set Maximum Number of JPGs to Delete - USER NEEDS TO SET THIS VARIABLE
# This allows for deletion of more than one JPG (front cover, back cover, liner notes, etc.)
# while maintaining a margin of safety (i.e., the script can't accidentally delete hundreds of image files
# in a single folder at a time). If you know you only will have one JPG file in a directory, set value to 1. 
# For testing , this was set to 2 to test that the dummy folder with three JPGs + no music files would not be deleted.
maxjpgs=2

# END USER SETTINGS ============================================================

# Change Current Directory To Start Directory
cd $startdir

# Find files of type 'Directory' | and read dirs / subdirs until no more are in the stack
find -type d | while read dir; do

## Following Line Is For Testing ---------
echo "Relative Path From Find Output:" $dir
##---------------------------------------

# Sets variable to dir.
# The pipe to 'cut' is required to remove the leading './' from the relative path.
# In other words, the original output from find  = './path', but we need 'path'.
dircut=$(echo $dir | cut -c3-)

## Following Line Is For Testing ---------
echo "Relative Path After Output Piped To 'cut -c3-':" $dircut
##---------------------------------------

# Concatenate variables to create full paths (i.e., relative path '$dir' added
# to '$startdir' yields full path)
fulldir=$startdir/$dircut

## Following Line Is For Testing ---------
echo "Current Path:" $fulldir
##---------------------------------------

# Set variable to the total number of files in a directory. 'wc - l' counts the number of lines
# output by the 'ls' command (one line per file). The 'grep' command looks for '-' at the beginning
# of each line of the 'ls' output which indicates a regular file (thus excluding folders which are indicated by a 'd').
numfiles=$(ls -l "$fulldir" | grep "^-" | wc -l)

# Set variable to the total number of JPG files in a directory. 'wc - l' counts the number of lines
# output by the 'ls' command (one line per file). The 'grep' command looks for 'jpg' at the end
# of each line of the 'ls' output.
jpgfiles=$(ls -l "$fulldir" | grep ".jpg$" | wc -l)

## Following Two Lines Are For Testing --
echo "Total No. Files In Directory:" $numfiles
echo "Total No. JPGs In Directory:" $jpgfiles
##---------------------------------------

# *** DELETION TEST CRITERIA ***
# Test to see if total number of files in a folder (all types) = total JPG files in a folder. If true, 
# this means that only JPGs are in the directory.
# AND
# Test whether the number of JPGs is not equal to 0. Test is necessary to avoid running any operations on 
# empty directories (concern is valid only when first test is also true)
# AND
# Test that number of JPGs is less than or equal to the maximum number set in USER-SET variable 'maxjpgs'.
# Essentially, this test logic prevents us from having to know what types of files other than JPGs
# are in the directory (e.g., mp3, ogg, mpc, FLAC, mpeg, avi, etc.), and provides safeguards against deleting
# files if run in the wrong starting directory. More specifically, no files other than JPGs will be deleted
# and only the set maximum number of JPGs (variable 'maxjpgs') will be deleted per directory.
if [ "$numfiles" = "$jpgfiles" ] && [ "$jpgfiles" != "0" ] && [ $jpgfiles -le $maxjpgs ] ; then

## Following Two Lines Are For Testing --
echo "File(s) to be deleted:"
ls "$fulldir" | grep jpg
##--------------------------------------

# Set file mask to JPG wildcard - if your image files are other than JPGs, you can change the mask, e.g., *.png
filemask=*.jpg

# Following Line Is For Testing --
fulldirplusfile=$fulldir$plusfile
echo "Full Path Plus JPG File Mask:" $fulldirplusfile
#---------------------------------------

# *** TO BE UNCOMMENTED WHEN THROUGH TESTING - THIS IS THE CODE THAT ACTUALLY DELETES FILES ***

#find "$fulldir" -maxdepth 1 -type f -print0 | xargs -0 rm -f $filemask

#----------------------------------------------------------------------------------------

# Close IF THEN statement
fi

## Following Line Is For Testing --
echo "========================="
##---------------------------------------

# End of WHILE loop
done

#*** TO BE UNCOMMNENTED AFTER TESTING -------
#*** After deleting the stray JPGs, the oiginal line of code to delete empty directories is run

#find "$startdir" -type d -print0 | xargs -0 rmdir --ignore-fail-on-non-empty --parents

# Exit Script
exit


```


Below is a the output of the 'tree' command prior to running the script live. Note there are 14 files, with the items targeted for deletion highlighted. Also note that although the folder with 3 JPGs does not have any other file types inside it, the JPGs were not targeted for deletion because the variable 'maxjpgs' was set to 2, thus excluding any folder with more than 2 JPGs from being targeted. Please see the script's comments for more information. 

```

user@Computer:~/Desktop/test$ tree
.
|-- 3 Doors Down-The Better Life-Be Like That.mpc
|-- Al Stewart-Year Of The Cat-Lord Grenville.mpc
|-- new file
|-- new file 1
`-- untitled folder
    |-- Joe Strummer & The Mescaleros-Global A Go-Go-Johnny Appleseed.ogg
    |-- cover.jpg
    `-- untitled folder
        |-- Art Tatum-The Tatum Group Masterpieces-All The Things You Are.mpc
        |-- cover.jpg
        `-- untitled folder
            **|-- cover.jpg**
            `-- untitled folder
                |-- cover.jpg
                |-- cover1.jpg
                |-- cover2.jpg
                `-- untitled folder
                    **|-- cover.jpg**
                    **|-- cover1.jpg**
                    `-- untitled folder

**6 directories, 14 files**

```

Below is the output from the test script. The test output related to the targeted files is highlighted.

```

Relative Path From Find Output: .
Relative Path After Output Piped To 'cut -c3-':
Current Path: /home/001/Desktop/test/
Total No. Files In Directory: 4
Total No. JPGs In Directory: 0
=========================
Relative Path From Find Output: ./untitled folder
Relative Path After Output Piped To 'cut -c3-': untitled folder
Current Path: /home/001/Desktop/test/untitled folder
Total No. Files In Directory: 2
Total No. JPGs In Directory: 1
=========================
Relative Path From Find Output: ./untitled folder/untitled folder
Relative Path After Output Piped To 'cut -c3-': untitled folder/untitled folder
Current Path: /home/001/Desktop/test/untitled folder/untitled folder
Total No. Files In Directory: 2
Total No. JPGs In Directory: 1
=========================
[b]Relative Path From Find Output: ./untitled folder/untitled folder/untitled folder
Relative Path After Output Piped To 'cut -c3-': untitled folder/untitled folder/untitled folder
Current Path: /home/001/Desktop/test/untitled folder/untitled folder/untitled folder
Total No. Files In Directory: 1
Total No. JPGs In Directory: 1
File(s) to be deleted:
cover.jpg
Full Path Plus JPG File Mask: /home/001/Desktop/test/untitled folder/untitled folder/untitled folder/*.jpg[/b]
=========================
Relative Path From Find Output: ./untitled folder/untitled folder/untitled folder/untitled folder
Relative Path After Output Piped To 'cut -c3-': untitled folder/untitled folder/untitled folder/untitled folder
Current Path: /home/001/Desktop/test/untitled folder/untitled folder/untitled folder/untitled folder
Total No. Files In Directory: 3
Total No. JPGs In Directory: 3
=========================
[b]Relative Path From Find Output: ./untitled folder/untitled folder/untitled folder/untitled folder/untitled folder
Relative Path After Output Piped To 'cut -c3-': untitled folder/untitled folder/untitled folder/untitled folder/untitled folder
Current Path: /home/001/Desktop/test/untitled folder/untitled folder/untitled folder/untitled folder/untitled folder
Total No. Files In Directory: 2
Total No. JPGs In Directory: 2
File(s) to be deleted:
cover1.jpg
cover.jpg
Full Path Plus JPG File Mask: /home/001/Desktop/test/untitled folder/untitled folder/untitled folder/untitled folder/untitled folder/*.jpg[/b]
=========================
Relative Path From Find Output: ./untitled folder/untitled folder/untitled folder/untitled folder/untitled folder/untitled folder
Relative Path After Output Piped To 'cut -c3-': untitled folder/untitled folder/untitled folder/untitled folder/untitled folder/untitled folder
Current Path: /home/001/Desktop/test/untitled folder/untitled folder/untitled folder/untitled folder/untitled folder/untitled folder
Total No. Files In Directory: 0
Total No. JPGs In Directory: 0
=========================


```


Below is the output of the 'tree' command after running the 'live' script. Note that the aforementioned targeted files have been deleted while leaving the other files and directories intact. Also note that of the original 14 files, 11 are left (as desired).

```

user@Computer:~/Desktop/test$ tree
.
|-- 3 Doors Down-The Better Life-Be Like That.mpc
|-- Al Stewart-Year Of The Cat-Lord Grenville.mpc
|-- new file
|-- new file 1
`-- untitled folder
    |-- Joe Strummer & The Mescaleros-Global A Go-Go-Johnny Appleseed.ogg
    |-- cover.jpg
    `-- untitled folder
        |-- Art Tatum-The Tatum Group Masterpieces-All The Things You Are.mpc
        |-- cover.jpg
        `-- untitled folder
            `-- untitled folder
                |-- cover.jpg
                |-- cover1.jpg
                |-- cover2.jpg
                `-- untitled folder
                    `-- untitled folder

**6 directories, 11 files**

```

---

### Post by SuSUntu on 2007-03-05
**WARNING - The following contains code that deletes items from your computer. Understand what it does before using it. I also cannot be held responsible for its use or misuse.**

Here's the script with most of the explanatory comments deleted. Also, and most importantly, the original code that removes empty directories has been uncommented and is active. 

```

#!/bin/bash
##----------------
##Script Name: 
##Description of Script:
##Date:
#-----------------

## USER-SET VARIABLES -----------

# ****** startdir - Set Starting Directory

startdir='/home/001/Desktop/test'

# ****** maxjpgs - Set Maximum Number of JPGs to Delete - USER NEEDS TO SET THIS VARIABLE
# This allows for deletion of more than one JPG (front cover, back cover, liner notes, etc.)
# while maintaining a margin of safety (i.e., the script can't accidentally delete hundreds of image files
# in a single folder at a time). If you know you only will have one JPG file in a directory, set value to 1. 
# For testing , this was set to 2 to test that the dummy folder with three JPGs + no music files would not be targeted.

maxjpgs=2

## END USER_SET VARIABLES -------


cd $startdir

find -type d | while read dir; do
	dircut=$(echo $dir | cut -c3-)
	fulldir=$startdir/$dircut
	numfiles=$(ls -l "$fulldir" | grep "^-" | wc -l)
	jpgfiles=$(ls -l "$fulldir" | grep ".jpg$" | wc -l)

	if [ "$numfiles" = "$jpgfiles" ] && [ "$jpgfiles" != "0" ] && [ "$jpgfiles" -le "$maxjpgs" ] ; then
		filemask=*.jpg
# *** THIS CODE DELETES THE STRAY JPG FILES
		find "$fulldir" -maxdepth 1 -type f -print0 | xargs -0 rm -f $filemask
	fi
done

# *** ORIGINAL CODE THAT DELETES EMPTY DIRECTORIES 
find "$startdir" -type d -print0 | xargs -0 rmdir --ignore-fail-on-non-empty --parents

#---
exit

```

The testing presented in the previous post only reflects results from running the new code which removes JPGs as that was what I was focusing on. However, below is the 'tree' command output after having run the uncommented script (which runs both both the JPG removal code and the empty directory removal code) which is presented immediately above in this post. 

```

user@Computer:~/Desktop/test$ tree
.
|-- 3 Doors Down-The Better Life-Be Like That.mpc
|-- Al Stewart-Year Of The Cat-Lord Grenville.mpc
|-- new file
|-- new file 1
`-- untitled folder
    |-- Joe Strummer & The Mescaleros-Global A Go-Go-Johnny Appleseed.ogg
    |-- cover.jpg
    `-- untitled folder
        |-- Art Tatum-The Tatum Group Masterpieces-All The Things You Are.mpc
        |-- cover.jpg
        `-- untitled folder
            `-- untitled folder
                |-- cover.jpg
                |-- cover1.jpg
                `-- cover2.jpg

**4 directories, 11 files**

```

---

### Post by Darko Beta on 2007-03-05
Wow, this looks awesome susuntu.  I can't wait to spend some time tinkering with it tonight and looking at the code.

---

### Post by omrsafetyo on 2007-03-05
SuSUntu  - that is an amazingly powerful script, with so little code!  And its so simple!

Count files - count jpgs, if the numbers are equal - only jpgs!  If the number is less than max, delete all files.  Later, delete empty directories.  Its genius.

I knew someone would come up with something better than mine - I do very little scripting - I enjoy it, but haven't done enough to come up with something like that.  I did want to do something similar, but couldn't wrap my head around how.    Nice work.

---

### Post by SuSUntu on 2007-03-06
> **Darko Beta said:**
> Wow, this looks awesome susuntu.  I can't wait to spend some time tinkering with it tonight and looking at the code.

Thanks. I'm glad you may find it useful. :)

You definitely have the right attitude about checking the code and understanding it as opposed to just diving in and running it, especially since you don't know me from Adam.

---

### Post by SuSUntu on 2007-03-06
> **omrsafetyo said:**
> SuSUntu  - that is an amazingly powerful script, with so little code!  And its so simple!

Count files - count jpgs, if the numbers are equal - only jpgs!  If the number is less than max, delete all files.  Later, delete empty directories.  Its genius.



That praise is a little strong, but definitely appreciated. Glad you liked it :) 

> **omrsafetyo said:**
> 
I knew someone would come up with something better than mine - I do very little scripting - I enjoy it ... 

To be clear, I'm definitely not a BASH guru. I would have to say that this was the most "complex" BASH script I've ever bothered to write. And I'm definitely not a code-writing guru in general.

I do enjoy the challenge of coming up with the logic and then figuring out how a given language can be used to achieve the goal with minimum code ... sometimes it's pretty and sometimes it's ugly ... but the process is entertaining, nevertheless. And, as this thread testifies, there are a wide variety of ways to achieve the same end.

Thanks again.

---

