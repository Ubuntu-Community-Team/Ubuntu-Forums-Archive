---
title: "Command line and copying files"
date: 2015-07-12
forum: General Help
---

### Post by jaquesaulait on 2015-07-12
Hi community,
  I've been trying to use the CLI to copy files, it's not working as I'd expect.  Here's what I've been trying:
* Here's the folder contents:*
CLIdir  clifileA  clifileB  Greek alphs  Nano test 

Here's what did work:
cp clifileA clifileB

... giving me the expected copy, clifileB.  Here's what will not work:
cp Nano\ test\  Nano test 2

The back slashes are placed there by the system when I use the Tab key to autocomplete the file name.  I tried:
cp Nano\ test\  Nano \test \2

... by manually inserting the back slashes in my intended copied file name, but that didn't work.  All I keep getting is:
cp: target `2' is not a directory

...except when I tried:
cp Nano\ test\  Nanotest2

which worked:
CLIdir  clifileA  clifileB  Greek alphs  Nano test   Nanotest2

So is the system unable to make copies of files with more than 1 word in the new file name?  Does anybody know how I make a new copied file with more than 1 word in the name?

Thanks.


Jack.

---

### Post by dino99 on 2015-07-12
all the 'copy' commands
[http://www.die.net/search/?q=copy&sa=Search&ie=ISO-8859-1&cx=partner-pub-5823754184406795%3A54htp1rtx5u&cof=FORID%3A9](http://www.die.net/search/?q=copy&sa=Search&ie=ISO-8859-1&cx=partner-pub-5823754184406795%3A54htp1rtx5u&cof=FORID%3A9)

---

### Post by tyler.maxwell on 2015-07-12
Well, the backslash \ is for escaping a character , in this case a space. That means that if you file has a space in its name, for example "Nano test", terminal would complete it like this:
```
Nano\ test
```
so that the space is correctly associated with the filename, and not interpreted as a space on the command to separate the command arguments.
So this line is mostly likely incorrect:
```
cp Nano\ test\ Nano \test \2
```
because it will be interpreted like this:
```
cp "Nano test Nano" "    est" "\2"
```
the spaces before " est" being a tab (\t is interpreted as tab).

Topy files within directories, use the slash ( / ) to separate subdirectories in the path, and if you need to copy entire directories, use the cp -r (as in recursive copy).

For example, to copy file test1 from Nano subdirectory to a file name test2 into the Micro subdirectory you'd use:
```
cp Nano/test1 Micro/test2
```

---

### Post by jaquesaulait on 2015-07-12
Dino,
  Thanks for the info, useful, but I couldn't find the answer to my question.  Thanks anyway.

Jack.

---

### Post by jaquesaulait on 2015-07-12
Tyler,
  Thanks for the info ... but it doesn't answer my question.  I'm simply trying to copy files within the same directory.

Jack.

---

### Post by tyler.maxwell on 2015-07-12
Within the same directory just skip the dir name in the path; and you can use quotes for file names.
For instance, if you want to copy the file "Nano test" to a "Nano test 2" you might use
```
cp "Nano test" "Nano test 2"
```
This way you don't get mixed up with space in the filenames.

The escaped version would be
```
cp Nano\ test Nano\ test \2
```

---

### Post by steeldriver on 2015-07-12
@tyler.maxwell you are still escaping the final 2 rather than the space

```

cp Nano\ test Nano\ test[COLOR=#ff0000]**\**[/COLOR] 2
________^____ _____^_____^_

```

---

### Post by jaquesaulait on 2015-07-12
Tyler,
  "That seems to have done the trick"!   Thanks very much.

Regards.    Jack.

---

