---
title: "[SOLVED] Unable to open .txt files"
date: 2008-06-05
forum: General Help
---

### Post by brett123 on 2008-06-05
I have hundreds of .txt files as a legacy from Windows. When I open Places - Documents and double click these files all is good and they open in gedit (happy with that).

The problem is Places - **Search For Files**, in the search results it won't let me double click .txt files - I just get an error "**There is no installed viewer capable of displaying the document**."

If I have files with no extension, then I can open them in the search results (gedit), but not .txt ones.

Can anyone help me please, I desperately need this to function.

Preference of solutions:
1) Keep the files in .txt format but have them open in search results, or
2) What is easy way to remove all .txt extensions and just leave the file names (rather not do this, but it would solve my problem in any case).

Thank you.

---

### Post by Xiong Chiamiov on 2008-06-05
1.  (Not quite sure in gnome, but should be similar) Right-click -> properties, then somewhere you can change which application files of that type open with.  If need be, I can log into Gnome to check.
2.  If you're in a directory with a bunch of .txt's, you should be able to just
```

mv *.txt *

```
Let me check that out before you run it though.

EDIT: Ok, #2 was totally wrong.  Use this instead:
```

rename 's/\.txt//' *.txt

```
Now I'm off to check #1.

EDIT2: Ok, it's right-click -> properties -> open with.

---

### Post by brett123 on 2008-06-05
The right-click open-with stuff is fine, all set to "Text Editor" (which means gedit in my case). The problem is only in Search Results. Sorry, I do not have enough Linux/Ubuntu vocab just yet to explain it better than that.


EDIT: Tried mv *.txt * on a sample directory, and just got:
mv: `Fix.txt' and `Fix.txt' are the same file

---

### Post by Xiong Chiamiov on 2008-06-05
Yes, GNOME likes to call things simply by what they are, rather than by their actual application names (drives me nuts!).

I updated (read: fixed-from-completely-wrong) my suggestions.  I'll take a look at search results.

---

### Post by brett123 on 2008-06-05
Thanks, _rename 's/\.txt//' *.txt_ did work on my test directory.

I won't rename them all yet though - if you can possibly fix #1 I would be eternally grateful :D

---

### Post by Xiong Chiamiov on 2008-06-05
Can you double-click .txt files in nautilus to open them, or do you have to use the open-with menu?  With a default viewer set, I just have to double-click files to open them in search results.

---

### Post by brett123 on 2008-06-05
Not sure what this Nautilus is, but if you just mean the standard open Documents and double click - then yes, that works fine. Double click .txt opens in gedit, and double-clicking no ext also opens in gedit.

It's only Search Results. Can't double click .txt. And even right click the Open option does nothing (except cause that no viewer error).

---

### Post by brett123 on 2008-06-05
I'm not smart enough to know what all this means, but it looks like someone else has just found a similar thing:
[https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/236829](https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/236829)

---

### Post by Xiong Chiamiov on 2008-06-05
Ah, yes, Nautilus is the default file manager for Gnome.  As I said, they don't like to give things names...

That is rather odd.  It works just fine for me, on a pretty much untouched Gnome install.  I'm curious if it has to do with encoding...
Try creating a new text file like so
```

touch blah.txt

```
then searching for said text file, and see if the result's the same.
Tangent: when I did this, I got *way* too many results for "blah"...

---

### Post by Xiong Chiamiov on 2008-06-05
> **brett123 said:**
> I'm not smart enough to know what all this means, but it looks like someone else has just found a similar thing:
[https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/236829](https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/236829)
Hmm, interesting.  However, no one in any of the 3 bug reports seems to have a solution, which is a shame.  Well, actually:
> 
Replacing
gnome_vfs_mime_get_default_application with g_app_info_get_default_for_type
(and g_app_info_launch_uris below) actually solves the problem

but I'm more lost than he is
> 
but that
requires deeper hacking, because things like launch-contexts, etc. are still
unclear to me.


---

### Post by brett123 on 2008-06-05
> **Xiong Chiamiov said:**
> It works just fine for me, on a pretty much untouched Gnome install.  I'm curious if it has to do with encoding...
Try creating a new text file like so
```

touch blah.txt

```
then searching for said text file, and see if the result's the same.
Tangent: when I did this, I got *way* too many results for "blah"...

Brilliant!! It works! 

Ok, now my next question - hahahahha.... ahhhh, any idea how to fix this encoding with all these ex-Windows files (I really do need them)? Maybe I should just remove the .txt extension and be done with it!?!??!

I've made the permanent switch to Ubuntu today (goodbye Bill), but am just not quite prepared to bite the bullet and remove all these extensions in case I need to go back some day.

---

### Post by Xiong Chiamiov on 2008-06-05
Well, first make sure that if you rename one of those files to have no extension, that you can double-click it to open it in the search results.  If not, then removing the extension won't do anything.

I'll have to think for a moment about switching encoding.  I think it would involve opening and resaving all of them using some sort of batch process, but I'm not quite sure how to specify encoding with a command switch.

---

### Post by brett123 on 2008-06-05
This might help???

tr -d '\015' < old.txt > new.txt

It DOES work, removes the new line character apparently (I vaguely have an idea what I'm talking about). I tried it and it works (now opens in Search Results).

However, I do not know how to batch process these. Would need to issue one command for hundreds of files. Also, that command above requires an old and a new file to write to - ie it cannot overwrite the existing file (you end up with blanks).


EDIT: Unashamedly stole that code from [http://linuxreviews.org/quicktips/txt_doc2unix/](http://linuxreviews.org/quicktips/txt_doc2unix/)

---

### Post by Xiong Chiamiov on 2008-06-05
I think I can hack something up, but could you please attach one of those files, so that I have something to test on?

---

### Post by brett123 on 2008-06-05
Will do, thanks. But, just found one strange thing regarding this, still investigating.... will attach up a file in a minute.

---

### Post by Xiong Chiamiov on 2008-06-05
Ok, I believe this will work.  Create a new text file in the directory (test directory, of course!):
```

gedit temp

```
and enter this code:
```

#!/bin/bash

for i in $(ls *.txt)
do
  echo $i
  tr -d '\015' < $i > tempFile
  mv tempFile $i
done

exit 0

```
You can take the echo line out; I just had it in there so I could make sure my for loop was correct.
Save, then give it executable permissions, then run:
```

chmod +x temp
./temp

```

EDIT: For an explanation:
"ls *.txt" will show a listing of all the files that end with .txt in the directory.
The for loop assign the variable "i" the value of the first .txt file, then runs that command, outputting it to a txt file named tempFile.  It then moves tempFile back to the original name and continues on for each .txt file.

---

### Post by brett123 on 2008-06-05
Problem solved!!! Linux is a funny animal me thinks....

The problem ONLY occurs if the first 2 characters in a file (ANY file, not just .txt and not just Windows files, also happens with native Ubuntu files) are hyphens!!! Believe it or not.

Just create a blank file and enter -- or more --- etc, then find it in search, and you won't be able to open it. Search thinks it is a VHDL Document (whatever that is).


Many of my ex-Windows files start with a line of ------------- like in a header of sorts:

------------------------
  TAX RETURN
------------------------

It is these now I realise I have issues with. Easy to fix.

So sorry to waste your time, but I did learn alot about many things from you tonight. Thank you again.

---

### Post by brett123 on 2008-06-05
Cheers for the code above too, am going to keep that. I think it will come in handy some time. I do understand all that code, did learn Linux many moons ago in university, it's slowly coming back the more and more code I look it.

---

### Post by Xiong Chiamiov on 2008-06-05
Oh God, VHDL.  I just finished my last lab for my Digital Design class tonight (thankfully my major's software-oriented), and hopefully I'll never have to deal with VHDL again.  Essentially, it's a programming language for creating circuits, rather than putting together the gates by hand.  The Electrical Engineers think it's really nifty, but when you're learning Python at the same time... let's just say it's not the most elegant language.  And yes, VHDL comments start with --.

My time was not wasted, as it posed an interesting problem for me, and helped keep me up on my very basic bash scripting knowledge.  I'm glad to have helped at all, and that you figured out what the problem was.  Cheers, and have a good night! (or morning, or whatever time of day it is for you)

---

