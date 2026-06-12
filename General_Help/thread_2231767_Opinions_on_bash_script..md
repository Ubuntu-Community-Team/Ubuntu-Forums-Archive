---
title: "Opinions on bash script."
date: 2014-06-27
forum: General Help
---

### Post by CaptainMark on 2014-06-27
I'd like some opinions on this script I wrote that organizes photos into a year/month directory structure out of my dropbox folder on a permanent loop, it's been changed many times over the years since I first scribbled it down, it got very long and convoluted, then recently I pretty much scrapped it and re-wrote it cutting away a lot of unnecessary bits.  

I'd like to know what people think of my code and if anyone has any constructive criticism of my bash technique

```
#!/bin/bash #~ run on: desktop
 #~ Photo Sorter
 #~ A script to sort photos in date ordered directories
 #~ Mark Skinner
 #~ Created 04/03/2012
 #~ last modified 27/06/2014
 #~ Requires jhead to be installed


set -x


while true; do
    # sleep for 5mins
    sleep 5m


    # determine files for iteration
    while read -d $'\0' photo ; do
        # obtain photo timestamp
        timestamp=$(jhead "$photo" | grep Date/Time)
        # strip full path name from photo
        photo=$(basename "$photo")
        # obtain year and month
        year=${timestamp:15:4}
        month=${timestamp:20:2}
        # if year and month both exist
        if [ $year ] && [ $month ]; then
            # rename photo whilst capturing new photo name
            renamed_photo=$(jhead -n%Y-%m-%d\ %H:%M:%S $HOME/Dropbox/Camera\ Uploads/"$photo" |awk -F '/' {'print $(NF)'})
            # mv photo to new location
            mkdir -p $HOME/Pictures/$year/$month; mv -n $HOME/Dropbox/Camera\ Uploads/"$renamed_photo" $HOME/Pictures/$year/$month/
        fi
    done< <(find ~/Dropbox/Camera\ Uploads -maxdepth 1 -iname *.jpg -print0)


    # sleep for another 5mins
    sleep 5m


done

```
Thanks

---

### Post by papibe on 2014-06-27
Hi CaptainMark.

A few thoughts and ideas:

**Sleep and find**
I'm not sure how Dropbox works, but if the file appears on the folder when fully updated, then you may take advantage of the inotify tools. Instead, of waiting and then scanning the whole directory, you would be directed just to the files that were changed. This would be the general idea:
```
#!/bin/bash

while read -r file ; do
    echo "File to work with: $file"
done< <(inotifywait -m -q -e create,modify,move,delete --format '%f' ~/Dropbox/Camera\ Uploads)

```
**Global variables**
You are referencing at least 3 times the upload directory. I'd recommend putting it on a global var at the beginning of the script:
```
UPLOADS="$HOME/Dropbox/Camera\ Uploads"
```
and then use "$UPLOADS" for all references.

**basename and awk to rename**
You would gain some performance if you use bash internal parameter substitution to manipulate strings. For example, to get the same results as 'basename' and the tail of a string separated by '/'. For instance:
```
photo=${photo##*/}
...
temp_name=$(jhead -n%Y-%m-%d\ %H:%M:%S $HOME/Dropbox/Camera\ Uploads/"$photo")
named_photo=${temp_name##*/}
```
more info [here]("http://tldp.org/LDP/abs/html/string-manipulation.html") and [here]("http://www.thegeekstuff.com/2010/07/bash-string-manipulation/").

**sleep twice?**
Unless you planed it that way, you are waiting 5mins the first time and then 10m for the rest. If that is not the case you may simple remove one of the 'sleep' to always wait the same. If you go with the inotify approach, you wouldn't need the sleep BTW

There you go. All comments made with the best intentions.

Kind Regards.

P.S.: I also learned something new: the 'jhead' command, thanks ;)

---

### Post by Lars Noodén on 2014-06-28
Rather than looping, you could use [inotify](http://www.cyberciti.biz/faq/linux-inotify-examples-to-replicate-directories/) to launch your script whenever files are added or deleted to the directory being watched.  Do that by setting up an [incrontab](http://manpages.ubuntu.com/manpages/trusty/en/man5/incrontab.5.html) entry.

---

### Post by CaptainMark on 2014-06-29
Thanks very much for your advice, I have implemented your suggestions about the global variables and using built in bash to obtain the filenames, very useful.

I am sceptical about inotify, it appears to use the same services as incrontab which I have used before and found to be more or less broken, (If memory serves correctly it struggles to pass arguments with spaces to your scripts, even when you quote them) this was a long time ago so I will take another look and see if it works. Additionally I don't mean to pick holes, but just to query, if the inotifywait is monitoring for MOVE events and its actions are to move the file out of the watch directory, won't file be permanently iterated over and over? I've tried it with moved_to event monitoring and it seems to work well so far.

Many Thanks,


EDIT: I've played around a little more, I don't think inotify is going to work for me, in the middle of the while loop when jhead renames the file, this counts as a move event so it queues the file in inotifywait for a second iteration which fails miserably, I've tried to stop it from doing that but everything I try seems be a bit of a dirty hack, additionally I can't mv the file out and THEN rename it, because I have shotwell monitoring the destination folder so I need to photos to be moved into its final destination readily named, otherwise shotwell finds the photo under one name, and then loses it when it's renamed.

What a drama, I think I'll stick with the sleep waits for now unless I can figure a good way round this.

---

### Post by CaptainMark on 2014-06-29
Not being one to give up, I've realised that if I don't use jhead to rename the file in the middle then everything works okay, the renaming is done by the final mv command which obtains the final file name from the $timestamp variable, so I've got all bases covered here, 
my final niggle, which I'd like some pointers with, is: Can I easily substitute the variable $new_photo_name in it's "YYYY:MM:DD HH:MM:SS.jpg" format to this format instead "YYYY-MM-DD HH:MM:SS.jpg" notice the hyphens instead of colons in the date (Damn smilies, thats a seperate ':' and 'D').

If it's easy enough to do great but if it's hard then I won't worry too much about it, it's only because every photo I've taken in the last two years has the same name format and I'm a stickler for uniformity.

Here is the current code

```

#!/bin/bash
 #~ run on: desktop
 #~ Photo Sorter
 #~ A script to sort photos in date ordered directories
 #~ Mark Skinner
 #~ Created 04/03/2012
 #~ last modified 27/06/2014
 #~ Requires jhead to be installed
 #~ ideas: add a notifier upon any failures, add a check for duplicates feature incase the photo exists already


set -x
#~ Global Variables
UPLOADS=$HOME/Dropbox/Camera\ Uploads






# variables
count=0
no_timestamp=0
duplicate=0


# determine files for iteration
while read -r photo_path ; do
    # obtain photo timestamp
    timestamp=$(jhead "$photo_path" | grep Date/Time)
    # obtain year and month
    year=${timestamp:15:4}
    month=${timestamp:20:2}
    # create new_photo_name variable
    new_photo_name=${timestamp:15:19}
    # mv photo to new location
    if [ ! -z "$new_photo_name" ] && [ ! -z "$year" ] && [ ! -z "$month" ]; then
        mkdir -p $HOME/Pictures/$year/$month; mv -n "$photo_path" $HOME/Pictures/$year/$month/"$new_photo_name".jpg
    fi
    unset timestamp year month new_photo_name
    
done< <(inotifywait -m -q -e create,moved_to --format '%w%f' "$UPLOADS")

```

Note: The unused variables at the start are for a feedback system I plan to implement via notify-send so ignore them for now

---

### Post by papibe on 2014-06-29
> **CaptainMark said:**
> "YYYY:MM:DD HH:MM:SS.jpg" to this format instead "YYYY-MM-DD HH:MM:SS.jpg"
There's a lot of string manipulation examples in the section 'Substring Replacement' of the first page I linked on post #2.

To replace all occurrences of the character ':' for a '-' you use the following structure:
```
${string//substring/replacement}
```
For instance:
```
$ var="2014:06:29 20:07:45"
$ newvar="${var//:/-}"
$ echo "$newvar"
2014-06-29 20-07-45
```
Which it is close, but not perfect (hour-min-sec got changed).

If you consider that you can separate the variable into an array, and then replace only in the first part, you could do this:
```
$ var="2014:06:29 20:07:45"
$ arr=($var)
$ newvar="${arr[0]//:/-} ${arr[1]}"
$ echo "$newvar"
2014-06-29 20:07:45
```
Hope it helps.
Regards.

---

### Post by CaptainMark on 2014-06-30
Thanks for the advice, I continued looking into it and the method I came up with is similar to yours```

new_photo_name=${timestamp:15:19}
new_photo_name[COLOR=#000000][FONT=Ubuntu Mono]="${new_photo_name/:/-}"
[/FONT][/COLOR]new_photo_name[FONT=Ubuntu Mono][COLOR=#000000]="${new_photo_name/:/-}"[/COLOR][/FONT]
```
just replacing the first instance of : to - twice over.
[FONT=arial][COLOR=#000000]I'm happy with this now, using inotify is working great and has certainly improved the effectiveness of the script.

Regards
Mark [/COLOR][/FONT]

---

### Post by slonk on 2014-06-30
The time parsing is fragile.  At the very least I would put a `jhead foo | grep bar | head -1` so that you don't get flooded with possibly new or undocumented additional EXIF fields (which I think will show up later than the standard fields).

You can also feed the timestamp through a short pattern match and bail if it isn't what you expected.

---

### Post by CaptainMark on 2014-07-03
> **slonk said:**
> You can also feed the timestamp through a short pattern match and bail if it isn't what you expected.That's a good idea, I'll do that this weekend. Thanks

---

