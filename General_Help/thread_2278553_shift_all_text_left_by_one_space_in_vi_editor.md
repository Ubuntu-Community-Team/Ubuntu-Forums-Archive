---
title: "shift all text left by one space in vi editor"
date: 2015-05-17
forum: General Help
---

### Post by IAMTubby on 2015-05-17
Hello,
 I would like to shift all my text left one space in vi.

 So a line starting at the second column in the editor would now start from the first column, line starting at the third column would start from the second column and so on.

 I have selecting text and doing the following

 ```

Vjjjj:le 0
 
```

But this just shifts all of my text to start from the first column immaterial of the indentation I had previously.

Thanks.

---

### Post by SeijiSensei on 2015-05-17
Must you do this in vi?  Here's a simple solution with sed:
```
sed 's/^/ /g' < input_file > output_file
```
The carat "^" denotes the beginning of a line in regular expressions.  Sed simply replaces that with a space.

Whoops, I see you want to do the opposite. The command above shifts the text to the right.  To shift to the left is trickier unless all the lines start with a space.  Assuming that, you can use 
```
sed 's/^ //g' < input > output
```
That will strip the leading space from any line that has one.

---

