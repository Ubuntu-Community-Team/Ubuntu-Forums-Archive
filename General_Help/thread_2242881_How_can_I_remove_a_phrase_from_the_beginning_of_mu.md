---
title: "How can I remove a phrase from the beginning of multiple file names?"
date: 2014-09-04
forum: General Help
---

### Post by stretch4 on 2014-09-04
I have a bunch of files, like this:

```

Example File 01 Mary.avi
Example File 02 Joe.avi
Example File 03 Brad.avi
Example File 04 Ryan.avi
...etc.
```

I want them to be:

```

01 Mary.avi
02 Joe.avi
03 Brad.avi
04 Ryan.avi
...etc.
```

How?

---

### Post by papibe on 2014-09-04
EDIT: I misunderstood th question. Answer edited. Thanks yancek.

Hi stretch4

You can use the command 'rename'.

To test your command, first run this on dry run mode (-n) so there's no risk of a mistake.
```
rename -vn 's/^Example //' *.avi
```
when you are sure you are making the correct changes, just remove the -n:
```
rename -v 's/^Example //' *.avi
```
What it does: it changes the expression 'Example ' that has to appear at the beggining of the file name (^), for nothing (string contain between // is an empty string).

Hope it helps. Let us know how it goes.
Regards

---

### Post by yancek on 2014-09-04
The code below would do it if all the files you want to change are in the same directory and you run the command in a terminal in that directory.  The reason I say "would" is because you have spaces in the current names and want to keep a space in the changed names.  I'd create a test directory and create a couple of test files with the old names and run it see what output you get. It might work if you put quotes around the whole thing as in the second example.

```
rename File "" File*
```

```
rename "File "" File*"
```

---

### Post by stretch4 on 2014-09-04
Adding 'File ' to your solution got the result I was looking for. Thank you!
```
Example File 01 Mary.avi  Example File 02 Joe.avi  Example File 03 Brad.avi  Example File 04 Ryan.avi
stretch@Xubuntu:~/test$ rename -vn 's/^Example //' *.avi
Example File 01 Mary.avi renamed as File 01 Mary.avi
Example File 02 Joe.avi renamed as File 02 Joe.avi
Example File 03 Brad.avi renamed as File 03 Brad.avi
Example File 04 Ryan.avi renamed as File 04 Ryan.avi
stretch@Xubuntu:~/test$ rename -vn 's/^Example File //' *.avi
Example File 01 Mary.avi renamed as 01 Mary.avi
Example File 02 Joe.avi renamed as 02 Joe.avi
Example File 03 Brad.avi renamed as 03 Brad.avi
Example File 04 Ryan.avi renamed as 04 Ryan.avi
stretch@Xubuntu:~/test$ 


```

---

### Post by yancek on 2014-09-04
```
rename File "" File*
```

I wasn't sure the above would work so I tested it and it worked as expected.

---

