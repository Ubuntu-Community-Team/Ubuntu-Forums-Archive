---
title: "Install and run Unigine 4.0"
date: 2014-12-04
forum: General Help
---

### Post by sanfrd16237 on 2014-12-04
Longtime lurker here, finally had a problem i couldnt search an answer for. Ive been messing with linux on and off for a while but now am finally getting into figuring out how to open different filetypes etc.  My question is - I am trying to run Unigine 4.0.  I managed to install the main .run file now i have a normal Unigine file with a couple of folders in it.  Inside the bin folder there are a couple of executables in there that wont open.  I have set them to be executable but still nothing.  This is my first attempt at dealing with a non repository application install.  Not sure what else i can do.  Any help would be greatly appreciated.

---

### Post by dragonfly41 on 2014-12-04
I don't know Unigine .. but perhaps you've missed some step in this advice ...

[http://sourcedigit.com/12262-execute-run-bin-file-linux-ubuntu-14-04/](http://sourcedigit.com/12262-execute-run-bin-file-linux-ubuntu-14-04/)

---

### Post by sanfrd16237 on 2014-12-04
When i try and follow the gui instructions it only tries to open with gedit.  It looks like its trying to load something and i have a wall of text but nothing but a huge amount of cpu usage is present.  Ive left it to load for close to 20 mins but no progress.  The terminal install is what i did before and all it leaves me trying to do is open with "sudo ./Unigine_Heaven-4.0.run"  all i get is command not found.

---

### Post by dragonfly41 on 2014-12-04
Just to be certain .. step by step

Open terminal in same directory where you have downloaded Unigine_Heaven-4.0.run 

Make the file executable ...
[COLOR=#0000ff]chmod +x Unigine_Heaven-4.0.run[/COLOR]

Right click on Unigine_Heaven-4.0.run and check properties

Run the executable file ...
[COLOR=#0000ff]sudo ./Unigine_Heaven-4.0.run[/COLOR]

---

### Post by sanfrd16237 on 2014-12-04
Alright i did the exact steps.  This is pretty much what i did the first time.  Once again though i have an uncompressed folder wirh the same contents.  In the terminal this is the message afterwards that i get.

"Unigine Heaven Benchmark installation is completed. Launch heaven to run it"

There is a file in the folder that is labeled heaven but when i try and open it, it will open with gedit and give me this message

"#!/bin/bash

cd ./bin
ARCH=$(uname -m)
if [ "$ARCH" == x86_64 ]; then
    export LD_LIBRARY_PATH=./x64:$LD_LIBRARY_PATH
    ./browser_x64 -config ../data/launcher/launcher.xml
else
    export LD_LIBRARY_PATH=./x86:$LD_LIBRARY_PATH
    ./browser_x86 -config ../data/launcher/launcher.xml
fi

I even tried to run it from the terminal and only get command not found.  Im fairly certain im missing someting simple here.

---

### Post by pqwoerituytrueiwoq on 2014-12-04
chmod +x that script that open in gedit
then it should work when you double click it
you can just run the script via terminal

---

### Post by sanfrd16237 on 2014-12-04
Im sorry, i do understand what you want me to do but im unsure how to do it.  And which part of the script?  Can i copy and paste the script or do i have to open up that directory again?

---

### Post by dragonfly41 on 2014-12-04
The file I looked at is 273MB in size .. not a short script ..

[http://www.techpowerup.com/downloads/2204/unigine-heaven-benchmark-4-0-for-linux/](http://www.techpowerup.com/downloads/2204/unigine-heaven-benchmark-4-0-for-linux/)

---

### Post by sanfrd16237 on 2014-12-04
Yep, thats it.  Should i have waited longer for gedit to do its thing?

---

### Post by dragonfly41 on 2014-12-04
p.s.  found this thread .. seems you have to run **./heaven**

[http://ubuntuforums.org/showthread.php?t=2144692](http://ubuntuforums.org/showthread.php?t=2144692)

---

### Post by sanfrd16237 on 2014-12-04
I have tried to run ./heaven in a variety of ways and only get command not found or directory not found.  Where from and how should i run this?

Update: It worked. I just wasnt getting the directory right.  The real question now is how can i make a shortcut do this?

---

### Post by pqwoerituytrueiwoq on 2014-12-04
[[IMG]http://www.zimagez.com/miniature/screenshot-12042014-090829pm.php[/IMG]]("http://www.zimagez.com/zimage/screenshot-12042014-090829pm.php")
do that and you can double click on it

just have your launcher cd to that directory, setting the working directory SHOULD do the same thing
this command should in theory work in a launcher
```
cd ~/heaven && ./heaven
```

---

### Post by sinisa1hr-z on 2015-07-09
so its simple like this 4[COLOR=#0000cd] blue[/COLOR] commands!
somewhere you download it,that can be in "Downloads" what is "Preuzimanja" in my local Croatian language..or wherever,and whatever named folder you like,just change name,and location to reflect that
in terminal open that location,in my case is like this
# cd to folder where is downloaded script located,in my case folder name is "Preuzimanja" 
sinisa1hr@amd64sabertooth:~/Preuzimanja$  
# in your case that can be any folder but probably will be something like Downloads 
when you are in make as was written above in previous post,but i will repeat,how to start that downloaded shell script
[COLOR=#dda0dd]#we located where is and now we give it permission to run[/COLOR]
[COLOR=#0000ff]chmod +x Unigine_Heaven-4.0.run
[/COLOR]#now we will start it,i mean we gonna start script not benchmark program!
[COLOR=#0000ff]sh Unigine_Heaven-4.0.run
[/COLOR]
#you will get message in terminal like this:if not,double check,and repeat steps above

[COLOR=#800080]"Creating directory Unigine_Heaven-4.0
Verifying archive integrity... All good.
Uncompressing Unigine Heaven Benchmark.............................................................................
Unigine Heaven Benchmark installation is completed. Launch heaven to run it"
[/COLOR]
then, you will get one extracted folder in your (Downloads or where you downloaded,or save it) folder ,so ,go to that,with cd command in terminal,so now you need to 

[COLOR=#0000ff]cd Unigine_Heaven-4.0[/COLOR]

and you will be inside folder what was created by script you downloaded ..

in my case that look like in terminal like this
sinisa1hr@amd64sabertooth:~/Preuzimanja/Unigine_Heaven-4.0$

and opposite what was written in some post(two above) ,you need just to type,without any "run" command! so now we will start benchmark program, just type or copy in terminal

[COLOR=#0000ff]./heaven[/COLOR]

to start it! 

enjoy,

looks like long ,but its short and works anytime! use sudo with commands if you need it,or if you are unsure when you need it. Most of you will need sudo just with chmod command.

---

