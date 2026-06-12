---
title: "No File Type On Filename"
date: 2023-05-27
forum: General Help
---

### Post by wyattwhiteeagle on 2023-05-27
Using the Terminal, are there commands to have the file types added to the end of the filenames?


This only applies to files under the directories that I personally have created which doesn't have the file type in the filename.


In a folder under "Detailed List", the "Type" column will identify the file type of each item within the folder.
Some of these files doesn't have the file type as part of the filename.
You know, the "*.txt", "*.png", "*.html"...

---

### Post by Holger_Gehrke on 2023-05-27
Don't confuse 'extension' and 'file type'. Also 'file type' can mean different things in different situations. A directory is a file type, so is a block device file, a character device file, a named pipe, or a symbolic link. What you mean is the type of the file contents aka MIME-type. You can use the command 'file' to get a short description of the type of contents in a file; example 'file MyFileWithoutAnExtension' (which will print 'data' if it can't identify the contents or 'empty' for a file without any content). Any command that can change the file name can add an extension. You could use something like "rename 's/$/.png/' *" to add an extension to all files in the current working directory. Or you could use something like 'mv myfile myfile.odt' to rename them one at a time. Or you could just rename them in the file manager of your choice.

Holger

---

### Post by wyattwhiteeagle on 2023-05-27
> **Holger_Gehrke said:**
> Don't confuse 'extension' and 'file type'. Also 'file type' can mean different things in different situations. A directory is a file type, so is a block device file, a character device file, a named pipe, or a symbolic link. What you mean is the type of the file contents aka MIME-type. You can use the command 'file' to get a short description of the type of contents in a file; example 'file MyFileWithoutAnExtension' (which will print 'data' if it can't identify the contents or 'empty' for a file without any content). Any command that can change the file name can add an extension. You could use something like "rename 's/$/.png/' *" to add an extension to all files in the current working directory. Or you could use something like 'mv myfile myfile.odt' to rename them one at a time. Or you could just rename them in the file manager of your choice.

Holger

Thank you
Your reply details some things which I may utilize in the future.

Perhaps adding a more detailed example in describing what I'm looking for is needed.
So here goes...I hope this clarifies

Renaming the files in the file manager seems to take forever sometimes.

I'm working on a shell script (bash).
I use this script to recover lost files I use on IMVU, a "Instant Messaging Virtual Universe".
For those who don't know, it's a social media chat site that most people use for roleplaying.

The script doesn't delete or remove all of the files.
Only those files which would be repeated every time I run the script
Not deleting those files would return an error message like "File already exists. not moving (or overwriting) the file."

The files I keep are mostly image files, but there are others which I keep that aren't images.
If it's an image file and not a text file, I don't want to rename the file from "Wyatt", being an image, to "Wyatt.txt".
I want to name it to "Wyatt.png" or "Wyatt.jpg"

The same goes for the other types of files that I keep, ie text files, html files, pdf files...

These files have no file extensions.
However, the "Type" column shows what type of file it is.
Whether it's a "plain text file", "xsf file", "xml file", "html document", "png image", "jpg image", "shell script", etc.

Notice in the script there's no file extension of the file specified in the "rm" command line.
That's how all the files in the source subdirectories appear.
```
mkdir /home/wyatt/Desktop/IMVU-Extracted-Textures
find /home/wyatt/.wine/drive_c/users/wyatt/AppData/Roaming/IMVU/HttpCache/* -type f -print0 | xargs -0 mv -t /home/wyatt/Desktop/IMVU-Extracted-Textures
find /home/wyatt/.wine/drive_c/users/wyatt/AppData/Roaming/IMVU/HttpCache/* -type d -empty -delete
find /home/wyatt/Desktop/IMVU-Extracted-Textures -type f -name 'product*' -delete
rm -f /home/wyatt/Desktop/IMVU-Extracted-Textures/0b8bca5651664e27a343fb71586eb7f7
ls /home/wyatt/Desktop/IMVU-Extracted-Textures > /home/wyatt/Desktop/IMVU-Extracted-Textures.txt
```

---

### Post by wyattwhiteeagle on 2023-05-27
*Update*

I know that "plain text file" usually, not for everything, under "Details > Type" means the file may be renamed ".txt"

---

### Post by Holger_Gehrke on 2023-05-27
Get the file types from 'file' and then use a case construct to rename them. Something like:
```

for i in * do
  a=$(file "$i")
  a=${a#*:} # remove the leading filename
  a=${a%%,*} # remove all details after the first comma
  case a in
  "PNG image data" ) mv "$i" "$i".png ;;
  "JPEG image data" ) mv "$i" "$i".jpg ;;
  .
  .
  .
  esac
done

```

---

### Post by wyattwhiteeagle on 2023-05-27
How many lines can a script hold before the script becomes unable to be edited?

Scripting such as this may become quite lengthy, thus rendering the script to become uneditible or even unusable.
It may be beneficial to include a command line at the end of these scripts to invoke another script.

---

### Post by Holger_Gehrke on 2023-05-27
If an editor has a limit on how many lines a file may have, then it's time to switch to a better editor. I know that both vi(m) and emacs have no problem loading files bigger than available memory (they load just as much of the file as fill fit and then they start paging the file in as needed ...). A script I downloaded recently - it produces contact sheets from video files using ffmpeg and ImageMagick - is about 180 kb in 5348 lines. I have produced scripts that are longer than that (much simpler, but longer) for a similar purpose to what you're doing by doing ```
for i in * ; do echo mv \"$i\" \"$i\";done>script
```I then had several thousand lines of mv commands which I edited and ran when I was happy with them.

Holger

---

### Post by wyattwhiteeagle on 2023-05-28
CLI text editors such as nano, vim, and visudo...I can use them, but they aren't my "cup of tea".


I've never encountered a line limit when creating a script, however I have encountered a line limit when opening a script which was put on the system when performing a fresh clean Distro install.


Therefore, I'm not exactly sure what the line limit of featherpad is.


Perhaps some scripts aren't meant to be accessed using a simple text editor.

---

### Post by wyattwhiteeagle on 2023-08-24
Found this "one-liner" command to add an extension to all files in a directory (not the current working directory) that have no extension
```
find /path -type f -not -name "*.*" -exec mv "{}" "{}".jpg \;
```
Source: [https://stackoverflow.com/questions/1108527/recursively-add-file-extension-to-all-files](https://stackoverflow.com/questions/1108527/recursively-add-file-extension-to-all-files)

This solves this thread.

---

### Post by Holger_Gehrke on 2023-08-25
Well, actually it doesn't. This code will rename all the files without extension to have the extension '.jpg' which might be wrong. Consider the most common extension-less files you will find in almost every source code distribution: README, INSTALL, and LICENSE ...

A search for "fixing wrong file extensions on linux" brought up this one liner:
```

find . -type f -not -name "*.*" | while read FILE; do if [ $(file --mime-type -b "$FILE") == "image/jpeg" ]; then mv "$FILE" "$FILE".jpg; fi; done;

```
 which will only rename files that actually are JPEG files to have the extension '.jpg'.

Holger

---

### Post by wyattwhiteeagle on 2023-08-25
```

find . -type f -not -name "*.*" | while read FILE; do if [ $(file --mime-type -b "$FILE") == "*/*" ]; then mv "$FILE" "$FILE".*; fi; done;

```
What would the above do?
I used "wildcards" in place of "media/jpeg" and jpg.
> **Holger_Gehrke said:**
> Well, actually it doesn't. This code will rename all the files without extension to have the extension '.jpg' which might be wrong. Consider the most common extension-less files you will find in almost every source code distribution: README, INSTALL, and LICENSE ...

A search for "fixing wrong file extensions on linux" brought up this one liner:
```

find . -type f -not -name "*.*" | while read FILE; do if [ $(file --mime-type -b "$FILE") == "image/jpeg" ]; then mv "$FILE" "$FILE".jpg; fi; done;

```
 which will only rename files that actually are JPEG files to have the extension '.jpg'.

Holger
Wow, thank you for that AWESOME input.

When I did my search, that wasn'tin the results.
Great find!

---

### Post by wyattwhiteeagle on 2023-08-25
*UPDATE*
Nope, changing from the current working directory didn't work.

Still looking

---

### Post by Holger_Gehrke on 2023-08-26
> **wyattwhiteeagle said:**
> ```

find . -type f -not -name "*.*" | while read FILE; do if [ $(file --mime-type -b "$FILE") == "*/*" ]; then mv "$FILE" "$FILE".*; fi; done;

```
What would the above do?
I used "wildcards" in place of "media/jpeg" and jpg.


Wildcards (aka globs) aren't a magical way of making the computer do what you want. They are part of the parsing process the shell does for every command. This part of the process is called pathname expansion. In short: glob patterns are expanded to a space separated list of matching filenames. Your code might do ... something ... but very probably not what you intend.

You might be able to do something closer to what you want by using an associative array with mime-types as the keys and extensions as the values.
```

declare -A extensions=([image/png]=.png [image/jpeg]=.jpg [image/gif]=.gif [application/gzip]=.gz [application/zip]=.zip [text/html]=.html [image/webp]=.webp [image/svg+xml]=.svg [text/plain]=.txt); find . -type f -not -name "*.*" | while read FILE; do mv "$FILE" "$FILE"${extensions[$(file -b --mime-type $FILE)]}; done;

```

Holger

---

### Post by wyattwhiteeagle on 2023-08-26
> **Holger_Gehrke said:**
> Wildcards (aka globs) aren't a magical way of making the computer do what you want. They are part of the parsing process the shell does for every command. This part of the process is called pathname expansion. In short: glob patterns are expanded to a space separated list of matching filenames. Your code might do ... something ... but very probably not what you intend.

You might be able to do something closer to what you want by using an associative array with mime-types as the keys and extensions as the values.
```

declare -A extensions=([image/png]=.png [image/jpeg]=.jpg [image/gif]=.gif [application/gzip]=.gz [application/zip]=.zip [text/html]=.html [image/webp]=.webp [image/svg+xml]=.svg [text/plain]=.txt); find . -type f -not -name "*.*" | while read FILE; do mv "$FILE" "$FILE"${extensions[$(file -b --mime-type $FILE)]}; done;

```

Holger
It worked
However, it changed more than I expected. I'm gonna trust that it won't cause any issue's later.
How would I limit it to only the expected subdirectorie's?
(not the current working directory, please)

---

### Post by Holger_Gehrke on 2023-08-26
By giving find one or more directories as starting points for the search instead of giving '.' (which means 'current working directory').
```

declare -A extensions=([image/png]=.png [image/jpeg]=.jpg [image/gif]=.gif [application/gzip]=.gz [application/zip]=.zip [text/html]=.html [image/webp]=.webp [image/svg+xml]=.svg [text/plain]=.txt);\
find **/home/wyatt/Desktop/IMVU-Extracted-Textures** -type f -not -name "*.*" | while read FILE; do mv "$FILE" "$FILE"${extensions[$(file -b --mime-type $FILE)]}; done;

```

'find' can take multiple starting points for it's search, just give them all as a space separated list before any tests or actions. Also there are options '-maxdepth' and '-mindepth' (both followed by a non-negative whole number). These give the maximum and minimum number of directory-depth to go to for searching. And then there's '-path' and '-prune' which can be used to stop find from going into specific directories. 'man find' is really worth a read, I discover things I didn't consider every time I re-read it ...

A small tip: when trying out things like this, I usually put an 'echo' command before any commands that will make lasting changes. That way it tells me what it would do but doesn't (yet) do it. In this specific case, the 'echo' would go before the 'mv' :
```

declare -A extensions=([image/png]=.png [image/jpeg]=.jpg  [image/gif]=.gif [application/gzip]=.gz [application/zip]=.zip  [text/html]=.html [image/webp]=.webp [image/svg+xml]=.svg  [text/plain]=.txt);\
find /home/wyatt/Desktop/IMVU-Extracted-Textures -type f -not -name "*.*" | while read FILE; do **echo** mv "$FILE" "$FILE"${extensions[$(file -b --mime-type $FILE)]}; done;

```

Much safer that way ...

Holger

Edit: I don't know what file manager you're using, but in Thunar there is an option to rename multiple files in various ways. If I order the list by file type, mark the ones of one type, and either hit F2 or select 'rename' from the context menu, I get a form in which I can do a 'rename' in various ways. I usually use the 'regular expression' option when using this, select 'name and suffix' as what to rename, 'search and replace' as mode, give '(.*)' as the expression to search for and '$1.jpg' (or whatever extension I want to append). Apart from the short wait while it refreshes it's preview, this is quite quick. I'd be surprised if there wasn't something similar in whatever file manager you use.

---

### Post by wyattwhiteeagle on 2023-08-26
> **Holger_Gehrke said:**
> By giving find one or more directories as starting points for the search instead of giving '.' (which means 'current working directory').
```

declare -A extensions=([image/png]=.png [image/jpeg]=.jpg [image/gif]=.gif [application/gzip]=.gz [application/zip]=.zip [text/html]=.html [image/webp]=.webp [image/svg+xml]=.svg [text/plain]=.txt);\
find **/home/wyatt/Desktop/IMVU-Extracted-Textures** -type f -not -name "*.*" | while read FILE; do mv "$FILE" "$FILE"${extensions[$(file -b --mime-type $FILE)]}; done;

```

'find' can take multiple starting points for it's search, just give them all as a space separated list before any tests or actions. Also there are options '-maxdepth' and '-mindepth' (both followed by a non-negative whole number). These give the maximum and minimum number of directory-depth to go to for searching. And then there's '-path' and '-prune' which can be used to stop find from going into specific directories. 'man find' is really worth a read, I discover things I didn't consider every time I re-read it ...

A small tip: when trying out things like this, I usually put an 'echo' command before any commands that will make lasting changes. That way it tells me what it would do but doesn't (yet) do it. In this specific case, the 'echo' would go before the 'mv' :
```

declare -A extensions=([image/png]=.png [image/jpeg]=.jpg  [image/gif]=.gif [application/gzip]=.gz [application/zip]=.zip  [text/html]=.html [image/webp]=.webp [image/svg+xml]=.svg  [text/plain]=.txt);\
find /home/wyatt/Desktop/IMVU-Extracted-Textures -type f -not -name "*.*" | while read FILE; do **echo** mv "$FILE" "$FILE"${extensions[$(file -b --mime-type $FILE)]}; done;

```

Much safer that way ...

Holger

Edit: I don't know what file manager you're using, but in Thunar there is an option to rename multiple files in various ways. If I order the list by file type, mark the ones of one type, and either hit F2 or select 'rename' from the context menu, I get a form in which I can do a 'rename' in various ways. I usually use the 'regular expression' option when using this, select 'name and suffix' as what to rename, 'search and replace' as mode, give '(.*)' as the expression to search for and '$1.jpg' (or whatever extension I want to append). Apart from the short wait while it refreshes it's preview, this is quite quick. I'd be surprised if there wasn't something similar in whatever file manager you use.
That worked awesome
Did exactly what I wanted and nothing more.
Would this thread be solved?

---

