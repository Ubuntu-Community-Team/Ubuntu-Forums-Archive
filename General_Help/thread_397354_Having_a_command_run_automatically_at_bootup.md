---
title: "Having a command run automatically at bootup"
date: 2007-03-30
forum: General Help
---

### Post by sticks on 2007-03-30
There is a certain line that I run from the terminal to enable sound in a game 
application , echo "quake3.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss.
To avoid having to run that command every time I start up the game is there
any way I can have this line run automatically?

I tried putting that line in a script named "quake3" and put it in the
 /etc/init.d/ folder then ran the commands "$chmod +x quake3" then
"% update-rc.d quake3 defaults"

This didn't work

I tried adding the line to /etc/init.d/bootmisc.sh 
That didn't work


Not being able to run this line automatically I at least tried to create an alias
so I wouldn't have to type in the whole line everytime, I edited .bashrc with
# Define your own aliases here ...
if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi


alias q3='echo "quake3.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss'

This also did not work.


Is there any way I can do this?

---

### Post by Adramelech on 2007-03-30
try making a script like

echo "quake3.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
./quake

So run it at the same time you run quake

---

