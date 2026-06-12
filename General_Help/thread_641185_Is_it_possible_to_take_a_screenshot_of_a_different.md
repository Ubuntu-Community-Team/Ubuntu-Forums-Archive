---
title: "Is it possible to take a screenshot of a different workspace?"
date: 2007-12-15
forum: General Help
---

### Post by cknight on 2007-12-15
Does anyone know of a way to take screenshots of workspaces you are currently viewing?  I've got active programs on each workspace and it would be nice to capture a screenshot of all workspaces at once (or close to it) without manually switching to each and capturing the screenshot.  Is this possible?  

If it makes a difference, I'm using fluxbox.

Cheers!

---

### Post by dagnabit dang doohickey on 2007-12-15
The following script will capture screenshots of all your workspaces by running one command.
The script requires wmctrl and scrot to function (both are available in Ubuntu repos.)
```

#!/usr/bin/env bash

## scaws - Screenshot Capture of All Workspaces.

## Sleep time in seconds (floating-point values ok)
## Increase the sleep time value if experiencing screenshot errors.
sleeptime=0

i=1
j=$(wmctrl -d | wc -l)
k=$(wmctrl -d | grep '^[[:digit:]][[:space:]]\+\*')
let k=$(( ${k:0:1} ))

echo "Current workspace: $(( $k+1 ))"
echo "Total workspaces: $j"

wmctrl -s 0
while [ $i -le $j ] ; do
    sleep $sleeptime
    scrot "%F-%H%M%S_workspace-$i.png" -e 'echo "screenshot: $f"'
    sleep $sleeptime
    if [ $i -lt $j ] ; then
        wmctrl -s $i
    else
        wmctrl -s $k
        echo "Screenshots of all $j workspaces captured."
    fi
    (( ++i ))
done

exit 0

```
Save the code as "scaws" (or whatever you wish to name it) and put it in your users ~/bin/ directory.
Then, make it executable:
```
chmod +x ~/bin/scaws
```
To run it, simply enter "scaws" in the Alt+F2 run dialog (or in the terminal).

---

### Post by cknight on 2007-12-16
OK, cool, I'll give it a try.  Thanks

---

### Post by t-bone510 on 2007-12-16
cool script.

---

### Post by gejr on 2008-01-30
I extended dagnabit dang doohickey's script a bit to also automatically create a montage of the pictures. So the list of dependencies has obviously grown to include imagemagick (apt-get install imagemagick) ? 

I use archlinux so i don't know what apt calls it :)

Anyways..here's the script:

```

#!/usr/bin/env bash

## scaws - Screenshot Capture of All Workspaces.

## Sleep time in seconds (floating-point values ok)
## Increase the sleep time value if experiencing screenshot errors.
sleeptime=1

# Create montage automatically. Change to false to disable. 
montage_create=true;
montage_name=$(date +%b.%d-%H:%M:%S).png
# Your screen's resolution
resolution="1280x800"

# Delete captured images after montage has been created? change to false if you want to keep them.
delete=true;


i=1
j=$(wmctrl -d | wc -l)
k=$(wmctrl -d | grep '^[[:digit:]][[:space:]]\+\*')
let k=$(( ${k:0:1} ))
echo "Current workspace: $(( $k+1 ))"
echo "Total workspaces: $j"


wmctrl -s 0
while [ $i -le $j ] ; do
    sleep $sleeptime
    scrot "%F-%H%M%S_workspace-$i.png" -e 'echo "screenshot: $f"'
    sleep $sleeptime
    if [ $i -lt $j ] ; then
        wmctrl -s $i
    else
        wmctrl -s $k
        echo "Screenshots of all $j workspaces captured."
    fi
    (( ++i ))
done

if [ $montage_create = true ]; then
        montage *workspace-*.png -adjoin -tile 4 -geometry ${resolution} ${montage_name}
fi


if [ $delete = true ]; then
        rm *workspace*.png;
fi

exit 0

```

I included this example png of my workspaces:)

[[IMG]http://geo.norvegium.no/autoscreen-thumb.png[/IMG]]("http://geo.norvegium.no/autoscreen.png")

---

