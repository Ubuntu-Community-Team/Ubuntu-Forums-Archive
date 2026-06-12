---
title: "Looping directory content and avoiding whitespace woes in BASH"
date: 2008-03-02
forum: General Help
---

### Post by jugisahunk on 2008-03-02
I have a pet BASH project that involves reading in the contents of a directory via command e.g. 'ls' 'pwd' 'dir' or some other.  Once  a directory's contents have been sent to standard out, I loop through them in a for loop.  Here's an example:

echo "create file" > myFile.txt

for FILE in $(pwd)/*
#
do
	echo "some text: '"$FILE"'" >> myFile.txt
done

I have two problems I haven't been able to solve.
1) How do I deal with whitespace in my FOR loop
2) How can I get just the name of file contents i.e. 'dirContent' instead of   
    '/home/myUser/dirContent'

I have tried using sed to filter out the absolute part of the path, but as it is said, "A man that tries to  solve a problem by using Regular Expressions will then have two problems to solve."

Suggestions?

---

### Post by lloyd_b on 2008-03-03
As for #2:

```
BASENAME=`basename "$FILE"`
echo "some text: '"$BASENAME"'" >> myFile.txt
```
The "basename" command strips the path, leaving just the base file name.

Exactly what problems are you having with "whitespace" - I tested your sample code in a directory that has files with spaces in the names, and didn't encounter any problems.

Lloyd B.

---

### Post by ghostdog74 on 2008-03-03
> **jugisahunk said:**
> 
I have two problems I haven't been able to solve.
1) How do I deal with whitespace in my FOR loop
 
you use shell expansion  and double quotes usually.
```

for file in *
do
 echo "$file"
done 

```
> 
2) How can I get just the name of file contents i.e. 'dirContent' instead of   
    '/home/myUser/dirContent'

basename command can be used, however for many many files that you parse, using bash internal string operations might be better
```

# a='/home/myUser/dirContent'
# echo ${a##*/}
dirContent

```

---

### Post by jugisahunk on 2008-03-03
Thanks, dog.  That method worked perfectly!  Props to you also for having a screename that allows such a snappy salutation.

---

### Post by ghostdog74 on 2008-03-03
> **jugisahunk said:**
> Thanks, dog.
its ghostdog ( the movie)

---

### Post by jugisahunk on 2008-03-03
Actually...it doesn't, not completely.  I am using each of the contents of a directory as the parameter in a 'cd' command.  

For example, the working directory is /home/user/ and it contains a subdirectory called 'My Directory':

1 for FILE in $(pwd)/*
2 #
3 do
4	BASENAME=`basename "$FILE"`
5	cd `basename "${BASENAME}"`
6	#do stuff in that directory
7
8        # return to starting directory
9	cd ../
10 done

I get a "line 9: cd: My: No such file or directory" error.  Thoughts?

---

### Post by lloyd_b on 2008-03-04
> **jugisahunk said:**
> Actually...it doesn't, not completely.  I am using each of the contents of a directory as the parameter in a 'cd' command.  

For example, the working directory is /home/user/ and it contains a subdirectory called 'My Directory':

1 for FILE in $(pwd)/*
2 #
3 do
4	BASENAME=`basename "$FILE"`
5	**cd `basename "${BASENAME}"`**
6	#do stuff in that directory
7
8        # return to starting directory
9	cd ../
10 done

I get a "line 9: cd: My: No such file or directory" error.  Thoughts?

The highlighted line above is the problem.  First off, you've already *got* the basename of the file in BASENAME.  There's no reason to run "basename" on it again.

Second - running "basename" again is eating the quotation marks, which makes the "cd" command go wacky:
```
cd `basename "My Directory"`
```
becomes
```
cd My Directory
```
without quotation marks.

What that line *should* be is
```
cd "$BASENAME"
```
which will translate to
```
cd "My Directory"
```

Lloyd B.

---

### Post by ghostdog74 on 2008-03-04
> **jugisahunk said:**
> Actually...it doesn't, not completely.  I am using each of the contents of a directory as the parameter in a 'cd' command.  

For example, the working directory is /home/user/ and it contains a subdirectory called 'My Directory':

1 for FILE in $(pwd)/*
2 #
3 do
4	BASENAME=`basename "$FILE"`
5	cd `basename "${BASENAME}"`
6	#do stuff in that directory
7
8        # return to starting directory
9	cd ../
10 done

I get a "line 9: cd: My: No such file or directory" error.  Thoughts?


i thought you already solved the thing. The reason you have the error, is because you did not check whether the FILE variable is a file or directory. you cannot "cd" to a file. 
use  [ -d $FILE ] to test whether its a directory, and if it is, then cd to it.

---

