---
title: "[SOLVED] extracting data from multiple xml files into txt"
date: 2013-03-04
forum: General Help
---

### Post by clementeb on 2013-03-04
Hello,

I am trying to make one word-list (unicode txt) extracting entries from a series of xml files.
What would be the best software that can accomplish the task?
And what should I do?
I have never tried doing something similar, so I am a bit lost, but I am very willing to learn[IMG]https://lqo-thequestionsnetw.netdna-ssl.com/questions/images/smilies/smile.gif[/IMG]
All the best to all of you,
Cheers,

Clemens
P.s. just in case, here is a zip file withthe xml files
[http://dfiles.eu/files/wd92zyffr](http://dfiles.eu/files/wd92zyffr)
I am trying to extract only what's in between the <hdwd> </hdwd> tags.
Cheers

---

### Post by zero2xiii on 2013-03-04
Hay,

I would suggest writing a bash script for the task.

Using the following:
html2text
sed

maybe awk and grep. Some "cut" might also be needed.

I will slap something together real quick and try and comment as much as possible.

Just note that I am by no means a "qualified scriptor". So please do not take my scripts as the bible of scripting hehehe... :oops:

Philip

---

### Post by zero2xiii on 2013-03-04
Solution option:
```
echo "please enter path of file to parse, relative to current directory:"
echo $(pwd)
read file
cat $file | grep "<hdwd>" |sed -e 's_<hdwd>__g' -e 's_</hdwd>__g' -e '/^<entry/d' > $file.parsed
cat $file.parsed
echo "Parsed file can be found at:"
echo $file.parsed
```

Explanation:
```
echo "please enter path of file to parse, relative to current directory:"
echo $(pwd)
read file
```
This simply asks the user to type the path to the file,
$(pwd) is the environmental variable that refer to the current working directory,
This line simply reads the user input and stores it in the variable "file"

```
cat $file | grep "<hdwd>" |sed -e 's_<hdwd>__g' -e 's_</hdwd>__g' -e '/^<entry/d' > $file.parsed
```
Broken down:
```
cat $file
```
This simply opens the file and redirects its output to the pipe (standard out get piped to the next command by the pipe character "|")
```
grep "<hdwd>"
```
This command searches for and prints (to standard out) all lines containing "<hdwd>" and then gets piped again to the next command
```
|sed -e 's_<hdwd>__g' -e 's_</hdwd>__g' -e '/^<entry/d'
```
This is the most difficult part. Sed is here used to do 3 things in sequence to the standard input received from grep:
1. <hdwd> gets replaced by nothing (deleted basically)
2. </hdwd> gets replaced by nothing (deleted basically)
3. all remaining lines starting with "<entry" gets deleted. This is one thing I noticed that remains after doing grep. Not sure why, but this removes the issue.
 ```
> $file.parsed
```
This simply redirects standard output to a file with the appended ".parsed" file name.
```
cat $file.parsed
echo "Parsed file can be found at:"
echo $file.parsed
```
This simply outputs the parsed file to the terminal,
And lets the user know where to find the newly created file.

I hope this helps. Will include a new post with a script to parse all files in a directory.

Good luck

---

### Post by zero2xiii on 2013-03-04
Possible Solution two:
```
echo "please enter path of folder to parse, relative to current directory:"
echo $(pwd)
read folder
mkdir $folder/parsed
for file in $folder/*.xml
	do
		cat $file | grep "<hdwd>" |sed -e 's_<hdwd>__g' -e 's_</hdwd>__g' -e '/^<entry/d' > $file.parsed
		#cat $file.parsed
		#echo "Parsed file can be found at:"
		mv $folder/*.parsed $folder/parsed
		echo "$file Parsed"
	done
echo "Parsed file can be found at:"
echo "$folder/parsed"
```

This is EXACTLY as the above. It just loops through all the files in the folder and prints the parsed file destination to terminal.
However it copies the parsed files to a subdirectory called "parsed".


To use any of the above scripts simply create an empty document and paste to code in it.
Rename the file to a .sh extention.
In terminal run: (assuming file name is "extractor.sh")
```
cd ./path/to/file
chmod +x ./extractor.sh
./extractor.sh
```

and then follow the on screen instructions.

Hope this is clear. I tried being as clear as I could without being to daft about it.

Sorry about all the separate posts moderators. Just trying to keep things as little confusing as possible for OP.

Good luck :)

---

### Post by clementeb on 2013-03-08
Wow!!
Thank you very much for the very clear and detailed explanation. I will try it right away.
All the best,

Clemens :)

---

### Post by zero2xiii on 2013-03-10
Hay,

Very much welcome :)

If it solves your problem, please remember to mark your thread as solved.

Philip

---

### Post by clementeb on 2013-03-11
Thank you very very much,
your solutions worked wonderfully. I have just one last question that shows what a newbie  I am.
I now have got the parsed files in the parsed folder within the original files folder. I was wondering how to "unite" their content into just one long file with all the terms contained in the individual parsed files together.
Thanks,

Clemens

---

### Post by zero2xiii on 2013-03-11
Hay,

Sorry I completely forgot about that :oops:.

After everything is done you can simply do this in terminal:
```
cd /directory/of/files/parsed
for file in "./*.parsed"; do cat "$file" >>"combined.txt"; done
```

This simply runs the command "cat $file" on every file in the directory, but instead of printing the content to terminal it is redirected to a file called "combined.txt" in the current folder.
Using >> instead of > means to append the output to the file instead of overwrite what already is there.

> = replace
>> = Append

Hope this helps.

To change the original script to output to a single file simply do the following amendment:
Original:
```
do
		cat $file | grep "<hdwd>" |sed -e 's_<hdwd>__g' -e 's_</hdwd>__g' -e '/^<entry/d' > $file.parsed
mv $folder/*.parsed $folder/parsed
		echo "$file Parsed"
	done
```

Amended:
```
do
 	cat $file | grep "<hdwd>" |sed -e 's_<hdwd>__g' -e 's_</hdwd>__g' -e '/^<entry/d' **>> result.txt**
		echo "$file Parsed"
	done
```

This will put the parsed text for all files in a single file called "result.txt" within the working directory.
To find your working directory:
```
echo $(pwd)
```

Cheers
Philip

---

### Post by clementeb on 2013-03-11
Great!!
Everything worked very well. I have also appreciated a lot your very clear instructions: the whole process has been very good for me also from the educational point of view.
I wish you a nice week. 
All the best,

Clemens

---

### Post by zero2xiii on 2013-03-11
Hay,

You are very welcome :). Every one has to learn.

Same to you

Philip

---

### Post by vasa1 on 2013-03-13
> **clementeb said:**
> ... I have also appreciated a lot your very clear instructions: the whole process has been very good for me also from the educational point of view....+1
A thread worth reading. Thanks from me as well. :)

---

