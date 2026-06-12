---
title: "How do I unzip multiple files? (Thousands)"
date: 2016-02-11
forum: General Help
---

### Post by tyler91 on 2016-02-11
Okay so I just got a thing for a thing and I had to download a thing to unzip these files. Problem is, I can only unzip like 200 at a time and I have a couple thousand. Is there a way I can just unzip them all at once? They are all .7z archives. Thnx~

---

### Post by QIII on 2016-02-11
You would be much more likely to get help if your first sentence were not gibberish.  Nobody will read past that.

---

### Post by newbie-user on 2016-02-11
Put them all in a single folder, then in the terminal, navigate to that folder and run:
```
7za e *.7z
```

---

### Post by tyler91 on 2016-02-11
> **newbie-user said:**
> Put them all in a single folder, then in the terminal, navigate to that folder and run:
```
7za e *.7z
```

That didnt work..

---

### Post by yancek on 2016-02-11
You neglected to post the output/results of what "didn't work" making it difficult for anyone to suggest another approach unless they want to spend the day guessing.

---

### Post by tyler91 on 2016-02-11
Ok well, here is what it says when I input that cmd.

kleo-hat@Spoks-100101011011:~$ cd /home/kleo-hat/Downloads/THIG
kleo-hat@Spoks-100101011011:~/Downloads/THIG$ 7za e *.7z

7-Zip (A) [64] 9.20  Copyright (c) 1999-2010 Igor Pavlov  2010-11-18
p7zip Version 9.20 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,4 CPUs)

Processing archive: Nagagutsu wo Haita Neko - Sekai Isshuu 80 Nichi Daibouken.7z


No files to process

Files: 0
Size:       0
Compressed: 30186
kleo-hat@Spoks-100101011011:~/Downloads/THIG$

---

### Post by montag dp on 2016-02-11
> **tyler91 said:**
> Ok well, here is what it says when I input that cmd.

kleo-hat@Spoks-100101011011:~$ cd /home/kleo-hat/Downloads/THIG
kleo-hat@Spoks-100101011011:~/Downloads/THIG$ 7za e *.7z

7-Zip (A) [64] 9.20  Copyright (c) 1999-2010 Igor Pavlov  2010-11-18
p7zip Version 9.20 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,4 CPUs)

Processing archive: Nagagutsu wo Haita Neko - Sekai Isshuu 80 Nichi Daibouken.7z


No files to process

Files: 0
Size:       0
Compressed: 30186
kleo-hat@Spoks-100101011011:~/Downloads/THIG$I just tried this and get the same problem.  For some reason, 7za doesn't seem to work with wildcards.  Here's a script to do the same thing, but one at a time.  Save it as unzip.sh (or whatever you want to call it), make it executable, and run it in the directory where all you *.7z archives reside.

```
[FONT=monospace]**#!/bin/bash**

[/FONT][FONT=monospace]**while read line; do**
  7za e **"****$line****"**
**done** **<** **<****(****ls**** *.7z****)**
[/FONT] 
```

---

### Post by tyler91 on 2016-02-11
> **montag dp said:**
> , make it executable,

As in run it with "Run Software"?

I copied and pasted it into gedit then saved it as unzip.sh then ran it with "Run Software" but nothing happened.

---

### Post by tyler91 on 2016-02-11
Wait...

---

### Post by tyler91 on 2016-02-11
Which one?

---

### Post by tyler91 on 2016-02-11
I tried both but nothing.

---

### Post by montag dp on 2016-02-11
Save it in the same directory as your *.7z files. Open a terminal, navigate to the same directory, and then type chmod +x unzip.sh to make it executable. Then run it by typing ./unzip.sh. If it doesn't work, please post the output.

---

### Post by buzzingrobot on 2016-02-11
Do this in a terminal in the directory containing the script:

> sudo chmod +x unzip.sh

This makes the script executable. 

To execute the script, place it in the same directory with the archives.  Then, in a terminal, first change to the directory holding the archives.

Then, do this:  > ./unzip.sh (Note the period in front of the backslash).

chmod is the command that flags a file as executable. That's how it's done in Unix and Linux.  File extensions aren't used like they are in Windows.

---

### Post by steeldriver on 2016-02-11
The version of 7z from p7zip-full (at least) does seem to support wildcards - but as a quoted argument rather than a true shell glob i.e.

```

7z e '*.7z'

```
or
```

7z e "*"

```

---

### Post by tyler91 on 2016-02-11
It worked!! Thanks a whole bunch! \(*0*)/

---

### Post by montag dp on 2016-02-11
You're welcome (if it was the script that worked for you).

---

### Post by tyler91 on 2016-02-11
Yes, it was the script and your guy's help! Thanks alot~

---

