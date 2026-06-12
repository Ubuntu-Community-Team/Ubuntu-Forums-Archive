---
title: "Handbrake dvd to ipod script"
date: 2007-01-27
forum: General Help
---

### Post by bitterbug on 2007-01-27
I spent about an hour and a half last night trying to get Handbrake to compile on my machine, only to realize that the space in the name of the directory above it was breaking the compile script. (I knew there was a reason I always felt queasy putting spaces in folder names in Windows).

Anyway, once it compiled I opened up ipodvidenc and made the necessary changes to make it rip a DVD and save it to a filename of your choice.

It's very basic but it gets the job done on straightforward jobs.

```

#!/bin/bash
## dvdtoipod - Handbrake encoder script for Linux.
## Derived from
## ipodvidenc - The iPod Video Encoder for Linux.
## Created by Eric Hewitt, January 9, 2006.
## Released under the GPL.

echo "What would you like to name the output file (sans extension)?"

read output_file_name

echo "$output_file_name will be located in $PWD. Is this acceptable? [y/n]"

read output_file_loc_permis

if [ $output_file_loc_permis = 'n' ] || [ $output_file_loc_permis = 'N' ]
then
        echo "Where would you like to store $output_file_name.mov?"
        read output_dir
else
        output_dir=$PWD
fi

hbtest -i /dev/dvd -o ${output_dir}/${output_file_name}.ipod.mp4 -t 1 -a 1 -2 -d -r 29.97 -R 44100 -b 400 -w 320 -l 240 -f mp4


```

Note that hbtest is in lowercase, so you may need to modify it if you're using the original mixed case name.

Don't forget to chmod 755 the script.

Cheers :)

---

### Post by soze on 2007-05-25
You might also be interested in dvpod, which  is a simple wrapper script for HandBrake that simplifies and automates ripping one or more tracks from a DVD to a file which can be viewed on a video iPod.

It can be downloaded from: [http://sourceforge.net/projects/dvpod](http://sourceforge.net/projects/dvpod)

You will obviously need to have HandBrake installed in order to run this.

---

