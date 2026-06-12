---
title: "[SOLVED] Music Length"
date: 2008-05-26
forum: General Help
---

### Post by init1 on 2008-05-26
How would I calculate how many hours of music I have with Ubuntu?

---

### Post by barichardson5727 on 2008-05-26
I use amarok as my media player and it tells the total play time of all the songs in your music library if you don't have anything playing. Amarok is not installed by default but it should be available in the package manager.

---

### Post by ibuclaw on 2008-05-26
Here is a script I just wrote to solve your problem.

It only reads mp3 files though, as it uses mp3info to read the tag data.
```
sudo apt-get install mp3info
```

```

#!/usr/bin/env bash

calc()
{
    export secs=$1
    export mins=$((secs / 60))
    export hours=$((mins / 60))
    export days=$((hours / 24))
    echo
    echo -n "You have "
    echo -n "$days days, "
    export temp=$((days * 24))
    echo -n "$((hours - $temp)) hours, "
    export temp=$((hours * 60))
    echo -n "$((mins - temp)) minutes and "
    export temp=$((mins * 60))
    echo -n "$((secs - temp)) seconds of mp3 music "
    echo "in your $path directory."
}    

search()
{
    if [ -d "$1" ]
    then echo -n "Finding Files..."
         for song in "$(find "$1" -iname "*.mp3" 2>/dev/null)"
         do echo "$song" | sed 's/ /?/g;s/\[/*/g;s/\]/*/g' > .musiclist
         done
         [ "$(cat .musiclist)" == "" ] && export num=0 || export num=$(wc -l .musiclist | awk '{print $1}')
         echo  "Found $num MP3s"
         export i=1
         export j=1
         echo -n "Reading Files..."
         for song in $(cat .musiclist)
         do  export length=$(mp3info -p %S "$song")
             let total=(total + length)
             if [ $i -eq 100 ]
             then echo -n "$((i * j++))."
             export i=1
             else let "i++"
             fi
         done
         echo $num
         calc $total
    else echo "Argument not a valid path"
         exit 1
    fi
}

die()
{
    echo "Usage: $1 /PATH/TO/DIR/"
    exit 1
}

total=0
count=0
path="$1"
[ $1 ] && search "$1" || die $0
rm .musiclist
echo
exit 0

```

You should get an output like this:
[PHP]
$ ./script /home/iain/music/
Finding Files...Found 16 MP3s
Reading Files...16

You have 0 days, 1 hours, 42 minutes and 52 seconds of mp3 music in your /home/iain/music/ directory.
[/PHP]
Although, depending on how many files you have. This could take from 5 seconds (dozens of files) to 5 minutes (thousands of files).

Regards
Iain

---

### Post by sdennie on 2008-05-26
tinivole: Come on...  Where is the semi-oneliner?

```

echo -n "secs=" > /tmp/.mp3info; find . -name "*.mp3" -exec mp3info -p %S {} \; -exec echo -n " + " \; >> /tmp/.mp3info ; echo -e "0;days=secs/60/60/24;days;hours=secs/60/60;hours-days*24;secs/60-hours*60" >> /tmp/.mp3info ; printf "%d days %d hours %d mins\n" `cat /tmp/.mp3info | bc` ; rm /tmp/.mp3info

```

Edit:

For both this solution and tinivoles, you'll need to first:
```

sudo apt-get install mp3info

```

---

### Post by init1 on 2008-05-27
Thanks for your comments, this was exactly what I was looking for :D

---

