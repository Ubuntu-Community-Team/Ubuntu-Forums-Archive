---
title: "Unzip Multiple Zipfile's"
date: 2024-04-24
forum: General Help
---

### Post by wyattwhiteeagle on 2024-04-24
I have multiple zipfile's (*.zip) in 3 different subdirectories.

Using the terminal, how would I unzip these into a different directory?
Not into the current directory.

---

### Post by Holger_Gehrke on 2024-04-24
```

cd the/target/directory
unzip path/to/the/zipfile

```
or ```

unzip path/to/the/zipfile -d the/target/directory

```
'unzip' will unpack the given file into the current working directory or the directory given after the '-d' option, including any directory hierarchy inside the archive. If you want all the files without the hierarchy you can give unzip the option '-j' to unpack the files without reproducing the directory hierarchy. Since 'unzip' will only process one archive per call, you'll have to call it multiple times, once per archive. A loop might be useful ('for i in path1/zipfile1 path2/zipfile2 path3/zipfile3 ; do unzip "$i"; done').

Holger

---

### Post by wyattwhiteeagle on 2024-04-24
> **Holger_Gehrke said:**
> ```

cd the/target/directory
unzip path/to/the/zipfile

```
or ```

unzip path/to/the/zipfile -d the/target/directory

```
'unzip' will unpack the given file into the current working directory or the directory given after the '-d' option, including any directory hierarchy inside the archive. If you want all the files without the hierarchy you can give unzip the option '-j' to unpack the files without reproducing the directory hierarchy. Since 'unzip' will only process one archive per call, you'll have to call it multiple times, once per archive. A loop might be useful ('for i in path1/zipfile1 path2/zipfile2 path3/zipfile3 ; do unzip "$i"; done').

HolgerIt appear's a loop is useful, indeed.
Just so I understand...am I missing anything?
```
'/home/wyatt/Downloads/File-1.zip /home/wyatt/Desktop/Zipped/File-2.zip ; do unzip "$i"; done'

```

---

### Post by wyattwhiteeagle on 2024-04-24
Update...

> **wyattwhiteeagle said:**
> It appear's a loop is useful, indeed.
Just so I understand...am I missing anything?
```
'/home/wyatt/Downloads/File-1.zip /home/wyatt/Desktop/Zipped/File-2.zip ; do unzip "$i"; done'

```
Looks like I'm missing a few things here such as '$i' designation, etc

I'll post later with the terminal output.

---

### Post by Holger_Gehrke on 2024-04-24
Yes, you're missing the 'for i in ' part, which tells the shell that this is a loop and the variable i should be set to one of the listed values at the beginning of each iteration. You also might want to 'cd' into the target directory before running the loop or add a '-d' option with the target directory to the unzip command. And on the command line you don't need the single quotes I enclosed it in. Obviously, with a loop all archives will be unpacked into the same directory unless you do something really fancy - let's say two arrays, one holding the filenames, one holding the paths to extract to, looping over the indices to extract each file to the directory with the same index in the second array. With anything under ten files I probably wouldn't bother with a loop at all and just do the unzipping one at a time.

```

cd the/target/directory
for i in /home/wyatt/Downloads/File-1.zip /home/wyatt/Desktop/Zipped/File-2.zip ; do 
  unzip "$i"; 
done

```

The usual warning: filenames with spaces in them can lead to really surprising results when doing shell-scripting ...

---

### Post by wyattwhiteeagle on 2024-04-24
Oops...missed your reply...let me read and try.
Please don't reply until after my next post.

What I tried didn't work.
What all am I missing in the script?
The script has...
```
SRC="/home/wyatt/Desktop/Test-Folder-2/Image/Wyatts-Scripts.zip /home/wyatt/Desktop/Everything/Compressed/ZIP/Cheys-Place-GA.zip"
TGT="/home/wyatt/Downloads"
unzip "$SRC" -d "$TGT"
```
Here's the output...
```
wyatt@wyatt-hplaptop15ef1xxx:~$    /home/wyatt/Desktop/Test-Script.sh
unzip:  cannot find or open /home/wyatt/Desktop/Test-Folder-2/Image/Wyatts-Scripts.zip /home/wyatt/Desktop/Everything/Compressed/ZIP/Cheys-Place-GA.zip, /home/wyatt/Desktop/Test-Folder-2/Image/Wyatts-Scripts.zip /home/wyatt/Desktop/Everything/Compressed/ZIP/Cheys-Place-GA.zip.zip or /home/wyatt/Desktop/Test-Folder-2/Image/Wyatts-Scripts.zip /home/wyatt/Desktop/Everything/Compressed/ZIP/Cheys-Place-GA.zip.ZIP.
wyatt@wyatt-hplaptop15ef1xxx:~$ 
```

---

### Post by wyattwhiteeagle on 2024-04-24
Thank you so very much.
The below worked.
Marking this as solved.
```
cd /home/wyatt/Downloads
for i in /home/wyatt/Desktop/Test-Folder-2/Image/Wyatts-Scripts.zip /home/wyatt/Desktop/Everything/Compressed/ZIP/Cheys-Place-GA.zip ; do unzip "$i"; 
done
```

---

### Post by Holger_Gehrke on 2024-04-24
As I said, 'unzip' will unpack one file per call. By enclosing the list of files in quotes in post #6, you've turned it into one token. So now unzip looks for one file named '/home/wyatt/Desktop/Test-Folder-2/Image/Wyatts-Scripts.zip /home/wyatt/Desktop/Everything/Compressed/ZIP/Cheys-Place-GA.zip' and can't find it. But even if it would correctly split it into two tokens it wouldn't work; second and following parameters are interpreted as specific files to unpack from the archive given as the first parameter. That way you can selectively unpack only the files you need from an archive. To unpack multiple archives you really do need a loop as you've done in post #7.

If you need to unpack multiple files in different places, you'd do something like
```

declare -a filenames=(the/first/file the/second/file the/'third and final'/file)
declare -a targetdirs=(one/directory/ another/directory/ and/a/final/directory)
for (( i=0 ; i<${#filenames
[*]} ; i++)) ; do 
  unzip ${filenames[i]} -d ${targetdirs[i]}
done

```

This might actually be useful if you have a dozen or so archives to unpack into as many different directories ...

Holger

---

### Post by wyattwhiteeagle on 2024-04-24
> **Holger_Gehrke said:**
> As I said, 'unzip' will unpack one file per call. By enclosing the list of files in quotes in post #6, you've turned it into one token. So now unzip looks for one file named '/home/wyatt/Desktop/Test-Folder-2/Image/Wyatts-Scripts.zip /home/wyatt/Desktop/Everything/Compressed/ZIP/Cheys-Place-GA.zip' and can't find it. But even if it would correctly split it into two tokens it wouldn't work; second and following parameters are interpreted as specific files to unpack from the archive given as the first parameter. That way you can selectively unpack only the files you need from an archive. To unpack multiple archives you really do need a loop as you've done in post #7.

If you need to unpack multiple files in different places, you'd do something like
```

declare -a filenames=(the/first/file the/second/file the/'third and final'/file)
declare -a targetdirs=(one/directory/ another/directory/ and/a/final/directory)
for (( i=0 ; i<${#filenames
[*]} ; i++)) ; do 
  unzip ${filenames[i]} -d ${targetdirs[i]}
done

```

This might actually be useful if you have a dozen or so archives to unpack into as many different directories ...

Holger
It appear's as though you were typing your reply while I was editing my post.
Anyhow, that too might be useful.
Again, thanks bunches :)

---

### Post by dragonfly41 on 2024-04-24
Not being an expert in bash scripts I take the easy route of Krusader double panel manager (similar to Double Commander). Although these tools do have a large footprint of dependencies.

Copy the zip(s) from ~/Downloads to target panel and just click to expand in its target.

There are additional features in Krusader Useractions.

---

### Post by Holger_Gehrke on 2024-04-24
So Krusader doesn't open archives ? That was always the big feature for me in midnight commander (mc, a dual pane file manager in the terminal). It treats archives as if they were directories - just hit enter on an archive and you can work with it's content.

Holger

---

### Post by dragonfly41 on 2024-04-24
Yes, as in Midnight Commander and Double Commander (and Total Commander in Windows) Krusader *does* open archives. By a click. The point I was trying to make (sorry to add after closed thread) was  that it is a powerful tool for managing workflows and "useractions" in toolbar offers even more options to customise workflows (e.g. run meld operations between panels, or backup). I just prefer UI rather than bash scripting. It is a personal choice and in Linux I know I am in the minority. Krusader is my "command hub". Another ingenious tool in my toolbox  is CherryTree which can contain rich text, images and importantly code blocks (in multiple languages - Bash, Python .. whatever .. your choice). This little tool has undocumented uses. Any number of operations can be added to code box (like Jupyter notebooks) -- such as rdiff-backup scripts, or pandoc. But I digress.

---

### Post by HermanAB on 2024-04-25
BTW, for future reference:  On UNIX systems, the way to execute a command on several files, without resorting to an error prone loop script, is with the find command.

Find can exec a command on each file it finds.  Read the man page or google “linux bash find” for examples. It is the easiest way.

---

### Post by dragonfly41 on 2024-04-25
Another workflow tip
I have Recoll installed.
I index every file in the desktop (first time takes some time, be patient).
Thereafter update index daily. File > Update
Now if I want to look for any MIME types (extensions such as zip) I run this query.   ext:zip  (list all extensions *.zip).  Other filters can be added to query. Hover cursor over query field to view cheat sheet.
Click on any *.zip filtered in Recoll GUI and there are various options to manage actions thereafter.
Recoll is another useful tool for the toolbox.

---

### Post by TheFu on 2024-04-25
> **HermanAB said:**
> BTW, for future reference:  On UNIX systems, the way to execute a command on several files, without resorting to an error prone loop script, is with the find command.

Find can exec a command on each file it finds.  Read the man page or google “linux bash find” for examples. It is the easiest way.

**find** and **xargs**

The manpages for both these commands are extensive, but sorta abstract.  Google for* Top 50 **find** examples* - to get some concrete examples.  **xargs** has some implied inputs based on the input list.  

Both tools are handy and have lots of options.  We just need to remember they are there and available.

---

