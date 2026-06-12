---
title: "Can Linux do this?"
date: 2008-04-30
forum: General Help
---

### Post by iSplicer on 2008-04-30
Hey all!

I heard from here and there that linux is extremely powerful and bash commands can do just about anything. Is it possible to do this:

Say I have a folder that is 7.5GB. It has 23 folders in it. In each of these folders there is a split RAR archive of about 350MB. Is there a bash script that one can write to go to each of these folders, extract the file within the split archive for all the 23 folders without any intervention?

That would really be great, because going to each folder and manually extracting the files is really tedious.

Thankyou!~

---

### Post by ibutho on 2008-04-30
Its possible. I'm not very good with bash, but some options I can think of, use a for loop, find (with exec or xargs) or a combination of both.

---

### Post by iSplicer on 2008-04-30
Thanks for the reply. Could anyone please suggest some nice bash tutorials that I can learn from?

thankyou

---

### Post by dreadlord_chris on 2008-04-30
Bash Scripting Guide
[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

---

### Post by rajan on 2008-04-30
if you let this post sit for a few minutes someone who is smarter than me will write you a really good basic script. what you're looking for in my opinion is:

1 a function that will note which files or directories need to be processed
2 a systematic way to queue them up
3 the actual processing

i am not sure about #3, but i am fairly certain that something to this effect will work for #1 and #2:

```

sh
for x in `ls`
do 

```
whatever the commands you need should be inserted after that. this should only be a starting point. good luck.

---

### Post by iSplicer on 2008-05-01
Thankyou for the replies, guys!

If any more advice is available, that woulde be great!

---

### Post by rajan on 2008-05-01
ok so the code should look more like this:

```

sh
```
hit return and you'll be put into the "sh" environment. if you're bent on doing this in bash, then this isn't the way, but you definitely have "sh" on your computer.

after you're in the sh environment:

```

for x in `ls`;
do
echo $x
done

```

hit control and "d" to get out of the "sh" environment after you type in "done." the program will automatically be executed upon exit of the environment.

note that this won't actually do anything except for echoing the list of your directory back out to you, but you can replace the echo $x part with anything you'd like. what you're doing in this script is loading the contents of "ls" into a buffer and then reading that buffer piecewise into a variable called "x" which must be referenced as a variable using the dollar sign. why don't you try something out and then post what difficulties you have back on here. we'll be more help with a more specific description of your problem.

---

### Post by ryanhaigh on 2008-05-01
Its not bash because I have gotten used to doing these things in python now but here it is anyway:
```

#!/usr/bin/env python
#extracts all rar files recursively

import os
import sys
path='.'
#path='/path/to/music/collection'
for root, dir, files in os.walk(path):
    for file in files:
        if file.endswith('.rar') or file.endswith('.RAR'):
            os.system('unrar e -y '+root+os.sep+file)
 
sys.exit(0)

```


And to prove that bash is indeed quite powerful (and that I still know how to use it) a one liner
```

find ./ -iname '*.rar'  -exec unrar e -y {} \;

```

---

### Post by danwood76 on 2008-05-01
split rars dont have the .rar extention.
They tend to have .rxx (xx = number) or sometimes just a number.
You only need to tell it to unrar the first one.

so the above python would then be:
```

#!/usr/bin/env python
#extracts all rar files recursively

import os
import sys
path='.'
#path='/path/to/music/collection'
for root, dir, files in os.walk(path):
    for file in files:
        if file.endswith('.rar') or file.endswith('.RAR') or file.endswith('.r00'):
            os.system('unrar e -y '+root+os.sep+file)
 
sys.exit(0)

```

---

### Post by ryanhaigh on 2008-05-01
I didn't know that rar archives could JUST have the numbered files, all of the one I have also have the .rar and then the .r** files. For archives that contain both this would cause the archvie to be extracted twice. You may want to adjust the options passed to rar to tell it not to overwrite files (use this: 'unrar e -y -o-'). Check the man page of unrar for further options.

---

### Post by danwood76 on 2008-05-01
I have many that have just the numbers, it depends what sofwtare you make the rars with.

---

### Post by iSplicer on 2008-05-01
I thanked everyone who replied, I will read through the posts and see how it goes. Thanks again!

---

