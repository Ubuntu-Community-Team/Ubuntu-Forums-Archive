---
title: "How to add Zenity/YAD to this script to show progress bar?"
date: 2014-05-16
forum: General Help
---

### Post by Thee on 2014-05-16
Hi,

I have this script that I found on the net which helps me copy files with specific names to specific folders.
I want to use this script to copy some large files from local disk to a NAS, and I would like to see a GUI progress bar while copying.
Can anyone help me with that?

Here's the script:

```

dir1=~/tmp/dir1
dir2=~/tmp/dir2


for f in *.avi *.mp4; do
    case $f in
         *[Tt][Ee][Ss][Tt]*) mv -n $f $dir1 ;;
         *[Ff][Ii][Ll][Ee]*) mv -n $f $dir2 ;;
    esac
done

```

Thanks!

---

### Post by Habitual on 2014-05-18
I'd make the 'for f in" a function:

```

dir1=~/tmp/dir1 ;<-- this may not work, try absolute /path/to/tmp/dir1
dir2=~/tmp/dir2 ;<-- this may not work, try absolute /path/to/tmp/dir2

function do_work ()
{
for f in *.avi *.mp4; do
    case $f in
         *[Tt][Ee][Ss][Tt]*) mv -n $f $dir1 ;;
         *[Ff][Ii][Ll][Ee]*) mv -n $f $dir2 ;;
    esac
done
}

```

then 'touch' a /tmp file and call the function, then remove the /tmp file as in 
```
touch /tmp/$$
( ( echo 1 ; while [ -f /tmp/$$ ] ; do sleep 1 ; done ; echo 100 ) | yad  --progress --pulsate --auto-close --text="Doing Work..."  --width=150 --title="" --undecorated --no-buttons) & do_work
rm /tmp/$$ 
```

See [http://bournetoraiseshell.com/article.php?story=2011070711554993](http://bournetoraiseshell.com/article.php?story=2011070711554993) for my similar script.

I haven't been able to have the progress bar work in this kinds of activity, so I used pulsate to indicate activity.
Hope that helps.

---

### Post by Thee on 2014-05-18
Yeah I guess the pulsate will have to do then, even if it doesn't help to know how much is copied. Thanks in any case ;)

---

### Post by Vaphell on 2014-05-18
in order to have proper progress bar you'd have to collect relevant files first (put them in array) count them, optionally calculate their sizes if you want progress by size not by number of items.


```
#!/bin/bash

dir1=./dir1
dir2=./dir2


declare -A files # [$file]=$destination

for f in *.avi *.mp4
do
    case $f in
         *[Tt][Ee][Ss][Tt]*) dest=$dir1 ;;
         *[Ff][Ii][Ll][Ee]*) dest=$dir2 ;;
         *)                  continue ;;
    esac
    files[$f]=$dest   
done

for k in "${!files[@]}"
do
    echo mv -n -t "${files[$k]}" "$k" >&2
    sleep 0.1
    echo $(( ++i*100/${#files[@]} ))%
done | zenity --progress
```

---

### Post by Habitual on 2014-05-18
Thanks Vaphell,
I can always count on you to make code "better".

---

### Post by Thee on 2014-05-20
Thanks! I'll give it a try :)

---

### Post by Thee on 2014-05-20
Looks like it doesn't work..

```

movefile3.sh: 8: movefile3.sh: declare: not found
movefile3.sh: 17: movefile3.sh: files[file.avi]=/home/thee/: not found
movefile3.sh: 17: movefile3.sh: files[test.avi]=/home/thee/: not found
movefile3.sh: 20: movefile3.sh: Bad substitution

```

---

### Post by Vaphell on 2014-05-21
are you using bash or sh?
associative arrays are a bash feature.

---

### Post by Thee on 2014-05-21
I used sh, my fault, but still the script doesn't move the files when I used bash instead... only shows 100% progress bar and OK button..

```

$ bash movefile3.sh
mv -n -t /home/thee/ file.avi
mv -n -t /home/thee/ test.avi

```

---

### Post by Vaphell on 2014-05-21
note that in my proof of concept i put *echo*(sent to stderr) in front of *mv*, effectively neutering it, so the progress of the processing could be eyeballed in terminal too to confirm the progress bar works correctly. I also put superfluous *sleep* there to emulate mv delays, because otherwise the whole loop effectively did nothing and ended in 0.01s.

don't call shell explicitly when running script, you have a hashbang line (#!/bin/bash) for that. *chmod u+x* the script and run it like

```
./movefile3.sh
```

the system will use the shell specified in the script.

---

### Post by Vaphell on 2014-05-21
double post

---

### Post by Thee on 2014-05-21
Please excuse my ignorance, it works like a charm now! :)
Thank you very much!

---

