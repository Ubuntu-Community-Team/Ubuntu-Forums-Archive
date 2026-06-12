---
title: "Random Login/out Sounds?"
date: 2008-06-19
forum: General Help
---

### Post by knudsenjoe on 2008-06-19
Is it possible to have a random login/out sound? Maybe someone could help me out with a script or point me somewhere? If it matters I'm on Ubuntu/Gnome, but I would use whatever for this effect.

'Preciate it.

---

### Post by ibuclaw on 2008-06-19
Here you go sir.

[EDIT]
Shortened the script.
[PHP]
#!/bin/bash
SNDSDIR="/usr/share/sounds"
FILE="$HOME/.gnome2/sound/events/gnome-2.soundlist"

function replace {
    j=$RANDOM
    let "j = $j % $RANGE"
    echo ${LIST[$j]}
}

function writefile {
    while [ $# -gt 0 ]
    do echo >> "$FILE.bak"
       case $1 in
           "[login]")
              echo "$1" >> "$FILE.bak"
              echo "file=$LOGIN" >> "$FILE.bak"
              shift 2
              ;;
           "[logout]")
              echo "$1" >> "$FILE.bak"
              echo "file=$LOGOUT" >> "$FILE.bak"
              shift 2
              ;;
           *)
              echo "$1" >> "$FILE.bak"
              echo "$2" >> "$FILE.bak"
              shift 2
              ;;
       esac
    done
    mv "$FILE.bak" "$FILE"

}
# Get the current config file.                                                  
CONTENTS=( `cat $FILE` )

# Get the directory listings.
LIST=( `find $SNDSDIR -iname "*.wav"` )

# Get the number of lines in that list.
RANGE=${#LIST[@]}

# Run a loop to grab new sound file.
LOGIN=$(replace)
LOGOUT=$(replace)

# Set sounds to new file
writefile ${CONTENTS[@]}
cp "$FILE" "$HOME/.gnome/sound/events/gnome.soundlist"
exit
[/PHP]
As for making it run automatically, save the above into a file, make sure it is executable
```
chmod +x **filename**
```
And open up the file **/etc/gdm/PostSession/Default**.
```
sudo gedit /etc/gdm/PostSession/Default
```
Then put at the bottom before the **exit 0** line
```
su - username -c "/path/to/script"
```
Replacing **username** with your username and **/path/to/script** with the path to the script. Keep the double quotations.

Regards
Iain

---

### Post by ibuclaw on 2008-06-20
Oh, and here is a one-liner! :lolflag:

In true BASH style fashion:
```
d="/usr/share/sounds";f="$HOME/.gnome2/sound/events/gnome-2.soundlist";z(){ let "j=$RANDOM%$r";echo "${l[$j]}";};l=( `find $d -name "*.wav"` );r="${#l[@]}";o="$(z)";i="$(z)";sed -i '/logout/,+1d;/login/,+1d' "$f";echo -e "\n[logout]\nfile=${o#$d/}\n\n[login]\nfile=${i#$d/}" >> "$f";uniq "$f" > "$f~"; mv "$f~" "$f";cp "$f" "$(echo $f | sed 's/2//g;s/-//')"
```

I've improved the script on so many levels :)
Here is the full toosh:
```

#!/bin/bash
# d = Sound Directory
# f = Config File
# z = A Function
# l = List of all Sounds
# r = Range (No of Sounds)
# j = The chosen Sound
# i = logIn sound
# o = logOut sound

d="/usr/share/sounds"
f="$HOME/.gnome2/sound/events/gnome-2.soundlist"
z()
{
    let "j=$RANDOM%$r"
    echo "${l[$j]}"
}

l=( `find $d -name "*.wav"` )
r="${#l[@]}"
o="$(z)"
i="$(z)"
sed -i '/logout/,+1d;/login/,+1d' "$f"
echo -e "\n[logout]\nfile=${o#$d/}\n\n[login]\nfile=${i#$d/}" >> "$f"
uniq "$f" > "$f~"
mv "$f~" "$f"
cp "$f" "$(echo $f | sed 's/2//g;s/-//')"

```

Regards
Iain

---

### Post by knudsenjoe on 2008-06-20
'Preciate the help y'all.

I tried with both scripts, but something seems amiss...

1) Do I need to turn off the sound files in the sound manager?

2) I'm on a triple boot, so do I need to point this to my ubuntu partition?

3) Where it says $HOME/.gnome2/sound/.......Do I need to make it say $HOME/**my user name**/.gnome2/sound......I actually went ahead and tried, but given conditions above not sure if it mattered

Please forgive a noob.

---

### Post by ibuclaw on 2008-06-20
Does the file exist?
```
test -f $HOME/.gnome2/sound/events/gnome-2.soundlist && echo YES || echo NO
```

If you get a **NO** from the above, then yes. Turning them off (or setting them to another value) would create the file and then it should work now.

And **$HOME** should be your home directory.
```
echo $HOME
```

Also. just to let you know, I turned on the PC this morning to have the sound "**TURN LEFT**" come through my speakers... Haha. I laughed so hard :)

Regards
Iain

---

### Post by knudsenjoe on 2008-06-20
I can't seem to figure it out. I'm thinking maybe I'm not saving the script properly.

Is it supposed to be a text file, a bin file, or what?

I 'preciate your help.

---

### Post by honkyusa on 2008-10-01
Your bash script works perfectly, however, I'm running into a problem with the actual custom .WAV files not playing.  Do you know if they need to be a certain freq or size ?   Right now I'm having to put a line into my startup programs:   mpg123 -q /path/to/your/file.mp3   

This approach works but is lame.   Any suggestions ?

---

