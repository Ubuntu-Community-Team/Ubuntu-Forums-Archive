---
title: "sync folder regardless of file extension"
date: 2018-01-14
forum: General Help
---

### Post by duruttye on 2018-01-14
Hello everyone!

I'm trying to find out how I could sync folders regardless of their extension, basing the sync only on the files names.

The reason I'm trying to do this is because I take a lot of pictures both in .jpg and .nef (raw) format. I copy them all on my laptop and since the .jpg files are much smaller, I look through them and delete a bunch. Since I have the same files in .nef format it is pretty painful to go through the other folder and delete them as well.

Does anyone know any easy solution for this?

I'm using standard Ubuntu 17.10 on a Sony Vaio laptop.

Thank you very much for your help.

---

### Post by TheFu on 2018-01-14
rsync
grsync
cp
tar
or any backup program.

Perhaps I don't understand the question?

---

### Post by duruttye on 2018-01-14
Hi TheFu,

Will they be able to sync the folders even if one of them has filename1.jpg and the other one has filename1.nef in them.

Or maybe I wasn't specific enough.
When I delete filename1.jpg in folder 1, I want filename1.nef to be deleted in folder 2, as well.

---

### Post by TheFu on 2018-01-14
rsync has plenty of options around removing stuff.

man rsync says:
```
            --delete                delete extraneous files from dest dirs
            --delete-before         receiver deletes before xfer, not during
            --delete-during         receiver deletes during the transfer
            --delete-delay          find deletions during, delete after
            --delete-after          receiver deletes after transfer, not during
            --delete-excluded       also delete excluded files from dest dirs

```
Extensions don't matter, unless you go out of your way to make them matter.  Extensions really are an MS-DOS and human readability thing. Linux doesn't care. The filename is the filename.

---

### Post by Holger_Gehrke on 2018-01-14
@TheFu :
I think you did misunderstand ...

@duruttye:
Let me first state how I understand the situation and then give my solution ...

Situation:
You have two directories, one with .jpg files and one with raw images. You browse through the jpegs and delete the ones you don't want and now you want to delete the raw files, too. The files have the same names and only differ in the extension (.jpg/.nef).

Solution:
Assuming the jpegs are in ~/jpegdir and the nef-files are in ~/nefdir open a terminal and do this:
```

cd ~/nefdir
for i in *.nef; do test -f ~/jpgdir/"${i%%.nef}.jpg"||rm "$i";done

```
Explanation: this goes through the .nef-files and checks whether there is a jpeg with the same name. If there isn't, it deletes the nef-file.

Holger

---

### Post by dragonfly41 on 2018-01-14
Suggestion. You could add this as a custom action in Thunar so that the process is synced.
Here are examples of custom actions.

[http://duncanlock.net/blog/2013/06/28/useful-thunar-custom-actions/](http://duncanlock.net/blog/2013/06/28/useful-thunar-custom-actions/)

The only problem I find is trying to select multiple files in Thunar.
Selecting a file then using Ctrl to select next file seems to popup a terminal window.

---

### Post by TheFu on 2018-01-14
Yep, I definitely was WAY OFF on understanding. Sorry.

If a script was used used to delete the jpg, then that same script could delete the .nef files from another location at the same time.  Of course, there are 50 other methods.

---

### Post by duruttye on 2018-01-14
Hi All,

Thank you for the replies.

@TheFu, maybe I wasn't clear enough, sorry :). I'm not using a scrip to delete the jpg files, I'm deleting them myself. I just want the .nef files deleted as well.

@dragonfly41 that looks way too complicated to me, I like the terminal better, but thank you anyway.

@Holger_Gehrke, I tried your approach and it is like something I was looking for. Although it doesn't work. I'm inside the /nefdir, file extensions are with capitals, changed that, too, still it just hangs with a > after the command. I'm not really sure how that command should work, but is there any way to test it step by step? Like an excel formula for example?

---

### Post by duruttye on 2018-01-14
How about something like:

$ rsync -avz --delete /jpgdir/DSC*.* /nefdir/DSC*.*

---

### Post by HermanAB on 2018-01-14
Further, with a deduplication utility, you can convert identical photo files with the same or different names scattered over your disk into hard links and recover the space.

See fslint (the one I happen to use), duff, fdupes, rdfind, hardlink etc.

With deduplication, you can quickly recover gigabytes of space.

---

### Post by Holger_Gehrke on 2018-01-14
If the shell just sits there with the secondary prompt (">"), it means you've left out one of the double quotes I put around the variable names to cope with spaces in file names. You can abort this broken command by hitting ctrl-c. You can paste into most terminal programs using ctrl-shift-v (as opposed to ctrl-v, which means something different in the shell), so if you copy the line from your browser and paste it into the shell it should work (I just copied it to my terminal, changed the extensions used to doc and odt and the rm to echo and got a list of the doc-files for which I have no odt ... so it works as advertised). If you want to test it out and see what it would delete, you can replace the 'rm' in the second line with 'echo'.

Holger

---

### Post by TheFu on 2018-01-14
Sorry folks - I was way off on the initial reply.  OP seems to have 2 directories.
a) contains both .jpg and .nef files.
b) contains copied over .jpg files.
She/he uses "b" to delete files that aren't desired, but wants files in "a" to be removed as well based on the filename-basename (ignoring extensions).

The OP doesn't want to use a script to delete the files in both "a" and "b" at the same time.  I'm unsure what  *"I'm deleting them myself"* means. 

Or I could be completely wrong, again. ;(

---

### Post by duruttye on 2018-01-14
@Holger_Gehrke  

It worked, I did leave out a quote, jeez.

Thank you very much!!

---

### Post by duruttye on 2018-01-14
@TheFu

To make it even more clear, if someone else will be looking at this:

My camera makes two sets of files for each picture I take. One is a JPG and the other on is a NEF-raw file. When I copy them to my laptop I use two folder, one for the jpg and the other one for the nef. So I have two folders with the same file names but different extensions. When I look through the pictures, I delete some (most) from the JPGs, because they are easier to open and quickly browsed through. Because sometimes I have a few hundreds of pictures it was a hassle to go through the folder with the NEF files and delete the ones I saw and deleted from the JPG folder. 

I'm sure there are more people doing the same as me, or at least something similar.

I will save this post, cause I will use this for a long time from now on.

Thank you all, again!

---

