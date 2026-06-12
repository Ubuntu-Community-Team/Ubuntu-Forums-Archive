---
title: "Add a new line at the end of txt files"
date: 2022-09-15
forum: General Help
---

### Post by enricomar on 2022-09-15
Hi everyone! I have a bunch of txt files and some of them, on R, give me an "incomplete final line found" error. So I would like to add a line to all .txt files contained in a folder. Tips? Thank you!

---

### Post by grahammechanical on 2022-09-15
what is R? Is it the R Project?

[https://www.r-project.org/](https://www.r-project.org/)

Is that not the best place to seek help on using R? I can only guess that those text files with the issue are lacking an eof (end of file) marker. 

This might help

[https://stackoverflow.com/questions/12399978/eof-missing-for-unix-file](https://stackoverflow.com/questions/12399978/eof-missing-for-unix-file)

In Linux and Unix the end of file character is produced by Ctrl+D according to an internet search. In the past when using certain text editors (non-GUI) special characters had to be entered to produce new lines and to indicate the end of a file. Text editors on a graphical user interface insert these characters for the writer. 

Regards

---

### Post by enricomar on 2022-09-15
no, the problem was not of R, the problem was within the conversion mechanism in txt, Linux, and this is the patch solution
echo " " | tee -a * .txt

---

### Post by MAFoElffen on 2022-09-15
You still have us in the dark, because we have no idea what "R" is and you have ignored requests to explain that. IT might help if we knew what your target goal is...

Background: I've been programming for over 32 years. Have had to deal with files in binary, or not... Many file formats. On Mainframes down through handheld devices. On many OS'es. You have not explained what the boundaries and framework of the environment it is for.

Because reading your first post, before reading your second post... Since you are posting on a Linux Forum, I suspected a Linux Text Format... Where adding a blank line to the end of a text file would work... Such as 
```

echo "" >> test.txt

```
But you effectively said no, right?

I think the misunderstanding here, is that your terminology is off. Possibly you are tasking about for a different OS such as Windows and DOS rather than Linux/UNIX(???) Because in Linux text files the end of line character is a Line Feed, LF, escape n, denoted as \n. In Windows and DOS text files, the end of line characters are both Carraige Return life Feed, CR LF, escape r escape n, which is denoted as \r\n...

Is that what you are referring to?

So to convert a Linux Text file to DOS/Windows format:
```

sed 's/[^\x0d]\x0a/\x0d\x0a/g' FileName.txt

```

---

### Post by oldfred on 2022-09-15
I download some files from my bank, and they have wrong line endings, so I convert them.

You also can convert files with the dos2unix program.
From man dos2unix
[FONT=monospace][COLOR=#000000]dos2unix - DOS/Mac to Unix and vice versa text file format converter[/COLOR]

There also is tofrodos.
Tofrodos comprises one program, "fromdos" alias "todos", which converts
text files to and from these formats. Use "fromdos" to convert DOS
text files to the Unix format, and "todos" to convert Unix text files
to the DOS format.[/FONT]

---

### Post by enricomar on 2022-09-15
it's true, I formulated badly; actually the question was simpler: I need to add a line (or space) to a bunch of txt files inside a directory. I solved with the space (echo etc) as stated above, thanks anyway

---

### Post by MAFoElffen on 2022-09-17
So if this is resolved, then please go to the upper left of the thread and use the "Thread Tools" link to mark this thread as "Solved" so that other users can find your answer to help them their own similar questions.

---

### Post by TheFu on 2022-09-17
```
echo " " | tee -a * .txt
```
is wrong.  It has an added space that will cause all files in the directory to get the added lines.  If they are only text, fine.  If not, you've just corrupted every other file.


Unix isn't MS-DOS.  There are no extensions, so we don't need to have *.txt <---- without the space.  Use this instead:
```
echo " " >> *txt
OR
echo " " | tee -a *txt
```
if you want to waste an extra process starting that isn't needed.

Saving a character on every command over a day will save hundreds of extra characters, if not more.  Add that up over weeks, months, years and the savings is huge in time and keyboard wear.

---

### Post by mIk3_08 on 2022-09-19
> **enricomar said:**
> Hi everyone! I have a bunch of txt files and some of them, on R, give me an "incomplete final line found" error. So I would like to add a line to all .txt files contained in a folder. Tips? Thank you! Can you elaborate more about your issue. Because many in this community that are willing to help you. Regards and cheers.

---

