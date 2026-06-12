---
title: "Help with file deletion"
date: 2007-08-21
forum: General Help
---

### Post by MeneM on 2007-08-21
Oh dear... This should be simple ;-)

I'm trying to delete a very large list of files. All the filenames are inside a textfile "input.txt" but I can't seem to see how to "feed" or "pipe" the filenames to rm.

Tried things like: ```
cat ./input.txt | rm -f
```
and: ```
rm -f < ./input.txt
```

Could anyone help me?

Thanks!

---

### Post by jamvegan on 2007-08-21
How about command substitution?
```
rm -f `cat input.txt`
```

---

### Post by raevin on 2007-08-21
> **MeneM said:**
> Oh dear... This should be simple ;-)

I'm trying to delete a very large list of files. All the filenames are inside a textfile "input.txt" but I can't seem to see how to "feed" or "pipe" the filenames to rm.

Tried things like: ```
cat ./input.txt | rm -f
```
and: ```
rm -f < ./input.txt
```

Could anyone help me?

Thanks!

If you're currently in the directory where input.txt is, don't do "./input.txt", just "input.txt"...and if you're not, then "[path to file]/input.txt".  "./" in front of any file tells Linux to execute the file (and unless input.txt has executable-permissions, won't execute).

If you want to pipe the information to input.txt, then do "> input.txt"...want to pipe information to the console, type do "< input.txt" (assuming you are currently in the directory where input.txt is located.)

If I'm wrong, then someone else should be able to help you...but, this is how I've always done it.

---

### Post by MeneM on 2007-08-21
Thank you very much for these suggestions. I've tried them as you can see here:
```

mark@isp:/home/www/web1/webdav$ rm -f < delete.input
mark@isp:/home/www/web1/webdav$ rm -f 'cat delete.input'
mark@isp:/home/www/web1/webdav$
```

As you can see, nothing happened... Darn it! Darn Ubuntu! Darn all!!!! 

Ahum

Back to the man pages it is.

---

### Post by jamvegan on 2007-08-21
Actually, for command substitution you need to use backticks (`), not apostrophes (').  The backtick key is generally next to the 1 at the top of the keyboard.  Also, if it works, you won't see anything to indicate that.  You'll just have to check to see that the files are gone for confirmation.

---

### Post by raevin on 2007-08-21
> **jamvegan said:**
> Actually, for command substitution you need to use backticks (`), not apostrophes (').  The backtick key is generally next to the 1 at the top of the keyboard.  Also, if it works, you won't see anything to indicate that.  You'll just have to check to see that the files are gone for confirmation.

Actually, if you append "&" at the end of the command won't it send output to the console?

---

### Post by jamvegan on 2007-08-21
> **raevin said:**
> Actually, if you append "&" at the end of the command won't it send output to the console?

The & at the end of a command tells the shell to run the command in the background.  What this means is that you'll immediately get your command prompt back, and can run more commands, even if the first command is still running.

The shell will produce some output as a result.  First it will output the job number and process id, and then it will indicate when the command has finished running.  Unfortunately, it will not tell you if it did what you *wanted* it to do. :(

---

### Post by bodhi.zazen on 2007-08-21
in linux if the command completes without errors it was successful 

so, mission accomplished, no ?

---

### Post by jamvegan on 2007-08-21
> **bodhi.zazen said:**
> in linux if the command completes without errors it was successful 

so, mission accomplished, no ?

Well, usually.  But some commands fail silently (or at least don't do what you want, silently).  For instance, MeneM's:
```
mark@isp:/home/www/web1/webdav$ rm -f 'cat delete.input'
```
does absolutely nothing, and doesn't complain about it.

---

### Post by tekkenlord on 2007-08-21
What you need to do is the following

cat input.txt |while read line; do rm -r "${line}"; done

This will read the lines one by one and delete the respective files. Hope it helps.

---

### Post by astralsin on 2007-08-21
do this

```
cat input.txt | xargs rm -rf
```

---

### Post by MeneM on 2007-08-22
> **tekkenlord said:**
> What you need to do is the following

cat input.txt |while read line; do rm -r "${line}"; done

This will read the lines one by one and delete the respective files. Hope it helps.


Cool! That one worked!

Trying out this one now:

> astralsin Re: Help with file deletion

do this


Code:
cat input.txt | xargs rm -rf 

Perhaps I should also explain what I'm trying to accomplish.

I used fdupes to create a list of files that are duplicates of one and another. This file is 8Mb big, so quite the file I would say...

But if I feed this file to rm, eveything would be deleted including any original file. So I needed to delete 1 entry in every double. For instance fdupes would return this in a file if they are identical:

```

./photo0001.jpg
./temp/photo0001.jpg

./photo0002.jpg
./temp/holiday.jpg

./photo0003.jpg
./temp/renamed_but_still_the_same_photo.jpg
./holiday/yet_another_place_where_i_forgot_i_placed_photos.jpg
```

So you see, feeding this file would delete everything. I needed to delete the empty lines and then one extra line, so only one version of each file would remain on the hard drive.

I should write a python program to do this with. Could be a cool project for a beginner...

Later,
Mark

---

### Post by tekkenlord on 2007-08-22
SInce every block of the same photo , for example
./photo0001.jpg
./temp/photo0001.jpg

is seperated from the next one with an empty line, then it shouldn't be too hard to write a small program that reads every line of the file and deletes every first line from the beggining of each block. This way, you will end up with a file which contains every file you want to delete and then you can use the command I told you earlier.

---

### Post by tekkenlord on 2007-08-22
Keep also in mind that if you give fdups with the -d option (fdups -d <some directory>) it will then prompt you to choose which file you want to delete. However, this is not useful when you have many duplicated files...

---

### Post by MeneM on 2007-08-22
> **tekkenlord said:**
> 
is seperated from the next one with an empty line, then it shouldn't be too hard to write a small program that reads every line of the file and deletes every first line from the beggining of each block. This way, you will end up with a file which contains every file you want to delete and then you can use the command I told you earlier.

Yeah that's what I wqas thinking. Some sort of regex to search for an empty line, then delete it and the next one.

That will be what I will attempt to write in Python code. When done I'll post it here.

---

### Post by brett611 on 2008-01-01
Please do post your solution/python code as I have the exact same issue with fdupes.  I'm so close but yet so far!

thx

---

### Post by brett611 on 2008-01-01
Just found this thread re: fslint.  the author of fslint suggested some additional cl code to handle these dupe/delete issues.  I'm going in for a dip...will let you know how the water is...

[http://ubuntuforums.org/showthread.php?t=272292&highlight=fdupes](http://ubuntuforums.org/showthread.php?t=272292&highlight=fdupes)

"Hi I'm the Author of FSlint.
The GUI is a wrapper around a core command line utilities.
On a standard install you can add these utils to the path with:

export PATH="$PATH":/usr/share/fslint/fslint

Then you can use the utilities like:

findup /folder #list duplicates
findup -m /folder #merge duplicates using hardlinks
findup -d /folder #delete all but first duplicate
findup -dt /folder #report what would be deleted

fslint /folder #run all tools on a folder"

---

### Post by MeneM on 2008-01-02
Hi There!

Thanks for the added info, personally I ended up with using a completely different route: [http://lifehacker.com/software/featured-download/delete-duplicate-files-with-the-dupinator-293473.php](http://lifehacker.com/software/featured-download/delete-duplicate-files-with-the-dupinator-293473.php)

Hope that also helps.

Thanks,
Mark

---

