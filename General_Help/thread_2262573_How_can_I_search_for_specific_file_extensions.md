---
title: "How can I search for specific file extensions?"
date: 2015-01-25
forum: General Help
---

### Post by can5 on 2015-01-25
I want to search for some file extensions in a folder except for .zip .rar .txt etc...

Can I do this using terminal or is there a software which I could do this?

---

### Post by mooreted on 2015-01-25
If you want to search in the current directory:

find . -iname *.rar

You can search other directories from the current directory:

find /home/mooreted -iname *.rar

[http://www.binarytides.com/linux-find-command-examples/](http://www.binarytides.com/linux-find-command-examples/)

---

### Post by can5 on 2015-01-25
Thank you for your reply. I couldn't explain it correctly. I want to find files "except for" zip rar txt and others.

---

### Post by can5 on 2015-01-25
I think it's invert match in here: [http://www.binarytides.com/linux-find-command-examples/](http://www.binarytides.com/linux-find-command-examples/)

---

### Post by HermanAB on 2015-01-25
Maybe this?
$ find . -type f \( -iname "*" ! -iname "*.zip" \)

---

### Post by mooreted on 2015-01-25
Interesting, never tried that.

---

### Post by kjohri on 2015-01-25
Suppose you want to find all files with names containing the string "hello" but skip files with extension "o" and "php",

```
find . -name "*hello*" | egrep -v "(o$)|(php$)"
```

---

### Post by sisco311 on 2015-01-26
@[COLOR=#000000]HermanAB

For better performance you should put the type test after the iname test.

```
find ./ ! -iname '*.zip' -type f
```

@OP

There are many ways for doing this in the CLI. For example in bash you can use extglobs ([/COLOR][http://mywiki.wooledge.org/glob](http://mywiki.wooledge.org/glob)):
```
shopt -s extglob
echo !(*.txt|*.zip)

```


You can use extended regular expressions in GNU/find ([http://mywiki.wooledge.org/UsingFind](http://mywiki.wooledge.org/UsingFind))
```

find ./ -regextype posix-extended ! -regex '.*\.(zip|txt|rar)' -type f
```

Depending on what do you want to do with the files we can help you with finding the best solution for you.

EDIT:
@kjohri
What if  the filename contains a newline?
```

[sisco@acme foo]$ > "hello01.o
> world"
[sisco@acme foo]$ find . -name "*hello*" | egrep -v "(o$)|(php$)"
world

```

---

### Post by can5 on 2015-01-29
thanks for the replies. this is quite enough but I wonder if I could delete or move the files found. this is my code:

```
find . -type f \( -iname "*" ! -iname "*.zip" \) \( -iname "*" ! -iname  "*.jpg" \) \( -iname "*" ! -iname "*.mp3" \) \( -iname "*" ! -iname  "*.mp4" \) \( -iname "*" ! -iname "*.bmp" \) \( -iname "*" ! -iname  "*.rar" \) \( -iname "*" ! -iname "*.avi" \) \( -iname "*" ! -iname  "*.m4v" \) \( -iname "*" ! -iname "*.png" \) \( -iname "*" ! -iname  "*.m4a" \) \( -iname "*" ! -iname "*.mov" \) \( -iname "*" ! -iname  "*.3gp" \) \( -iname "*" ! -iname "*.wav" \) \( -iname "*" ! -iname  "*.AVI" \) \( -iname "*" ! -iname "*.txt" \) \( -iname "*" ! -iname  "*.srt" \) \( -iname "*" ! -iname "*.mkv" \) \( -iname "*" ! -iname  "*.gif" \) \( -iname "*" ! -iname "*.MPG" \) \( -iname "*" ! -iname  "*.htm" \) \( -iname "*" ! -iname "*.html" \) \( -iname "*" ! -iname  "*.wma" \) \( -iname "*" ! -iname "*.flv" \) \( -iname "*" ! -iname  "*.doc" \) \( -iname "*" ! -iname "*.docx" \) \( -iname "*" ! -iname  "*.xls" \) \( -iname "*" ! -iname "*.xlsx" \) \( -iname "*" ! -iname  "*.ppt" \) \( -iname "*" ! -iname "*.pptx" \) \( -iname "*" ! -iname  "*.mpeg" \)
```

---

### Post by sisco311 on 2015-01-29
Your find command looks a bit overcomplicated, but if it works for you and you don't plan to use it regularly or use it in a script, then it's okay. 

GNU/find has a -delete action which you can use to delete the matched files. You must place it at the end of your command. Putting -delete first will make find try to delete everything below the starting points you specified.

In order to move the files you can use find's -exec action with the mv command. Just make sure that the destination directory exists. 

```
mkdir -p path/to/dest &&
find ./ ! -iname '*.zip' ! -iname '*.jpg' -type f -exec mv --verbose --backup=numbered -t path/to/dest -- '{}' \+
```

You have to replace path/to/dest with the actual path to the destination directory which shouldn't be a sub-directory of the dir where the files are located.

Test the commands before you use them and it's always a wise idea to create a backup of your original files.

---

### Post by Holger_Gehrke on 2015-01-29
> **can5 said:**
> thanks for the replies. this is quite enough but I wonder if I could delete or move the files found. 

A bit shorter:
```

find . -type f \( \! -iname "*.zip" \! -iname "*.jpg" \! -iname "*.mp3" \! -iname "*.mp4" \! -iname "*.bmp" \! -iname "*.rar" \! -iname "*.avi" \
 \! -iname "*.m4v" \! -iname "*.png" \! -iname "*.m4a" \! -iname "*.mov" \! -iname "*.3gp" \! -iname "*.wav" \! -iname "*.txt" \! -iname "*.srt" \
 \! -iname "*.mkv" \! -iname "*.gif" \! -iname "*.MPG" \! -iname "*.htm" \! -iname "*.html" \! -iname "*.wma" \! -iname "*.flv" \
\! -iname "*.doc" \! -iname "*.docx" \! -iname "*.xls" \! -iname "*.xlsx" \! -iname "*.ppt" \! -iname "*.pptx" \! -iname "*.mpeg" \) 

```

All those "-iname '*'" aren't necessary; the '!' should be escaped, because the symbol also has a meaning for the shell; you had some additional capitalized variants in there, which aren't needed since the '-iname' test is case-**i**nsensitive.

To delete the found files, just append '-delete' at the end of the command. But run it without that first and **check carefully** that it really **only** lists the files you **want** to delete. 

For convenience, piping this command through 'less' might be a good idea (append "| less" after the command, less is a program for viewing text, hit the 'q'-key to exit it once you're done); if you do so, be aware that it will take a moment until you see the results of your search and the search continues in the background; so if you hit 'end' on the keyboard to jump to the end of the text, you'll have to wait until 'find' is completely done.

---

