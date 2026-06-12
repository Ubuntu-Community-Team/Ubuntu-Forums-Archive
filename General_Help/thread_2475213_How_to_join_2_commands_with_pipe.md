---
title: "How to join 2 commands with pipe ?"
date: 2022-05-19
forum: General Help
---

### Post by satimis on 2022-05-19
How to join 2 commands with pipe ?

command-1
$ convert -negate *.jpg
(convert all negative images to positive images)

command-2
$ convert -rotate -90 *.jpg
(rotate all images 90 deg counter-clockwise)

Is the command
$ convert -negate *.jpg | > convert -rotate -90
?

if further zip all output .jpg files to a image.zip file

Whether run;
$ convert -negate *.jpg | > convert -rotate -90 | > zip image.zip
?

Thanks

Regards

---

### Post by TheFu on 2022-05-19
Every "filter" is a little different. Some read from stdin and write to stdout automatically.  Some filters need hints that you want to read from stdin and write to standard out.  The hint is usually a '-' (hyphen) in the place where either an input or output file belongs in the command.

Say we have a filter tool called "filter" and it is in our PATH.  It reads from stdin and writes to stdout automatically ... things that show output in the terminal generally are writing to stdout.  grep, cat, more, less are examples that work that way.   Things that don't write all the output to stdout, need to be told explicitly.  Since when we run convert, we don't see a stream of binary (image file data) on the terminal, it doesn't write to stdout by default.

Also, when using file globbing as an input, there's little chance that the downstream filter will recognize where 1 file ends and the other begins.  You'll get garbage or worse.

Also, "| >" isn't how pipes get used.
A contrived example, which should never be used in the real world is:
```
$ cat *txt | grep -Ew 'the'
```
This will read and write all txt files to stdout.  Enhanced grep will read from stdin those files and search for the word "the".  It won't find "there", because I specifically asked for the word search.

For how to deal with multiple inputs, you'll need to handle each 1 at a time.  My sample script in your ffmpeg thread shows how to do that.

There are other methods too using some other processing tools, like **xargs**. xargs takes a list of files to be processed and runs whatever command follows 1 file at a time.  There are other options and the ability to parallelize programs from xargs.  

I use a batch processing queue system called Task Spooler (apt install task-spooler). Each queue that it manages can be configured for 1-process at a time (the default) or to run X number concurrently.  For single threaded tasks, it might make sense to run N-1 tasks where N is the number of cores your CPU has. I suppose the built-in **batch** program can do much of this. Batch is part of **at** and **cron**, I think.

```
NAME
       ts - task spooler. A simple unix batch system
DESCRIPTION
       ts will run by default a per user unix task queue.  The  user  can  add
       commands  to the queue, watch that queue at any moment, and look at the
       task results (actually, standard output and exit error).

```
In ubuntu, the task-spool program has been renamed to **tsp**, from ts. I guess there is another ts command that the Canonical/Debian team uses.  Looks like it is some ssl timestamp tool that I've never used directly.

Anyway, there are many options.

The learn more about pipes and redirection, here's something [https://github.com/jlevy/the-art-of-command-line](https://github.com/jlevy/the-art-of-command-line) that really should be read once a year until everything inside it is clear. Try to integrate new knowledge until it becomes a skill.  Why reread it?  Because as we learn more each year, more of it will make sense. You won't use everything in it, ever, but suppose that 10% makes sense each year. Then after 10 yrs, you can stop re-reading it.

---

### Post by Impavidus on 2022-05-19
**convert** supports multiple transformations at once, so in your case you can simply (and more efficiently) run```
convert -negate -rotate -90 input.jpeg output.jpeg
```
A pipe uses the | character to connect standard output of one command to standard input of another. You have to tell **convert** that you want to use standard output and standard input. As it happens, you can tell this to **convert** by using - as filename. Many application understand this, not all. And some will automatically assume standard input or standard output when you don't give a filename.

---

### Post by TheFu on 2022-05-19
The convert manpage has this summary:
> convert [input-option] input-file [output-option] output-file

So, if you insist on using a pipe (which I wouldn't), you might try ...
```
$ convert -negate *jpg - | convert -rotate -90 - -|  zip image.zip -
```
I doubt that would work, but didn't test it since the .   Also, note that the MS-DOS .jpg isn't needed.  *jpg is the same in any Unix shell. Saving 1 character at a time. ;)  The ZIP file won't have any individual files inside - it will be a stream of data, which isn't really what you want.  This workflow really needs to work on 1 file at a time, so filenames can be controlled for the input/output.

```
$ convert -negate *png -  
```
does force the output to stdout as a stream. If there is 1 image in the glob, that could be fine. If more than 1 image file is found, it won't be too useful.

---

### Post by satimis on 2022-05-19
> **Impavidus said:**
> **convert** supports multiple transformations at once, so in your case you can simply (and more efficiently) run```
convert -negate -rotate -90 input.jpeg output.jpeg
```
A pipe uses the | character to connect standard output of one command to standard input of another. You have to tell **convert** that you want to use standard output and standard input. As it happens, you can tell this to **convert** by using - as filename. Many application understand this, not all. And some will automatically assume standard input or standard output when you don't give a filename.
Thanks for your advice.

What I'm planning to achieve is no output files generated.  The convert commands will convert all input files to positives and rotate all input files 90 deg counter-clockwise.

I suppose it can be done on running;```

$ convert -negate -rotate -90 *.jpeg

```

On the 2nd command - compress all *.jpeg files to a .zip file```

$ convert -negate -rotate -90 *.jpeg | zip image.zip

```
?

Regards

---

### Post by ActionParsnip on 2022-05-19
Could make a script and use temporary files in /tmp and then a resulting file will arrive. As stated earlier you can add multiple transforms in convert

---

### Post by Holger_Gehrke on 2022-05-19
> **satimis said:**
> Thanks for your advice.

What I'm planning to achieve is no output files generated.  The convert commands will convert all input files to positives and rotate all input files 90 deg counter-clockwise.

I suppose it can be done on running;```

$ convert -negate -rotate -90 *.jpeg

```

On the 2nd command - compress all *.jpeg files to a .zip file```

$ convert -negate -rotate -90 *.jpeg | zip image.zip

```
?

Regards
This won't work because of the way wildcards / globbing works. The wildcard characters are not interpreted by the program but by the shell. So before convert is started the shell expands '*.jpeg' into a list of files which fulfill the conditions your glob-pattern expresses. Convert will then expect the last name in the list to be the name of the target file. If there are multiple files it will overwrite the last file in the list with the conversion of the first and write the second to the next to last into files with names built from that name with a dash and numbers appended before the extension.

If you use '-' as the output file convert will write to standard output but since a stream with multiple images in a file meant for one image (like a jpg or a png) is invalid it will abort the run after the first image.

What you can do instead is to loop over the files you want to convert, have convert do it's work and write to temporary files, zip those up and delete them afterwards, somewhat like this:
```

for i in *.jpeg; do
convert -negate -rotate -90 "$i" "${i%%.jpeg}-neg-90.jpeg"
done
zip images.zip *-neg-90.jpeg
rm *-neg-90.jpeg

```

The quotes around the parameter substitutions are a safeguard in case there are filenames with spaces; the "${i%%.jpeg}" is a parameter expansion that removes the given suffix (.jpeg) from the name. By doing it this way, you're getting one converted file per input file with a name based on the original name but with '-neg-90' inserted before the dot. Instead of the simple pattern '*.jpeg'  in the first line you can put any valid wildcard pattern (or even multiple patterns ...). You might want to check whether you already have files whose names end in '-neg-90.jpeg' before running this, otherwise they'll end up zipped and deleted.

Holger

---

### Post by TheFu on 2022-05-19
This is an excellent option: 
```
for filename in *.jpeg; do
```

as compared to what I normally use, which is:
```
for filename in "$@"; do
```

The difference is that the first will handle filenames with spaces and the "$@" will not because a space is a natural separator for most shells.  This is a key reason why I don't allow any filenames on my systems with spaces.  One of the first things I do when a new file shows up with spaces is to  run a script that does this:
~/bin/ren-fav
```
#!/bin/sh

IN="$1"
if [ "X$IN" = "X" ] ; then
  echo "no input match. 
 Usage:
   $0 lead-character-filename-pattern
  eg.
   $0 FX
"
  exit 1
fi
rename 's/ /_/g' $IN*;
rename 's/[_]+/_/g' $IN*;
rename 's/_-_/-/g' $IN*;
rename 's/-_/-/g' $IN*
rename 's/_2022/-2022/g' $IN*

```

It is a strange script, in that it doesn't want any filenames, just the start of the filename. If I have files named like this:
```
file 1.jpg
file 2.jpg
file 3.jpg
file 4.jpg
file 5.jpg
file 6.jpg
file 7.jpg
file 8.jpg
file 9.jpg
file 10.jpg
```
I can rename all of them to not have that space with 
```
ren-fav  file
```
or
```
ren-fav  f
```

I have a preference for years to be -YYYY, not _YYYY. Leave out that if you feel different.
I also have a preference for word-word, not word_-_word.
Anyway, the script above has been working for years here. Over a decade.

---

### Post by Impavidus on 2022-05-19
> **Holger_Gehrke said:**
> Convert will then expect the last name in the list to be the name of the target file. If there are multiple files it will overwrite the last file in the list with the conversion of the first and write the second to the next to last into files with names built from that name with a dash and numbers appended before the extension.

I just checked. convert indeed expects the last argument to be the target file, but will already use the constructed filenames for the first file it processes. The last file on the command line is not converted, but also not overwritten. At least, on Xubuntu 21.10.

zip can actually read from a pipe and add the files to the archive one by one, but the problem is setting the filename.```
convert -negate -rotate -90 input.jpeg - | zip archive.zip -
```will convert the file, then add it to archive.zip and you could run it multiple times, but each file will be added to the archive with the name -, so in the end only the last file will be there. Unfortunately, it appears there's no option in zip to set the filename of a file it reads from stdin, or to store a file in the archive under a different name than the filename from where it's read (except simple transformations). I think archive tools should be able to do so. If you insist, you could use a named pipe. You can also rename a file when it's already in the archive. All of that is less efficient than storing the image in a temporary file, as this makes the zip archive into a temporary file. I can't find this option in the man page for tar either, where it actually should be efficient..

BTW, you can't really compress jpeg files into a zip archive. Jpeg is already compressed, so it will be put into the archive, but without significant compression. You can just as well use an uncompressed archive format

---

### Post by satimis on 2022-05-19
> **Holger_Gehrke said:**
> This won't work because of the way wildcards / globbing works. The wildcard characters are not interpreted by the program but by the shell. So before convert is started the shell expands '*.jpeg' into a list of files which fulfill the conditions your glob-pattern expresses. Convert will then expect the last name in the list to be the name of the target file. If there are multiple files it will overwrite the last file in the list with the conversion of the first and write the second to the next to last into files with names built from that name with a dash and numbers appended before the extension.
....
....

Can I do it in 2 commands ?

1)
$ convert -negate -rotate -90 *.jpeg
Convert all .jpeg files to positive and rotate them counter-clockwise 90 deg

2)
$ zip images.zip *.jpeg 

Regards

---

### Post by satimis on 2022-05-19
> **TheFu said:**
> This is an excellent option: 
```
for filename in *.jpeg; do
```

as compared to what I normally use, which is:
```
for filename in "$@"; do
```

The difference is that the first will handle filenames with spaces and the "$@" will not .......
....

Thanks for your advice.

What is filename with space ? 

If the filename consists several words I'll join the words with "-", not leaving space between words.

Regards

---

### Post by satimis on 2022-05-19
> **Impavidus said:**
> I just checked. convert indeed expects the last argument to be the target file, but will already use the constructed filenames for the first file it processes. The last file on the command line is not converted, but also not overwritten. At least, on Xubuntu 21.10.

zip can actually read from a pipe and add the files to the archive one by one, but the problem is setting the filename.```
convert -negate -rotate -90 input.jpeg - | zip archive.zip -
```will convert ....
Thanks for your advice.

What is the use of  "-" at end of each command ?

Regards

---

### Post by Holger_Gehrke on 2022-05-19
> **satimis said:**
> 
What is the use of  "-" at end of each command ?


Some programs that don't normally act as filters - among them convert and zip - will read from standard input or write to standard output if you give a dash as the input or output file. But as Impavidus already said this has some unwanted consequences. Standard input is just a continuous stream of data without a name. So the zip archive created that way will have just one file in it named '-'. convert will abort the conversion as soon as it notices that it is producing something no one will be able to read, basically stopping after the first image.

You could of course make convert produce a file in a format that can hold multiple images like tif, gif or pdf by prefacing the '-' with the format name (for example 'tif:-') but that is probably not what you want ...

Holger

---

### Post by satimis on 2022-05-20
> **Holger_Gehrke said:**
> Some programs that don't normally act as filters - among them convert and zip - will read from standard input or write to standard output if you give a dash as the input or output file. But as Impavidus already said this has some unwanted consequences. Standard input is just a continuous stream of data without a name. So the zip archive created that way will have just one file in it named '-'. convert will abort the conversion as soon as it notices that it is producing something no one will be able to read, basically stopping after the first image.

You could of course make convert produce a file in a format that can hold multiple images like tif, gif or pdf by prefacing the '-' with the format name (for example 'tif:-') but that is probably not what you want ...

Holger
Your advice noted.  Thanks

On #10 above
I have asked 

Can I do it in 2 commands ?

1)
$ convert -negate -rotate -90 *.jpeg
Convert all .jpeg files to positive and rotate them counter-clockwise 90 deg

Then

2)
$ zip images.zip *.jpeg 

Pls advise.  Thanks

Regards

---

### Post by Holger_Gehrke on 2022-05-20
> **satimis said:**
> 
Can I do it in 2 commands ?

1)
$ convert -negate -rotate -90 *.jpeg
Convert all .jpeg files to positive and rotate them counter-clockwise 90 deg

Then

2)
$ zip images.zip *.jpeg 


As I already said in post #7, step 1 won't work quite the way you want because of the way wildcards - in this case '*.jpeg' work. The shell expands '*.jpeg' into a list of all files whose names end with '.jpeg' and passes these as parameters to 'convert'. 'convert' expects the last filename to be the name of the file to write to. You can instead use a filename reference as the target name, like this:
```

convert -negate rotate -90 *.jpeg 'rotated-negated-%d.jpeg'

```
The '%d' in the target name will be replaced with a count starting from 0 and the converted files will be written as 'rotated-negated-0.jpeg' and following.

Archiving the images the way you write will zip up all the *jpeg, original and converted. If you only want the ones which have been inverted and rotated and use the command using '%d' I gave above then you might want to be more specific with your wildcards, something like
```

zip images.zip rotated-negated-*.jpeg

```
On the other hand if you want to zip up the originals for safekeeping and backing them up, you might take a look at extended globbing in the bash (details are in the bash manual page in the section 'Pattern Matching'). There is a way to make the bash create a list of the file which are **not** like the wildcards you specify. For this to work, the option 'extglob' of the shell needs to be active. You can use the command 'shopt' to check, by default it should be on.
```

zip images.zip !(rotated-negated-*.jpeg)

```
This  will zip up all files except the ones with names starting with 'rotated-negated-' and ending with '.jpeg'. Obviously this will zip up **everything** else, so checking before you do this what else is in that directory is a good idea.

Holger

---

### Post by satimis on 2022-05-20
> **Holger_Gehrke said:**
> As I already said in post #7, step 1 won't work quite the way you want because of the way wildcards - in this case '*.jpeg' work. The shell expands '*.jpeg' into a list of all files whose names end with '.jpeg' and passes these as parameters to 'convert'. 'convert' expects the last filename to be the name of the file to write to. You can instead use a filename reference as the target name, like this:
```

convert -negate rotate -90 *.jpeg 'rotated-negated-%d.jpeg'

```
The '%d' in the target name will be replaced with a count starting from 0 and the converted files will be written as 'rotated-negated-0.jpeg' and following.
.....
.....

Thanks for your advice.

Performed following test;

In a Test folder there are 2 .jpeg files

$ cd Test
Test$ ls```

tower1a.jpeg  tower2a.jpeg

```

$ convert -negate -rotate -90 *.jpeg 'rotated-negated-%d.jpeg'
no complaint

Test$ ls```

rotated-negated-0.jpeg  rotated-negated-1.jpeg  tower1a.jpeg  tower2a.jpeg

```

2 new files created;
rotated-negated-0.jpeg  
rotated-negated-1.jpeg

They are positive images and rotated 90 deg counter-clockwise.

How to only change the original files without creating new files ?

Regards

---

### Post by Holger_Gehrke on 2022-05-20
'convert' always writes to new files. For changing the original files use 'mogrify' instead. It's another tool from the ImageMagick suite and accepts all the same options (except for any methods for changing the output file, obviously).

Holger

---

### Post by satimis on 2022-05-20
> **Holger_Gehrke said:**
> 'convert' always writes to new files. For changing the original files use 'mogrify' instead. It's another tool from the ImageMagick suite and accepts all the same options (except for any methods for changing the output file, obviously).

Holger
Your advice works.  Thanks
```

$ mogrify -negate -rotate -90 *.*

```

Done

Edit
==
Tried again with new negative.jpeg files

1)
Test$ mogrify -negate -rotate -90 *.jpeg | zip image.zip
Only handing there without progress

2)
$ mogrify -negate -rotate -90 *.jpeg | zip image.zip *.jpeg```

  adding: tower-1a.jpeg (deflated 0%)
  adding: tower-2a.jpeg (deflated 1%)
```

Nothing changes on the archived files

Regards

---

### Post by Impavidus on 2022-05-21
Think again. That's not how pipes work (which we tried to explain). With the | syntax in the bash shell, they connect standard output of one application to standard input of another.
> **satimis said:**
> 
Tried again with new negative.jpeg files

1)
Test$ mogrify -negate -rotate -90 *.jpeg | zip image.zip
Only handing there without progress
mogrify converts the images and writes them to ordinary files. Not to standard output, which is connected to standard input of zip, so zip cannot read the converted image files. And although zip can read the files it has to compress from standard input, that's not what you want, because it would see al its input as a single file.
> 
2)
$ mogrify -negate -rotate -90 *.jpeg | zip image.zip *.jpeg```

  adding: tower-1a.jpeg (deflated 0%)
  adding: tower-2a.jpeg (deflated 1%)
```

Nothing changes on the archived files
mogrify converts the images and zip archives them, that's correct, but the images are never written to the pipe and never read from it, so you can skip the pipe. What's more, when you run two applications at the same time using a pipe, they actually run at the same time. If the pipe buffer gets empty, the reading application is paused, and if the pipe buffer gets full, the writing application is paused, but as nothing is send through the pipe in this case, this doesn't even apply.

But that's not what you want. You first want mogrify to modify the images, then zip has to archive them, so you must guarantee that zip runs after mogrify. In your command, you cannot predict whether the old or new version of the jpeg is stored in the archive. If zip starts reading a particular jpeg before mogrify has finished writing it (which is likely, but not guaranteed), the old versions will be archived. So you have to run one command, wait for it to complete, then run the other.

BTW, note the "deflated 0%" output. zip is unable to compress the files.

---

### Post by satimis on 2022-05-21
> **Impavidus said:**
> Think again. That's not how pipes work (which we tried to explain). With the | syntax in the bash shell, they connect standard output of one application to standard input of another.
mogrify converts the images and writes them to ordinary files. Not to standard output, which is connected to standard input of zip, so zip cannot read the converted image files. And although zip can read the files it has to compress from standard input, that's not what you want, because it would see al its input as a single file.

mogrify converts the images and zip archives them, that's correct, but the images are never written to the pipe and never read from it, so you can skip the pipe. What's more, when you run two applications at the same time using a pipe, they actually run at the same time. If the pipe buffer gets empty, the reading application is paused, and if the pipe buffer gets full, the writing application is paused, but as nothing is send through the pipe in this case, this doesn't even apply.

But that's not what you want. You first want mogrify to modify the images, then zip has to archive them, so you must guarantee that zip runs after mogrify. In your command, you cannot predict whether the old or new version of the jpeg is stored in the archive. If zip starts reading a particular jpeg before mogrify has finished writing it (which is likely, but not guaranteed), the old versions will be archived. So you have to run one command, wait for it to complete, then run the other.

BTW, note the "deflated 0%" output. zip is unable to compress the files.
Hi,

Lot of thanks for your detailed advice.

Please advise;
1) How to continue running the 2nd zip command?
2) Dose "mogrify" works on;
```

mogrify -quality 50%

```
3) If 2) above works.  Can I run;
```

mogrify -negate -rotate 90 -quality 50% -brightness-contrast 150x15 *.jpeg

```
?

Thanks

Regards

---

### Post by Holger_Gehrke on 2022-05-22
```

mogrify -negate -rotate 90 -quality 50% -brightness-contrast 150x15 *.jpeg

```

While the options and their combinations are legal, I would not do such sweeping changes without having a backup of the original images; I'd go with convert in a loop and check the results carefully before further steps.

Unless I forgot something, there are four way to execute two or more programs together:
[LIST]
[*]You already know about about piping; both programs are started together and the standard output of the first program gets connected to the standard input of the second program. Obviously this doesn't work in a useful manner for programs that don't use standard input/standard output. 
[*]You can execute programs one after the other from one command line by simply putting a semicolon in between, for example 'ls;du -c --max-depth 1 .'. 
[*]You can make the call to the second program depend on the success of the first by putting '&&' between the commands. So 'cd workdir && mkdir tmp' will only create the directory 'tmp' if the change to 'workdir' succeeded. 
[*]You can make the call to the second program depend on the failure of the first by putting '||' between the commands. So 'unzip -t files.zip>/dev/null||echo 'Something is wrong with the archive' will test files.zip and hide the output from zip and only print a message if the test fails. 
[/LIST]
In this specific case I'd use '&&': zip up the files after mogrify but only if no errors occurred.

Holger

---

### Post by satimis on 2022-05-22
> **Holger_Gehrke said:**
> ```

mogrify -negate -rotate 90 -quality 50% -brightness-contrast 150x15 *.jpeg

```

While the options and their combinations are legal, I would not do such sweeping changes without having a backup of the original images; I'd go with convert in a loop and check the results carefully before further steps.

Unless I forgot something, there are four way to execute two or more programs together:
[LIST]
[*]You already know about about piping; both programs are started together and the standard output of the first program gets connected to the standard input of the second program. Obviously this doesn't work in a useful manner for programs that don't use standard input/standard output. 
[*]You can execute programs one after the other from one command line by simply putting a semicolon in between, for example 'ls;du -c --max-depth 1 .'. 
[*]You can make the call to the second program depend on the success of the first by putting '&&' between the commands. So 'cd workdir && mkdir tmp' will only create the directory 'tmp' if the change to 'workdir' succeeded. 
[*]You can make the call to the second program depend on the failure of the first by putting '||' between the commands. So 'unzip -t files.zip>/dev/null||echo 'Something is wrong with the archive' will test files.zip and hide the output from zip and only print a message if the test fails. 
[/LIST]
In this specific case I'd use '&&': zip up the files after mogrify but only if no errors occurred.

Hi Holgate

Your advice works for me.  Thanks.
```

mogrify -negate -rotate -90 *.* && zip image.zip *.*

```

I already forgot &&. I used it quite often before;
```

sudo apt update && sudo apt upgrade

```

Later I changed it to ; ```

sudo apt update ; sudo apt upgrade

```

I have tested "\" (backslash), the Linux line-continuation character.  It didn't work for me.

In these few days I have tried hard to find an easy way to digitize all my old film negatives, about 1,000 negatives.  It is because some of their old photos have become yellow in color.

I found an esay way scanning film negatives on Smart Phone, using a 10" Tablet as light box.  It worked for me without problem. I performed the tests on a Smart Phone, with and without scanning software installed.  They worked for me even on Smart Phone >10 years old.  The scanning speed is much faster than scanning film negatives on flatbed scanner.

I scanned 20 film negatives for this test.  Afterwards I saved the negative images in 4 folders.
Folder-1 negative images only needing for converting to postive images
Folder-2 negative images needing for converting to postive images and rotating 90 deg
Folder-3 negative images needing for converting to postive images and rotating -90 deg
Folder-4 negative images needing for converting to postive images and rotating 180 deg

Then I ran following commands on each folder
Folder-1```

mogrify -negate *.*
```

Folder-2```

mogrify -negate -rotate 90 *.*
```

Folder-3```

mogrify -negate -rotate -90 *.*
```

Folder-4```

mogrify -negate -rotate 180 *.*
```

They all worked correctively without problem.

Then I performed further test on adjusting brightness and contrast collectivley;
Step-1
Move the images on Folder-2/3/4 to Folder-1

Step-2
On GIMP I tested an image, adjusting the brightness and contrast, arriving at a value, say 12 and 34, with a good result of image quality.

Step-3
Run following command on Folder-1```

Mogrify -brightness-contrast 12x34 *.*

```

Technically it works without problem but the quality of the 20 images is NOT good.  I think it needs to perform post-editing on GIMP, one by one.  There is no easy way?

I think I have to surrender the idea of scanning old film negatives on Smart Phone and scan their photos on flatbed scanner.  Even some of them have become yellow in color.  I can remove their yellow color on GIMP.  But the quality of the digital image is NOT so perfect as its original.  Besides the time scanning photos on flatbed scanner is much slower than scanning film negatives on Smart Phone.

My old Epson Perfection 3490 Photo Scanner still works.  But it is time for it to retire.  If finally I decide to scan my old photos on flatbed scanner, instead of scanning film negatives on Smart Phone, I'll purchase an Epson V850 Pro photo scanner to do the job.

The final image files are NOT for printing.  I'll use them on digital album, slide show on computer as well as on website etc.

Your comment and suggestion are welcome.  Thanks

Regards

---

