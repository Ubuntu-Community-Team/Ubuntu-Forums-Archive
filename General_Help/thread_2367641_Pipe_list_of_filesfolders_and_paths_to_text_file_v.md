---
title: "Pipe list of files/folders and paths to text file via cron script?"
date: 2017-08-01
forum: General Help
---

### Post by 47_MasoN_47 on 2017-08-01
Is there a way to create a script that would dump a list of all the files/folders within a directory (/var/www/owncloud/data in this instance) to a text file?  I can do it with ls with a bunch of commands manually specifying subdirectories, but I don't want to have to manually edit the script every time we add/remove users to OwnCloud.  I'd like it to just automatically dump a list of all the files and folders inside each subdirectory.  We can do this on our Windows servers via powershell, so I'm sure there's a similar method available in Linux, I've just not been able to find it.

---

### Post by vocx on 2017-08-01
> **47_MasoN_47 said:**
> Is there a way to create a script that would dump a list of all the files/folders within a directory (/var/www/owncloud/data in this instance) to a text file?  I can do it with ls with a bunch of commands manually specifying subdirectories, but I don't want to have to manually edit the script every time we add/remove users to OwnCloud.  I'd like it to just automatically dump a list of all the files and folders inside each subdirectory.  We can do this on our Windows servers via powershell, so I'm sure there's a similar method available in Linux, I've just not been able to find it.
I would do it with the "find" program.
```

find /var/www/owncloud/data > text_file

```

---

### Post by 47_MasoN_47 on 2017-08-01
That gets me part of the way there, I forgot to mention that I also need the last modified date along with the list.

Thanks

---

### Post by vocx on 2017-08-01
> **47_MasoN_47 said:**
> That gets me part of the way there, I forgot to mention that I also need the last modified date along with the list.

Thanks
You can execute a command for each file with "find".
```

find /boot -exec stat -c '%n %y' '{}' ';' > text_file

```

If you know what command exactly produces the output you want, for example, "ls" and some options, you can include it in the part after "-exec".
```

find /boot -exec [custom command to run] ';' > text_file

```

The command is terminated by a semicolon, that needs to be escaped with single quotes or with the backslash. The file found is represented by the empty braces '{}', and is also escaped by the quotes.
```

find /boot -exec [custom command to run on this '{}' file ] \; > text_file

# Run the "stat" command and some options on each file
find /boot -exec stat -c '%n %Y' '{}' \; > text_file

```

If you are doing system stuff, it would be good if you learn a bit about Bash, which would be equivalent to the Powershell, I think. The individual utilities such as "find", "grep", "stat", "ps", "ls", etc. have their own options, so you need to read their manuals to fully understand what they do. Bash itself provides only the syntax of the command line, such as defining variables, escaping characters, expanding variables, double and single quotes, filename expansion using the asterisk "filename*", piping with |, and other control structures such as if-then-else, and defining functions. [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

Remember to use the full path of the programs that you use in cron. This is because cron usually resets the PATH variable, and thus if you try to run a program it may be not available in the limited PATH established by cron. That is, if you run "my_program some_file", you better write this as "/home/user/bin/my_program some_file".

---

### Post by papibe on 2017-08-01
Hi 47_MasoN_47.

If you need to record the date the list was created, you can use this:
```
find /var/www/owncloud/data > "/path/to/list.txt.$(date +%F-%T)"
```
If you need to save last modification date for each file you simple could do:
```
ls -lR /var/www/owncloud/data >  /path/to/list.txt
```
or this:
```
find /var/www/owncloud/data -printf "%T+ %p\n" > /path/to/list.txt
```
Does that help?
Let us know how it goes.
Regards.

---

