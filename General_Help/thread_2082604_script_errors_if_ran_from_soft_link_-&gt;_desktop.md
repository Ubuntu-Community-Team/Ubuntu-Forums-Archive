---
title: "script errors if ran from soft link -&gt; desktop"
date: 2012-11-09
forum: General Help
---

### Post by HiImTye on 2012-11-09
I'm having a strange issue where if I run a script (specifically, my conky script) from a soft link, either on the desktop, or in nautilus, it has issues with both 'while read' loops, resulting in my dynamic icon not being drawn, and the reference file being improperly named.
if, however, I run it directly in naultilus, or from within a gnome terminal, it runs perfectly (resulting in my icon being drawn correctly, and the proper reference file being created).

this is the script that is displaying the strange behavior (everything within either 'while read' loops behaves strangely)

.conkyrc-scripts-time.sh
```
#!/bin/bash

settings=$HOME/Launchers/.conkyrc-settings-general
# load variables from file
. $settings

imgtmp=$tmpfolder/.time-icon.png
imgout=$tmpfolder/time-icon.png
updatestmp=$tmpfolder/time-updates
mailtmp=$tmpfolder/time-mail
updatecount=$(cat $updatestmp)
mailcount=$(cat $mailtmp)

# check if there is new mail
if [ "$mailcount" = 0 ] ; then
 # no new mail, report to conky
 echo "\${color7}No new mail."
elif [ "$mailcount" = 1 ] ; then
 # new mail, report to conky
 echo "\${color5}$mailcount \${color6}Unread eMail\${color5}!"
 # set our strings variable
 strings="$timeIconGmail"
elif [ "$mailcount" -gt 1 ] ;  then
 # new mail, report to conky
 echo "\${color5}$mailcount \${color6}Unread eMails\${color5}!"
 # set our strings variable
 strings="$timeIconGmail"
else
 # error checking, report to conky
 echo "\${color7}Error checking mail."
fi
# check if there is new mail
if [ "$updatecount" = 0 ] ; then
 # no updates, report to conky
 echo "\${color7}System up to date."
elif [ "$updatecount" = 1 ] ; then
 # updates, report to conky
 echo "\${color5}$updatecount \${color6}New Update Available\${color5}!"
 # set our strings variable
 strings=$(echo -e "$strings"'\n'"$timeIconUpdate")
else 
 # updates, report to conky
 echo "\${color5}$updatecount \${color6}New Updates Available\${color5}!"
 # set our strings variable
 strings=$(echo -e "$strings"'\n'"$timeIconUpdate") 
fi
# check whether we need to reboot or not
if [ -f /var/run/reboot-required ]; then
 # we need to reboot, report to conky
 echo "\${color6}Restart required."
 # set our strings
 strings=$(echo -e "$strings"'\n'"$timeIconRestart")
else
 # no need to reboot, report to conky
 echo "\${color7}Restart not required."
fi

# define our reference
while read f; do
 if [ "$f" = "$timeIconGmail" ]; then
  # just a number because KISS
  ref=1
 elif [ "$f" = "$timeIconUpdate" ]; then
  ref=2
 elif [ "$f" "$timeIconRestart" ]; then
  ref=3
 fi
 # append our number to the end of any existing references
 reference=$(echo "$reference""$ref")
done < <(echo "$strings" | grep [\da-zA-Z])
# add our reference path to the beginning of our reference filename
reference="$tmpfolder/time=$reference"
# define our background image
bg=$timeBottomImage
# make our picture
if [ ! -f "$reference" ]; then
 while read fg; do
  # incriment our count by 1
  count=$(( $count + 1 ))
  # make our offset, using our count
  pos=+$(( 46 + ( ( $count - 1 ) * 45 ) ))+15
  # do the actual work of creating the image
  composite -geometry "$pos" "$fg" "$bg" "$imgtmp"
  bg="$imgtmp"
 done < <(echo "$strings" | grep [\da-zA-Z])
composite "$timeTopImage" "$bg" "$imgout"
rm "$imgtmp"
rm "$tmpfolder"/time=*
touch "$reference"
fi
exit
```for reference, this is what it looks like when it works properly (when run at startup, from a terminal, or directly in nautilus):
[ATTACH]226950[/ATTACH]
and this is what it looks like when run from a soft link:
[ATTACH]226951[/ATTACH]

---

### Post by Vaphell on 2012-11-10
the output itself would be more useful than what conky does with it. Looking at raw output is likely to hint the kind of the problem. Is the symlink in the same dir as original file? Probably not and there is a relative path somewhere.


this can't be right
```
elif [ "$f" "$timeIconRestart" ]; ...
```

general improvements
```
strings=$(echo -e "$strings"'\n'"$timeIconUpdate")
strings=$strings$'\n'$timeIconUpdate
```
besides what you do here is essentially having an array and appending elements to it
you could go with something like this
```
strings+=( "$timeIconUpdate" )
strings+=( "$timeIconRestart" )
...
for f in "${strings[@]}"; do
  [[ $f =~ [\da-zA-Z] ]] || continue
  if ... fi
done
```


```
reference=$(echo "$reference""$ref")
reference=$reference$ref
```

```
count=$(( $count + 1 ))
(( count++ ))
```
or rolling the whole thing into one
```
pos=+$(( 46 + count++ * 45 ) ))+15
```

```
$ count=1
$ count=$(( $count + 1 ))
$ echo +$(( 46 + ( ( $count - 1 ) * 45 ) ))+15
+91+15
$ count=1
$ echo +$(( 46 + count++ * 45 ))+15
+91+15
$ echo $count
2
```

inside (()) you don't need $ to get var value, any text is assumed to be a variable either way (obviously you need $ with script params). post increment operator ++ does the 'get value and then add 1'

---

### Post by HiImTye on 2012-11-10
no errors are produced, however, it seems to be restricted to symlinks on the desktop, if I run it as a symlink from outside ~/Desktop it works as expected
> this can't be right     ```
elif [ "$f" "$timeIconRestart" ]; ...
```thanks for noticing, for some reason it worked intermittently, worked every time in conky, unless run from a symlink on the desktop

edit: I lied, even if I copy the main script to the desktop it doesn't work (even with the *"$f" "$timeIconRestart"* fix). it's not a linking issue, it's a desktop folder issue. strange.

---

### Post by Vaphell on 2012-11-10
does the script work in locations other than the original one?

---

### Post by HiImTye on 2012-11-10
yeah, if ran from any other location it works as expected

---

### Post by Vaphell on 2012-11-10
that's almost impossibiru o.O
Can you dump the output to file(s) and check the difference?

---

### Post by HiImTye on 2012-11-10
update: it only fails if ran from the Desktop folder. if I run the link on the Desktop from outside the desktop, it runs normally. again, no errors are produced, it just fails to work

I'm completely stumped at this point. I may just accept that 12.10 doesn't like to run things from within the 'Desktop' folder

edit: keeping this in mind, my workaround was to add '*cd ..*' to the start of my main conky script. works as expected now.

---

