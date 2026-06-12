---
title: "Help w/ sed parsing special characters"
date: 2007-08-31
forum: General Help
---

### Post by clem_c_rock on 2007-08-31
Hello,

    I'm trying to change the image paths in a directory of files.

 My first question is that I'm trying to use this line to test the change in one file:


sed -e 's/images/http://cache.somewebsite.com/images' ajax_scaffold.css

When I try that I get this:

sed: 1: "s/images/http://cache.r ...": bad flag in substitute command: '/'

I did a test by running this:

sed -e 's/images/duh/' ajax_scaffold.css

and the output said the changes had worked but when I went to the actual file, the changes didn't show?


Also, when I find a command that works, is it possible to specify a directory

and run this command on every file w/in the directory?

---

### Post by lloyd_b on 2007-08-31
> **clem_c_rock said:**
> Hello,

    I'm trying to change the image paths in a directory of files.

 My first question is that I'm trying to use this line to test the change in one file:


sed -e 's/images/http://cache.somewebsite.com/images' ajax_scaffold.css

When I try that I get this:

sed: 1: "s/images/http://cache.r ...": bad flag in substitute command: '/'

I did a test by running this:

sed -e 's/images/duh/' ajax_scaffold.css

and the output said the changes had worked but when I went to the actual file, the changes didn't show?


Also, when I find a command that works, is it possible to specify a directory

and run this command on every file w/in the directory?

1. Try "escaping" the slashes with backslashes:
[SIZE="4"]```
sed -e 's/images/http:\/\/cache.somewebsite.com\/images/' ajax_scaffold.css
```[/SIZE]

2. sed sends its output to stdout (i.e. the screen).  If you want to save it to a file, you need to redirect it:
```
sed -e 's/images/duh/' ajax_scaffold.css > new_scaffold.css
```
Note: do NOT try redirecting it back to the input file (you'll wind up clearing the file!).  Redirect it to a new file, and then copy it to the old file name (I strongly recommend making a backup first, anyway).
 
3.  To process an entire directory, you'll need a simple shell script.  Note that for my example script, you'll need to be in the directory with the files (processing a directory name on the command line is possible, but a little more work, and I'm lazy).
```
#!/bin/bash

for CURFILE in *; do
     sed -e 's/images/http:\/\/cache.somewebsite.com\/images/' $CURFILE > tmpfile
     cp tmpfile $CURFILE
done 
rm tmpfile
```

Lloyd B.

---

### Post by aJayRoo on 2007-08-31
Okay, first of all sed will not change the contents of the file it is working on, that is the way it is designed. I find the best way of using sed is like this:
```
sed 'expression' filename > output_filename
```
This will perform the sed operation on the file 'filename' and the output will be written to the file 'output_filename'.

Now onto your example, you are using substitution which takes this form:
```
s/old/new/
```
The use of forward slash in this operation means that when you want to include a forward slash it must be escaped using the backslash character, meaning you substitution would become:
```
s/images/http:\/\/cache\.somewebsite\.com\/images/
```
Notice how the '.' chracter must also be escaped as it has a special meaning. Also notice the forward slash at the end of the expression, this tells sed that your substitution has ended. It is important as it is possible to specify options after this point which you may want to do. The substitution:
```
s/old/new/g
```
for example is especially useful as it will replace not only the first occurrence of 'old' with 'new' but every occurrence on each line.

Putting this all together gives us the following command:
```
sed -e 's/images/http:\/\/cache\.somewebsite\.com\/images/g' ajax_scaffold.css > ajax_scaffold.css.new
```
You can then check that the new file is what you expected and if confident you may replace the original with it (making a backup first is recommended as always).

As for performing the operation on a directory of files, this is probably possible but the output would end up in one file. It would be better to use shell scripting to repeat the command for every file in a directory sending output to separate files as in:
```
for file in *; do
    sed -e 's/images/http:\/\/cache\.somewebsite\.com\/images/g' "$file" > "${file}.sub"
done
```

Hope that helps!

EDIT: Wow I was just beaten to it!

---

### Post by clem_c_rock on 2007-08-31
Thanks - this is a wealth of information - THANKS

---

### Post by ninehrcoma on 2007-08-31
Just for reference, sed will indeed change the file that it is working on if you want it to. Perl one-liner fans will know the -i flag for edit in place. Well, sed now has that also.

```
sed -i 's/oldone/newone/g' filename
```

---

### Post by bodhi.zazen on 2007-08-31
> **ninehrcoma said:**
> Just for reference, sed will indeed change the file that it is working on if you want it to. Perl one-liner fans will know the -i flag for edit in place. Well, sed now has that also.

```
sed -i 's/oldone/newone/g' filename
```

+1 on that (I was going to post that information :twisted:)

OK, my meager tip is you do not have to use / as a deliniator in your expression. I use _ as it it easire for me to read :

sed -i -e 's_old_new_g' old > new

---

### Post by clem_c_rock on 2007-09-06
hello, and thanks for your help.


this is the solution that worked for me:

```

for file in *; do
    sed -e 's/\/images/http:\/\/cache\.reverbnation\.com\/images/g' "$file" > "${file}.sub"
    rm "$file"
    mv "${file}.sub" "${file}"
done

```

---

### Post by bogolisk on 2007-09-06
> **clem_c_rock said:**
> hello, and thanks for your help.


this is the solution that worked for me:

```

for file in *; do
    sed -e 's/\/images/http:\/\/cache\.reverbnation\.com\/images/g' "$file" > "${file}.sub"
    rm "$file"
    mv "${file}.sub" "${file}"
done

```

good! but you should really look at bodhi.zazen's post. No sed user would quote the slash.

---

