---
title: "script to convert rmvb to avi ( more files )"
date: 2014-01-10
forum: General Help
---

### Post by daanenjuul on 2014-01-10
Can please someone help me? :confused:. I've got a big list of .rmvb files and i want to convert these files to .avi

I found this command and it works very good:

mencoder <input_movie> -oac mp3lame -ovc lavc -o output_movie.avi

But, i can only use this command for 1 .rmvb file

Does anyone has an idea or example for me to make an (bash? or something else) script to convert the whole list of .rmvb files to .avi files? 
And that the script put the converted .avi files in a other directory.

I´ve tried to search with several keywords for an example, but no result. ( maby wrong keywords? hahah )

---

### Post by sjackling on 2014-01-10
I only have experience with python 2.7 but I have seen that bash uses a for loop too... im sure theres a way to use it to make a loop for it to perform that operation on each file in the list... Sorry i cant be more specific i plan to start teaching myself bash shortly

---

### Post by daanenjuul on 2014-01-10
no problem thanks for the reaction

---

### Post by steeldriver on 2014-01-10
What do you mean by a list? do you have the names in a file? or do you just want to convert all the .rmvb files in a particular directory? or in multiple directories? What do you wan the output names to be?

You could do something like

```

for **file **in *.rmvb; do
  mencoder **"$file"** -oac mp3lame -ovc lavc -o **"path/to/otherdir/${file%.rmvb}.avi"**
done

```
which will convert all the files in the current directory, naming the output files the same as the input files apart from the new suffix

---

