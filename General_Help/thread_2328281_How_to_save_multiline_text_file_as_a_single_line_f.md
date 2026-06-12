---
title: "How to save multiline text file as a single line file with embedded newline '\n'"
date: 2016-06-19
forum: General Help
---

### Post by suaro on 2016-06-19
I hope I can word my question correctly :) 

I have a text file that looks like this when I open it in an editor.
(partial snippet)

--------- start ----

# Location of pig log file. If blank, a file with a timestamped slug
# ('pig_1399336559369.log') will be generated in the current working directory.
#
# pig.logfile=
pig.logfile=/tmp/pig-err.log

# Log4j configuration file. Set at runtime with the -4 parameter. The source
# distribution has a ./conf/log4j.properties.template file you can rename and
# customize.
#
# log4jconf=./conf/log4j.properties


---- end -----

But I need to save this file with the newline '\n' actually embedded in the file itself. I need it saved as the literal '\n' 

In other words I need to save the file so it looks like this:


# Location of pig log file. If blank, a file with a timestamped slug[COLOR=#ff0000]\n[/COLOR]# ('pig_1399336559369.log') will be generated in the current working directory.\n#\n# pig.logfile=[COLOR=#ff0000]\n[/COLOR]# pig.logfile=/tmp/pig-err.log[COLOR=#ff0000]\n\n[/COLOR]# Log4j configuration file. Set at runtime with the -4 parameter. The source[COLOR=#ff0000]\n[/COLOR]# distribution has a ./conf/log4j.properties.template file you can rename and\n# customize.[COLOR=#ff0000]\n[/COLOR]#[COLOR=#ff0000]\n[/COLOR]# log4jconf=./conf/log4j.properties[COLOR=#ff0000]\n\n[/COLOR]


Above the newlines are not interpreted as an actual newline. The text has \n to designate the newline and everything above is actually contained on a single line. 

I hope this makes sense.   I was going to try to create a program that could read the original text file and replace the newline with the literal ->  '\n'  but was thinking there might be an intrinsic way of doing this .

Any tips greatly appreciated.

---

### Post by steeldriver on 2016-06-19
Try

```

sed -e :a -e '$!N; s/\n/\\n/; ta' oldfile > newfile

```

---

### Post by TheFu on 2016-06-19
The newline is in there, so you can just do a search and replace using any regex tool that you like.
sed
gedit
vim
perl
awk
python
take your pick. Must be 100-1000 more.  The key is using regex. [http://ubuntuforums.org/showthread.php?t=818748](http://ubuntuforums.org/showthread.php?t=818748) Regex is a powerful language designed for pattern matching. As a programmer, it is very important to learn.

with sed, I'd do
[B]sed -e 's/$/\\\n/' < /path-to-file/input.txt >  /path-to-file/output.txt 
[/B]
I didn't test this result, but would be shocked if it didn't work.  sed is a "stream editor", hence the need to redirect stdin and stdout to/from files.

---

### Post by HermanAB on 2016-06-19
dos2unix

---

