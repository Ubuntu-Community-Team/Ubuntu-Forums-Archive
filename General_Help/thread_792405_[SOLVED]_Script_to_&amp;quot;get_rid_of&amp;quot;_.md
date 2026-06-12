---
title: "[SOLVED] Script to &amp;quot;get rid of&amp;quot; gnome panel"
date: 2008-05-12
forum: General Help
---

### Post by Matthewslf on 2008-05-12
I use awn, and wanted to be able to get rid of the gnome panel, so I researched it. If you kill it, it will keep coming back unless each time you disable it in session preferences. Instead of killing the panel, I decided to just hide it. The script uses gconftool to set the panels to hide. It only fully works if you go in gconf-editor to apps --> panel --> toplevels --> (every panel) --> auto_hide_size and set it to zero. Once this is done you just run the script with the arguments hide or show.
Here's the code:
```
if [ $# -ne 1 ]; then
echo "Need 1 and Only 1 Argument"
exit 127
fi
if [ $1 != "hide" -a $1 != "show" ]; then
echo "Can only accept hide or show"
exit 127
fi
if [ $1 = "hide" ]; then
b="true"
fi
if [ $1 = "show" ]; then
b="false"
fi
gconftool /apps/panel/toplevels --all-dirs|tee /tmp/gconfpanel > /dev/null
split -d -a 1 -l 1 /tmp/gconfpanel /tmp/p
n="`wc -l /tmp/gconfpanel|grep -o [0-9].`"
i=0
n=`expr $n - 1`
while [ $i -le $n ]
do
t="/tmp/p"$i > /dev/null
c=`sed "s/[0-9]/&\/auto_hide/g" $t|sed "s/[\n\t\v\r\f]//g"` > /dev/null
gconftool $c -s --type boolean $b > /dev/null
rm $t
i=`expr $i + 1 `
done
rm /tmp/gconfpanel
echo "Done"
```
This is my first full shell script, so beware of bugs, but it should work fine. To use it copy the code into a text editor, save it, allow executing file as program in properties, and run it in terminal. It is also possible to script compiz so that it enables/disables the gnome panel when compiz starts/stops. Add code into the between and after the last two lines of /usr/bin/compiz and fiddle around with it.

---

