---
title: "help with grep script?"
date: 2016-04-01
forum: General Help
---

### Post by rebeltaz on 2016-04-01
I have written a script that polls a website every xx minutes looking for a particular text pattern. I have everything working, but is there any way that I can get the script to play a sound only if the grep command finds a match? Maybe with a cvlc command?

This is what I have now:

```

#! /bin/bash

cd /home/derek/downloads/temp

while :
  do
    rm /home/derek/downloads/temp/*

    wget --reject *.jpg http://www.website.com/
    echo " " 
    echo "Searching For Text_Pattern........"
    grep -i 'text_pattern' index.html | sed 's/<img class.*\/a>//g' | sed 's/<h3>.*<\/h3>//g' | sed 's/href=\"/href=\"http\:\/\/www\.website\.com/g'
    echo " "

    echo "Waiting Three Minutes..."
    sleep 3m
  done

```

---

### Post by gabriel69 on 2016-04-01
First store the grep output in some variable.
Second verify with an if condition if the output maches with something...
Then use pc speaker to beep or other program to play the sound. ( mplayer for example )

---

### Post by rebeltaz on 2016-04-02
After I posted this, I got to thinking about it and I did just that!

Here is the final, working code...

```

#! /bin/bash

cd /home/derek/downloads/temp

while :
  do
    rm /home/derek/downloads/temp/*

    wget --reject *.jpg http://www.website.com/
    echo -e "\007"
    echo " " 
    echo "Searching For Text_Pattern........"
    results=$(grep -i 'text_pattern' index.html | sed 's/<img class.*\/a>//g' | sed 's/<h3>.*<\/h3>//g' | sed 's/href=\"/href=\"http\:\/\/www\.website\.com/g')

    if [ "$results" != "" ]; then
      echo "$results"
      cvlc /home/derek/music/alarm.mp3 
      exit
    fi
    
    echo "No Text_Pattern Found..."
    echo "Waiting Three Minutes..."
    sleep 3m
  done

```

Sometimes just posting the question helps the answer come to me! Thank you!

---

