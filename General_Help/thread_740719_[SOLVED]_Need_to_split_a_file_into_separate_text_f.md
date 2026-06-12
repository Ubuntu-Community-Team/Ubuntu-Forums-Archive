---
title: "[SOLVED] Need to split a file into separate text files, one for each line"
date: 2008-03-31
forum: General Help
---

### Post by MountainX on 2008-03-31
I have a delimited text file. I want to create one new text file for each line (i.e., where the content of each new file is one line from the original file).

I want to name the new text file based on the first "word" on that line where the word is all the characters up to the delimiter. (I may have to check for chars that aren't valid for file names.) That word will also be included in the content in the file.

It would be really nice if I could turn each delimiter into a newline char in the new file.

I have a default installation of Ubuntu and I would like to do this without downloading any new development tools. I don't know what I have available in Ubuntu (I'm a newbie), but I'd like to use the easiest and most simple method for doing this task. I wouldn't mind learning how to write a shell script. Or I could use C, Java, or some other C-family language...

Can anyone offer me some help on this task? Thanks

BTW, this isn't homework or anything. It is just a task I need to do for myself.

---

### Post by monraaf on 2008-03-31
This is fairly easy to do in python.

```

#!/usr/bin/env python
infile = open('/etc/passwd','r')
for line in infile:
    words = line.replace(':','\n')
    ofile = open(words.partition('\n')[0],'w')
    ofile.write(words)
    ofile.close()
infile.close()

``` 

Just replace /etc/passwd with your filename and replace : with your delimiter.
I've omitted error checking, but you get the basic idea.

---

### Post by MountainX on 2008-03-31
Thank you very much! :)

How do I run it?
I made it executable. Do I have to type python <filename> or is there a way I make it run by double clicking on it? Thanks

---

### Post by sekinto on 2008-03-31
Well if you want to make it run by clicking something you could make a .sh file like this:

> #!/bin/sh
python "[YOUR FILE].py"
echo "

And then make the .sh file executable.

---

### Post by jespdj on 2008-03-31
If you've made it executable, you should be able to run it in a terminal window like this:
```
./program.py
```
(where 'program.py' is ofcourse the filename of the Python program).

---

### Post by MountainX on 2008-03-31
This works great!!!

---

### Post by ad_267 on 2008-03-31
Yup, the first line tells your computer how to execute the script, so you just execute it by changing into the right directory and ./yourscript
```
#!/usr/bin/env python
```
The #! is called a shebang :)

---

### Post by ad_267 on 2008-03-31
Actually while we're sort of on this topic, one thing I have seen before and wondered about is why people use "#!/usr/bin/env python", and not "#!/usr/bin/python" which also works?

Edit: Don't worry, Wikipedia answerd my question. For anyone else who wants to know, env just locates the interpreter using the PATH variable so is useful if someone has python in a different directory.

---

