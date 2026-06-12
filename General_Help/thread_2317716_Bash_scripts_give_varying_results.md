---
title: "Bash scripts give varying results"
date: 2016-03-18
forum: General Help
---

### Post by terry34 on 2016-03-18
Getting confused here. I've written some simple scripts to transcode videos that work perfectly some times, and not so great at other times. For example, I just ran "2mkv" against a single file is a separate folder, and got an error message upon completion that it could not move the original file to the directory "old", no such folder and yet the script quite clearly says on line 3 mkdir -p new and on line 4 mkdir -p old. Nowhere in the script are any folders removed.

I have another script that employs ffmpeg's af volumedetect to find the volume level and apply the difference between that and the ideal level of "0" (89 db). As bash does not handle floating decimal points I've had to call up bc to handle the mathematics end of things and, again, sometimes it adjusts the volume level and sometime it does not.

It isn't just my scripts. In Gnome Sudoku you can right click a square to enter in possible values, again, sometimes yes, sometimes no.

Now, I'm the kind of person who leaves their computer running 24/7, and have noticed that things usually work perfectly just after a boot or login, but if its been running for some hours it is more likely to act up and the only cure is to logoff (which occasionally fails) or reboot. In the meantime this has caused me endless hours of frustration.

Just how stable is xfce4? Is there anything I can do to make it more stable? Please do not suggest moving to unity or kde - tried them, hate them. I like a simple interface - I usually don't even change from the stock settings. No themes, no bouncy icons, just my wallpaper selection changing every 10 minutes. How about Openbox for stability? It has the right-click menu I like, and I don't mind tinkering to get the settings right. Anyone have a opinion/suggestion/magic wand?

Amd 64 bit /w 8 cores, 16 Gb Ram, Watercooled (so it is not overheating) 
Xubuntu 15.10 from clean install with all update.

---

### Post by QIII on 2016-03-18
What makes you think the Desktop Environment has anything to do with the behavior of your scripts?

Gnome Sudoku is probably developed by someone other than xubuntu.org or xfce.org.  Maybe there is a problem with it that is unrelated to either Xubuntu or xfce.

---

### Post by ajgreeny on 2016-03-19
Without knowing the whole sequence of the lines in the script it is difficult to know what is going on.

You could try using those two command lines as the first and second lines, prior to the actual transcoding line, and add a && at the end of each mkdir, so if that is unsuccessful the script will stop running.

Do you see any errors in terminal apart from the ones you mention about missing folders?
Are the pathways you are using for those folders definitely correct?

PS:  XFCE, in my opinion is extremely stable, configurable and my favourite DE at the moment.  I am using Xubuntu 14.04 but have the PPA for xfce-4.12 enabled, rather than the default xfce-4.10.

---

### Post by Nad_Fink on 2016-03-20
I have found Xfce to be very stable.  I use openbox currently and I like it very much.  If you post your script here, it might be of help.

---

### Post by terry37 on 2016-03-26
> **QIII said:**
> What makes you think the Desktop Environment has anything to do with the behavior of your scripts?

Gnome Sudoku is probably developed by someone other than xubuntu.org or xfce.org.  Maybe there is a problem with it that is unrelated to either Xubuntu or xfce.

Thanks for pointing that out. Ever since my depression worsened, thinking things out is five times harder. Basically what you're saying is that if a tv station is broadcasting a signal, it doesn't matter the make or model of your tv, the signal is always the same.

---

### Post by terry37 on 2016-03-26
> **ajgreeny said:**
> Without knowing the whole sequence of the lines in the script it is difficult to know what is going on.

You could try using those two command lines as the first and second lines, prior to the actual transcoding line, and add a && at the end of each mkdir, so if that is unsuccessful the script will stop running.

Do you see any errors in terminal apart from the ones you mention about missing folders?
Are the pathways you are using for those folders definitely correct?

PS:  XFCE, in my opinion is extremely stable, configurable and my favourite DE at the moment.  I am using Xubuntu 14.04 but have the PPA for xfce-4.12 enabled, rather than the default xfce-4.10.

Actually, I put a sleep statement in there before the mkdir and its been ok so far. This has stopped it from doing strange things like naming files after the file that was supposed to be made (and subsequently overwritten). Now the && is an excellent idea, I should use that.

---

### Post by QLee on 2016-03-26
> **terry34 said:**
> Getting confused here. I've written some simple scripts to transcode videos that work perfectly some times, and not so great at other times. For example, I just ran "2mkv" against a single file is a separate folder, and got an error message upon completion that it could not move the original file to the directory "old", no such folder and yet the script quite clearly says on line 3 mkdir -p new and on line 4 mkdir -p old. Nowhere in the script are any folders removed.


I can offer a possible answer that might help with your confusion. If the user running the script doesn't have permission to create a directory (folder) in the location (directory, folder) where the script tries to create a directory, it isn't going to be created.  [edit] I see from what you posted while I was typing that "timing" was a problem you had not yet considered.

It has been suggested that you post the script you are having trouble with. If you do that, then people can make suggestions on what to do to differently to accomplish your goals.

I understand that if your depression is getting worse it probably is getting much harder to think through these problems, I hope you are getting some help for that too.

---

### Post by terry34 on 2016-04-07
I managed to find a way around the directories not being created. I put each mkdir statement into an endless loop with only one means of escape - create the directory.

```


#!/bin/bash

until [ -d mkv ]; do
mkdir -p mkv ; if [[ -d mkv ]]; then break
else continue
fi
done

until [ -d original ]; do
mkdir -p original ; if [[ -d original ]]; then break
else continue
fi
done

i=1

if [[ $(find . -maxdepth 0 -type f  | wc -l) -eq 0 ]]; then break; else continue; fi
shopt -s nullglob nocaseglob
for filename in *.avi *.m4v *.mkv *.mov *.mp4 *.mpeg *.mpg *.wmv *.flv *.webm ; do
ffmpeg -i "$filename" -y -f matroska -r 29.97 -vcodec libx264 -vf scale=w=704:h=384 -aspect 16:9 -flags +loop -cmp chroma -b:v 1250k -maxrate 1M -bufsize 4M -bt 256k -refs 1 -bf 3 -coder 1 -me_range 16 -subq 7 -partitions all -g 250 -keyint_min 25 -level 30 -qmin 10 -qmax 51 -qcomp 0.6 -trellis 2 -sc_threshold 40 -i_qfactor 0.71 -acodec libvorbis -b:a 112k -ar 48000 -ac 6 ./mkv/"${filename%.*}".mkv
mv "$filename" ./original

done
```

I am no kind of code monkey, as you can see from the kludge above. Most of this was pieced together from various web searches, with the ffmpeg part lifted straight out of "winff" The i=1 was included with the two lines beginning wigh "shopt -s". I left it in even though it is never called because it does not real harm.

I have another script that gave me no end of grief. As you undoubtedly know you can apply a volume gain across audio tracks to even out the sound levels so you don't have extremes of high and low volumes. The is NO SUCH ANIMAL FOR VIDEO! (Sorry for yelling, but some people think there is such a thing. There is not.) 

One day I stumbled across references to an ffmpeg feature called "volumedetect". As the name implies to goes through a video clip, although I have also used it on mp3s, charting the high and low volume levels and outputs the difference between it and the "ideal" level arbitrarily called "0db", which translates to 89db in the real world. Instead of tacking a gain number for your player to apply on playback you have to recode the audio portion using "volume=" to apply the gain directly.

```

#!/bin/bash
$fm_import    

# This script uses ffmpeg's audio filters -af volumedetect and -af volume=
# to adjust audio levels. See man ffmpeg.
#
# Adjust volume levels

until [ -d clone ]; do
mkdir -p clone ; if [[ -d clone ]]; then break
else continue
fi
done
until [ -d original ]; do
mkdir -p original ; if [[ -d original ]]; then break
else continue
fi
done
until [ -d verify ]; do
mkdir -p verify ; if [[ -d verify ]]; then break
else continue
fi
done

i=1

if [[ $(find . -maxdepth 0 -type f  | wc -l) -eq 0 ]]; then break; else continue; fi
shopt -s nullglob nocaseglob
for filename in *.avi *.flv *.m4v *.mkv *.mov *.mp4 *.mpeg *.mpg *.wmv *.webm ; do
ffmpeg -y -i "$filename" -af volumedetect -report -f null /dev/null
grep -E "max_volume" ffmpeg*.log
sed -nr '/max_volume:/ s/.*[[:space:]]-?([[:digit:]\.]+)[[:space:]]+dB$/\1/p' ffmpeg*.log > ffmpegnew.log
s=$(<ffmpegnew.log)
cp "$filename" ./clone
ffmpeg -y -i "$filename" -af volume="$s" ./verify/"$filename"
mv "$filename" ./original
rm -f ff*.log

done

```

This one used to invoke bc (floating point calculator) to determine whether or not to recode the audio (applying gain to a file with a volume level of 0.0 yields -91db - total silence) half the time it would skip over the calculation yielding blood curdling screams from myself until I split it into two parts. The first command is essentially the same until the second invocation of ffmpeg - the one with "volume="$s" - where I replace the two lines with 
```

mkdir -p "$s"
mv "$filename" ./"$s"

```

I done know why it kept screwing up, but logging out/in before using really helped.

You may wonder why I included all this. I work very hard on this. My depression worsened from the stress and I would crash at the strangest times. I also had some most excellent help from people out there in Forumland. After all of that - especially the part about hitting the bed, my way of dealing with stress - it would be a shame to keep it to myself.

Copy some videos to a new directory and try them. See how they work for you. If you like them - share.

And to those who may be wondering, yes I am under a doctor's care for my depression. In fact, I have an appointment next week.

---

### Post by Bucky Ball on 2016-04-07
As this is a support thread in a support area, and you seem to be getting support now rather than sharing your experiences, might help your cause if you change the title of this thread to describe your issue. Edit first post> Go Advanced> Change title.

---

