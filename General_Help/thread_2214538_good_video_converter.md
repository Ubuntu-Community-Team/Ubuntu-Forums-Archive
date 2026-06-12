---
title: "good video converter?"
date: 2014-04-01
forum: General Help
---

### Post by princeofnam on 2014-04-01
I've been trying to batch convert AVI files to audio.  FFmpeg gives me errors and naturally ffwin isn't an option.  I can't seem to find an option to download Handbrake.  Does anyone have any recommendations?

---

### Post by su:bhatta on 2014-04-01
Handbrake can  be installed from PPA's :

[http://handbrake.fr/downloads.php](http://handbrake.fr/downloads.php)

Basically:

```
sudo add-apt-repository ppa:stebbins/handbrake-releases
sudo apt-get update
sudo apt-get install handbrake-cli handbrake-gtk
```

But the PPA's are upto Raring only, at least the launchpad page updates so..

Also found this :
[http://askubuntu.com/questions/107915/how-do-i-download-and-install-handbrake](http://askubuntu.com/questions/107915/how-do-i-download-and-install-handbrake)

This page lists 0.9.9 amd64 Deb files.

---

### Post by andrew.46 on 2014-04-01
> **princeofnam said:**
> I've been trying to batch convert AVI files to audio.  FFmpeg gives me errors [...]

It would be interesting to see the errors...

---

### Post by princeofnam on 2014-04-01
```

ffmpeg -i Musculoskeletal1.avi Muscule.mp3
ffmpeg version 0.8.10-6:0.8.10-0ubuntu0.13.10.1, Copyright (c) 2000-2013 the Libav developers
  built on Feb  6 2014 20:53:28 with gcc 4.8.1
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
[mpeg4 @ 0x21f15e0] Invalid and inefficient vfw-avi packed B frames detected
Input #0, avi, from 'Musculoskeletal1.avi':
  Metadata:
    encoder         : VirtualDubMod 1.5.10.3 | www.virtualdub-fr.org || (build 2550/release)
  Duration: 00:25:16.96, start: 0.000000, bitrate: 1116 kb/s
    Stream #0.0: Video: mpeg4 (Advanced Simple Profile), yuv420p, 1366x768 [PAR 1:1 DAR 683:384], 25 tbr, 30 tbn, 25 tbc
    Stream #0.1: Audio: pcm_s16le, 22050 Hz, 1 channels, s16, 352 kb/s
Output #0, mp3, to 'Muscule.mp3':
    Stream #0.0: Audio: [0][0][0][0] / 0x0000, 22050 Hz, 1 channels, s16, 200 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
Encoder (codec id 86017) not found for output stream #0.0


```

---

### Post by andrew.46 on 2014-04-02
Looks like you are missing an mp3 encoder. This can be rectified by installing the 'extra' packages that are available for FFmpeg:

```

sudo apt-get install libavcodec-extra-53

```

and this might kick FFmpeg into life :)

---

### Post by princeofnam on 2014-04-02
also i'm pretty sure I added the correct repositories but..

```

sudo apt-get install handbrake-cli handbrake-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package handbrake-cli
E: Unable to locate package handbrake-gtk

```

 
also thanks for the mp3 fix.  Works like a dream.  Had to use WinFF because I couldn't figure out how to batch convert. [http://ubuntuforums.org/showthread.php?t=867670&page=2](http://ubuntuforums.org/showthread.php?t=867670&page=2) has some answers but they're kinda convoluted.  Does anyone here happen to know how to batch convert via command line?

---

### Post by su:bhatta on 2014-04-02
Just installed Handbrake from the deb file provided in this link(bottom of Page, AMD 64 Deb for Quantal):
 [http://askubuntu.com/questions/107915/how-do-i-download-and-install-handbrake](http://askubuntu.com/questions/107915/how-do-i-download-and-install-handbrake)
 and it was launched without any problem.

Just give that a try if you want Handbrake.

---

### Post by Portaro on 2014-04-02
Maybe this works , any you need is mencoder and lame, and input methods is->
target the script on console

avitomp3.sh /file source to convert filetype

exxample ->

avitomp3.sh /home/user/your..avi avi2mp3

The file can be used also to convert 
flv to avi.
wmv to avi


I hope works well,I put the code on other answer

---

### Post by Portaro on 2014-04-02
```

#!/bin/bash                                                      
#SCRIPT Convert video flv to avi audio extract of avi convert wmv to avi                                      
 
if [ $1 = "--help" -o $1 = "-h" ]; then         #User call help of script
        echo "Convert video and audio files. Needs mencoder and lame."
        echo "Commands:"                                                                              
        echo "videoconverter.sh archive.flv flv2avi. To convert  flv on avi."                  
        echo "videoconverter.sh archive.flv avi2mp3. To extract audio of an avi."                
        echo "videoconverter.sh archive.flv wmv2avi. To convert wmv on avi."
        exit
elif [ -z $1 -o -z $2 ]; then                   #Not find a local or parameter
        echo "The script needs two inputs: 1º name of archive to convert, 2º filetype of conversion. Try --help "
        exit
elif [ -e $1 ];then                             #The archive exists???
        if [ -r $1 ]; then                      #The archive can be read???
                newarchive=`echo $1 | cut -d. -f1`
                if [ $2 = "flv2avi" ]; then     #Conversion flv to avi
                        echo "Conversion $1 to $newarchive.avi"
                        mencoder $1 -oac mp3lame -ovc xvid -lameopts preset=standard:fast -xvidencopts pass=1 -o $newarchive.avi
                        if [ -e $newarchive.avi ]; then
                                echo "Archive $newarchive.avi Done!"
                        else
                                echo "Error when create the new archive $newarchive.avi!"
                        fi
 
                elif [ $2 = "avi2mp3" ]; then   #Extract audio of avi
                        echo "Conversion $1 to $newarchive.mp3"
                        mencoder "$1" -of rawaudio -oac mp3lame -ovc copy -o "$newarchive.mp3"
                        if [ -e $newarchive.mp3 ]; then
                                echo "Archive $newarchive.mp3 Done!"
                        else
                                echo "Error when create the new archive $newarchive.mp3!"
                        fi
 
                elif [ $2 = "wmv2avi" ]; then   #Convert wmv to avi
                        echo "Conversion $1 to $newarchive.avi"
                        mencoder $1 -ofps 23.976 -ovc lavc -oac copy -o $newarchive.avi
                        if [ -e $newarchive.avi ]; then
                                echo "Archive $newarchive.avi Done!"
                        else
                                echo "Error when create the new archive $newarchive.avi!"
                        fi
                else
                        echo "Unable to find 2º parameter use --help."
                fi
        else
                echo "The file not loaded"
        fi
else
        echo "The file don't exist"
fi

```

---

### Post by SeijiSensei on 2014-04-02
> **princeofnam said:**
> also i'm pretty sure I added the correct repositories but..

```

sudo apt-get install handbrake-cli handbrake-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package handbrake-cli
E: Unable to locate package handbrake-gtk

```


Perhaps you didn't run "sudo apt-get update" first?  You need to update the package lists after adding a new repository.

---

### Post by andrew.46 on 2014-04-02
> **princeofnam said:**
> also thanks for the mp3 fix.  Works like a dream.  Had to use WinFF because I couldn't figure out how to batch convert. [http://ubuntuforums.org/showthread.php?t=867670&page=2](http://ubuntuforums.org/showthread.php?t=867670&page=2) has some answers but they're kinda convoluted.  Does anyone here happen to know how to batch convert via command line?

That perl stuff seems a little over the top :). Perhaps something like this:

```

for j in *.avi
do 
ffmpeg -i "$j" -c:a libmp3lame -ac 2 -qscale:a 2 -ar 44100 "${j%.avi}.mp3"
done

```

There is room for adjustment with this for loop (and I am not completely sure of the syntax for your version of avconv as I actually use the git FFmpeg)  but it should get you started I hope...

---

