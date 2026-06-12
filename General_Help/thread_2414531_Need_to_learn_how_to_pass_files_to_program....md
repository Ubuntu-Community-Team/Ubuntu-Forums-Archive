---
title: "Need to learn how to pass files to program..."
date: 2019-03-11
forum: General Help
---

### Post by nzdreamer55 on 2019-03-11
Hello everyone,

I am learning bash scripting and have a program that I can run on a bunch of files from the CLI.  The problem is this program looks at a folder and will process all the files within the folder at one time.  If any of the files are broken, it will stop and not finish any of the processing so that none of the files get processed.  I would like to learn how to write a script to have each file processed in a series so that if one in bad, only that one time will fail and the rest of the files will be processed.

I am not sure what this is called or where to learn how to do it.  Any pointers would be helpful.

Thank you very much.

---

### Post by TheFu on 2019-03-12
```
#!/bin/bash

for filename in "$@"; do

   echo "

===[ $filename ]===
"
   
done
```

This reads space-separated values from all the command line arguments and processes them one at a time.  Perfect for normal Unix globbing methods.

Usage:
```
  ./script   *html t*l file.name.t
```

---

### Post by SeijiSensei on 2019-03-12
If you're processing only one type of file you can use

```

cd /path/to/some/directory

for f in *.html
do
    echo $f
done

```

To pass a file to a program use this:
```

cd /path/to/some/directory

for f in *.html
do
    /path/to/some/program < $f
done

```

That will "pipe" the contents of each file to the program.  You can capture output with "> /path/to/some/file".

---

### Post by TheFu on 2019-03-12
SeijiSensei, I thought there were warnings about using globbing such as this inside scripts?   [https://lwn.net/Articles/686789/](https://lwn.net/Articles/686789/) explains.  That link provides many exceptions where globbing doesn't do what is intended.

Of course, 99.999% of the time, it doesn't matter when all the input names are controlled by safe-users. Have at it.  And just to be extremely clear, my example above fails too.  I can think of all sorts of dangerous filenames that can wipe out everything in a HOME, if not everything on a system, if not correctly passed in.

---

### Post by sisco311 on 2019-03-12
Linux is very permissive with file names. We can't change that.

The bigger problem is that 99% of shell/bash tutorials and guides are full of bugs. Globs are very useful but you have to use them correctly:
```
for file in ./* 
do
    whatever "$file"
done
```

I'm not a beginner but every now and then I still have to check out BashFAQ and BashPitfalls (link in my sig) to get some idea what is the best and safest method to write a specific script.

---

### Post by SeijiSensei on 2019-03-13
I dunno.  I've used constructs like "for f in *" for years.  But I don't create filenames with embedded spaces or any of the other types of problems that can trip this up.  Usually I'm writing scripts that cycle over a known set of files with well-defined filenames.

---

### Post by TheFu on 2019-03-13
> **SeijiSensei said:**
> I dunno.  I've used constructs like "for f in *" for years.  But I don't create filenames with embedded spaces or any of the other types of problems that can trip this up.  Usually I'm writing scripts that cycle over a known set of files with well-defined filenames.

Me too, but I prefer the "$@" construct so it can be used as a filter.

I was doing some image processing yesterday where someone else's script (clearly, not mine!) left filenames like -020.jpg.  Hundreds of files.  As we all know, filenames starting with a '-' are problematic with almost every GNU utility.  Need to add '--' as the last option to all the remaining filenames, especially those beginning with '-' are handled correctly.

By using the "$@" method, I can process a few files, as a test, easily. If it works well, then the glob is relaxed to handle the rest of the files.

Just shows there are a multitude of ways to solve most problems on Unix systems.

BTW, there are subtle issues with trusting a chdir to work. If it doesn't, for any reason, then processing of the wrong files is likely.  I'd rather set a DIR=.... variable and use that in all the globbing and other file commands.  Much safer when running scripts from a crontab too.

Do I follow these recommendations every time?  Nope.
Have I been burned by no following them?  Yep.

Will I fix myself and always script following the best practices?  Probably not.
 ;)

---

