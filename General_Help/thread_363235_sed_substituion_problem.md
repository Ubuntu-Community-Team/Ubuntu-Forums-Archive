---
title: "sed substituion problem"
date: 2007-02-16
forum: General Help
---

### Post by Jahkel on 2007-02-16
Anybody got any ideas why the following simple sed command is giving me such trouble?  Its starting to drive me up the wall!  Thanks.

```

sudo sed `s/workgroup = MSHOME/workgroup = WORKGROUP/` /etc/samba/smb.conf
bash: s/workgroup = MSHOME/workgroup = WORKGROUP/: No such file or directory
sed: -e expression #1, char 19: unterminated `s' command

```

---

### Post by WW on 2007-02-16
Don't use single backquotes to enclose the command. Try double quotes.

---

### Post by Jahkel on 2007-02-16
I started out using forward single-quotes but I got the error

```
sed: -e expression #1, char 1: unknown command: `&#65533;'
```

Same goes for double quotes.  I thought I was getting somewhere with those backquotes, but obviously not.

---

### Post by Tesiph on 2007-02-16
Text between backquotes is executed as a shell command. Single and double quotes are different in the fact that variable names and escape characters are substituted in the latter.

Using single or double quotes should work, backquotes should not. Your command works fine here as well (replacing the backquotes by single quotes)

---

### Post by WW on 2007-02-16
This
> sed "s/AAA/BBB/" filename
will read filename, replace the first occurrence of AAA in each line with BBB, and print the line to the standard output.  (Try it on a test file.)  If you want to change the file instead of printing it, use the -i option:
> sed -i.backup "s/AAA/BBB/" filename
By putting .backup after the -i option, I am telling sed to make a copy of the unchanged file in filename.backup before changing filename.

I recommend that you test this a few times by working with an unimportant file (maybe make a copy of your .conf file in /tmp) before using it with sudo to change a file in /etc.

---

### Post by Jahkel on 2007-02-17
I dont know why, but this command totally doesn´t work for me, I get the error I mentioned above - even for the simple test bellow.  Searching the web seems to indicate that it doesnt work for some Ubuntuers as well, no particular reason given.  

```

$ echo hello > test.txt
$ sed ´s/hello/goodbye/´ test.txt
sed: -e expression #1, char 1: unknown command: `&#65533;'

```

Thanks for the replies though, its helping me learn the linux shell in my gradual transition from Windoze :)

---

### Post by highneko on 2007-02-17
You're still using the wrong quotes I think. Looks like it to me. Maybe your keyboard's doing this? Try these:
```
echo hello | sed "s/hello/goodbye/"
sed "s/hello/goodbye/"<<<"hello"
sed "s/hello/goodbye/" filename
```

---

### Post by Jahkel on 2007-02-17
Ah, its looks like my quotes are different to yours.  I tried your first example and it worked.  The size of your quotes are *ahem* bigger than mine, which seems to be a consequence of having the UK International keyboard selected (you have to hit quote twice to get a quote - albeit a useless quote it seems).  Switching to the UK standard keyboard seems to have fixed it.

Thanks.

---

