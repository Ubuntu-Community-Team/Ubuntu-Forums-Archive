---
title: "Nautilus - Right click option"
date: 2016-09-16
forum: General Help
---

### Post by Plasma_NZ on 2016-09-16
Sounds simple enough.. running 2 sceens and 2 xsessions... would like to add a option in nautilus right click menu...

So say i wanted to open this pdf/spreedsheet etc.. on the second monitor with the associated application it uses...  How would i add that to the right-click menu in nautilus.? 

.. so if i right-clicked on hunting.pdf - had a option to launch file on second monitor..


Ideas.?

---

### Post by Plasma_NZ on 2016-09-16
I understand where the script needs to be located ~/.local/share/nautilus/scripts  etc... my issue is the commands/programming inside.... i use .sh scripts for launching programs to second monitor using the DISPLAY=:0.2 commands etc.. my issue is how do i write a script that will open the selected file to the second monitor using the associated program for the file thats currently selected in nautilus right-click menu..?

---

### Post by Plasma_NZ on 2016-09-16
OK... so have managed to get it to open files on the second monitor with associated program for the file... how do i change the right click context menu name from || scripts - second monitor ||   to just  || Second Monitor ||./?

---

### Post by Plasma_NZ on 2016-09-17
Ok.. have it working pritty much how i want.. except it has issues with filenames that contain spaces.. where have i gone wrong.?

> #!/bin/bash
T=`libreoffice --draw $1`
echo "opening file "  $1  " of type " $T "with " `xdg-mime query default $T`
xdg-open $1
echo "finished script"
fi


---

### Post by Plasma_NZ on 2016-09-17
Solved... in the second line.. the $1 should be encased in "$1"

---

