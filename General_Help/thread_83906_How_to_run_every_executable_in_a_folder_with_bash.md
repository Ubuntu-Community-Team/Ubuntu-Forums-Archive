---
title: "How to run every executable in a folder with bash?"
date: 2005-10-29
forum: General Help
---

### Post by One Quick Question on 2005-10-29
N00b-ish question:  How do you run every executable in a folder with bash?
Apparently $./* doesn't work.

---

### Post by adwait on 2005-10-29
Don't really know any direct method to do this.....
```
ls /folder/containing/sciprts >> <file>
awk '{print "./ "$1" "}' <file> > <file2>
chmod +x <file2>
./<file2>

```

What this does is, it puts you entire list of files in a file. The second line prefixed every line in that file with a "./" and puts that in a new file. The third line makes that file executable. The last one executes that file, which will in turn execute all the files in that folder.

---

### Post by doclivingston on 2005-10-29
[QUOTE=One Quick Question]N00b-ish question:  How do you run every executable in a folder with bash?
Apparently $./* doesn't work.[/QUOTE]

Assume that you have a directory containing "foo", "bar" and "baz". Bash will expand that to "./bar ./baz ./foo", which will run ./bar, passing the other two as parameters.

Try ```
find . -maxdepth 1 -exec bash '{}' \;
``` which says to find everything in the current directory (but not subdirectories), and then execute "bash file-name". For a better explanation, see the manpage for find.

---

### Post by One Quick Question on 2005-10-30
Hmm.  Doclivingston, I like that idea.
After some dissecting of my own, I also came up with this solution:
```
for f in *; do $f; done;
```   I can't decide which I like better...

---

### Post by NewbieNik on 2005-10-30
[QUOTE=One Quick Question]Hmm.  Doclivingston, I like that idea.
After some dissecting of my own, I also came up with this solution:
```
for f in *; do $f; done;
```   I can't decide which I like better...[/QUOTE]


Am i the only one in saying...what?????
Is this the only way we can do multiple executes? Is there not a way of highlighting all the files then saying "open".
Can I not use my Linux magic-wand? where was Gandolff when I bought this thing? Can I get my money back from those double-dealing ogre boys? shucks....

In all seriousness, there must be an easier way though, right?

---

### Post by doclivingston on 2005-10-30
[QUOTE=One Quick Question]Hmm.  Doclivingston, I like that idea.
After some dissecting of my own, I also came up with this solution:
```
for f in *; do $f; done;
```   I can't decide which I like better...[/QUOTE]

That will work, as long as none of the files have a space in their name. "For" breaks along spaces, so it will treat a file called "Some File" as two called "Some" and "File".

---

### Post by jazzer on 2005-11-01
Try this little script I just wrote:

```
#!/bin/sh
work_dir=$(echo $NAUTILUS_SCRIPT_CURRENT_URI| sed 's/file:\/\///g');
for file in $work_dir/*; do
	if [ -x "$file" ]; then
		$file;
	fi
done
```

Copy and paste that into your favourite text editor and save this under your ~/.gnome2/nautilus-scripts folder.  Name it whatever you like (I called mine 'Run all applications').    Now when you are browsing with nautilus you can go to:

File->Scripts->Run all applications.

Do note it doesn't run them all at once, it runs them one after the other.

(edit: if you would like to run them all simunataneously instead of one after the other change the line after the if statement:
```

      $file;  (original line)
      $file & (changed line)
```

The & sign will detach the process from the script and move on to the next executable)


doclivingston,

for f in *; do $f; done;

This will work if you wrap $f with quotes...  As my example above would show.  This is all I am doing in my example except for making it work with nautilus and check if the file is executable first before executing.

---

