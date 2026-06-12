---
title: "[SOLVED] Nautilus Bash Script Involving Spaces in File Path"
date: 2008-06-10
forum: General Help
---

### Post by styyle14 on 2008-06-10
I have a bash script i am working on in order to extract audio from media files.  It is based on ffmpeg, and the script is working perfectly on all input files except those with spaces...  The main part of the script is the simple command: 
```
encode_audio (){
ffmpeg -i "$1" -vn -ac "$channels" -ab "$bitrate" "$name"."$format"
}
```

Since it is a Nautilus script, the variable $1 is given based on the files highlighted when the script was executed. I have options in place which have allowed me to test all the other variables, and it has been extensively tested on files without spaces in their name. As you can see, the variable is in quotes, yet it refuses to be accepted by ffmpeg...

I have tried all the the combinations of single and double quotes I could think of to no avail... I know there are ways of doing this using outside programs, or character substitution, yet I think there is most likely a simple explanation to my problems....

Any input would be greatly appreciated, its probably just a simple problem that I can't see, yet I have searched google and forums for the better bart of 5 hours and would greatly appreciate help to this problem...

After I finish with this script, it will go on gnome-look.org and other sites under GPL, so anyone can use it...

Here is the entirety of the code if it helps at all:
```
#!/bin/bash

title="Extract Audio"

if [ $# -eq 0 ]; then
	zenity --error --title="error" --text="You must select at least 1 file"
	exit
fi

ffmpeg_bin=`which ffmpeg | grep -c "ffmpeg"`

if [ $ffmpeg_bin -eq "0" ]; 
then
zenity --error --title="::Error::" \
 --text="You do not have the ffmpeg package installed
Please install it in order to use this script. 
Make sure that the Universe repositories are enabled and
then type: 'sudo apt-get install ffmpeg' at a terminal."
exit
fi

encode_audio (){
ffmpeg -i "$1" -vn -ac "$channels" -ab "$bitrate" "$name"."$format"
}

option1="Choose your own"

while [ 'true' ]; do

format="mp3"
channels="2"
bitrate="128"

contin="1"

encode_type=`zenity --height="225" --title="$title" --text="Would you like to use the default encoding options or choose custom options?
(Default options are: same name as original, $format format, $bitrate kb/s, $channels channels)
Next File: $1" --list --radiolist --column="" \
--column="Name" \
TRUE "all default" \
FALSE "single default" \
FALSE "single default with custom name" \
FALSE "single custom" `

if [ ! "$encode_type" ]; then 
exit
fi

if [ "$encode_type" = "all default" ] && [ "$contin" = "1" ]; then
while  [ $# -gt 0 ]; do
filename=${1%.*}
name="$filename"
encode_audio $1
shift
done
exit
fi

if [ "$encode_type" = "single default" ] && [ "$contin" = "1" ]; then 
filename=${1%.*}
name="$filename"
encode_audio $1
shift
contin="0"
if [ $# -le 0 ]; then
exit
fi
fi

if [ "$contin" = "1" ]; then
filename=${1%.*}
name=`zenity --title="$title" --text="How would you like to name your file?" --list --radiolist --column="" \
--column="Name" \
TRUE "$option1" \
FALSE "$filename" `

if [ "$name" = "$option1" ]; then 
name=`zenity --title="$title" --text="Name of new file (without extension):" --entry `
fi

if [ "$encode_type" = "single default with custom name" ] && [ "$contin" = "1" ]; then 
encode_audio $1
shift
contin="0"
if [ $# -le 0 ]; then
exit
fi
fi
fi

if [ "$contin" = "1" ]; then
format=`zenity --title="$title" --text="Which audio format would you like to convert to?" --list --radiolist --column="" \
--column="Name" \
TRUE "mp3" \
FALSE "ogg" \
FALSE "flac" \
FALSE "wav" \
FALSE "wma" \
FALSE "$option1" `

if [ "$format" = "$option1" ]; then 
format=`zenity --title="$title" --text="Type the extension of the audio format you wish to use:
(Must be ffmpeg compatible)" --entry `
fi

if [ ! "$format" ]; then 
zenity --error --title="::Error::" --text="Please choose a format for the new audio file and try again." 
exit
fi

bitrate=`zenity --title="$title" --text="At what bitrate would you like to encode this file?
(Currently this script only handles mp3 and wma bitrates because the other formats have VBR's)" --list --radiolist --column="" \
--column="Name" \
FALSE "64" \
TRUE "128" \
FALSE "192" \
FALSE "240" \
FALSE "320" \
FALSE "$option1" `

if [ "$bitrate" = "$option1" ]; then 
bitrate=`zenity --title="$title" --text="Type the bitrate you wish to use:
(Must be ffmpeg compatible)" --entry `
fi

if [ ! "$bitrate" ]; then 
zenity --error --title="::Error::" --text="Please choose a bitrate for the new audio file and try again." 
exit
fi

channels=`zenity --title="$title" --text="How many channels would you like your file to have?" --list --radiolist --column="" \
--column="Name" \
FALSE "1" \
TRUE "2" \
FALSE "$option1" `

if [ "$channels" = "$option1" ]; then 
bitrate=`zenity --title="$title" --text="Type the number of channels you wish to use:
(Must be ffmpeg compatible)" --entry `
fi

if [ ! "$channels" ]; then 
zenity --error --title="::Error::" --text="Please choose a number of channels for the new audio file and try again." 
exit
fi

encode_audio $1

if [ $# -le 0 ]; then
exit
fi
fi
shift

done
exit
```

---

### Post by HalPomeranz on 2008-06-10
You can get the script to not treat spaces in file names as special by setting the IFS variable near the top of your script:

```

IFS=$'\t\n'

```

Normally IFS is set to space, tab, and newline-- the characters used to separate arguments in a normal shell command-line.  If we use the code above to set IFS to just tab and newline, then the spaces in your file names will no longer interfere with the proper handling of these files.

---

### Post by styyle14 on 2008-06-10
Thanks, that is exactly what I was looking for.  What would be the default value of IFS, in case it needs to be returned to its original value later in the script? I was thinking that in my encode_audio function I could change IFS to equal IFS=$'\t\n' at the beginning, and then at the end of the function change it back to it original settings... What would that be?

---

### Post by HalPomeranz on 2008-06-10
> **styyle14 said:**
> Thanks, that is exactly what I was looking for.  What would be the default value of IFS, in case it needs to be returned to its original value later in the script? I was thinking that in my encode_audio function I could change IFS to equal IFS=$'\t\n' at the beginning, and then at the end of the function change it back to it original settings... What would that be?

The default setting is:

```

IFS=$' \t\n'

```

Notice that there's a literal space character between the first quote and the "\t".

In general, however, you won't need to reset this variable back to its default settings.  The setting in the script only lasts for the lifetime of the script and goes away as soon as the script exits.

---

### Post by styyle14 on 2008-06-10
Thanks a bunch for all your help, once I define the dimensions of the zenity boxes and add some annotations to the script, I thinks it should be good to go.  Thanks for your quick response too!!!

---

