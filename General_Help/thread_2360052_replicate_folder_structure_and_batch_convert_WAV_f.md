---
title: "replicate folder structure and batch convert WAV files to MP3 with original timestamp"
date: 2017-05-01
forum: General Help
---

### Post by alain.roger on 2017-05-01
Hello,

I'm trying to save hard disk space by converting all my WAV files to MP3 format.
In order to do that i would like:

1. to replicate the folder (with sub-folders and files) structure to another folder AND keeping timestamp of original files.
2. list all WAV files in the new structure and in a batch to convert them to MP3 format AND add date and time to the beginning of the file (format: YYYY-MM-DD_HH-MM-SS_originalfilename.mp3).

for that purpose i started to create a script as following:
```

#!/bin/bash


# Convert all WAV files from main directory (and sub-directories) into MP3


# variable without spaces between = and text


# original directory to convert
dir_original="rec"
dir_converted="converted"


#for f in *.wav
#do
#    mv -n "$f" "$(exiftool -d "%Y-%m-%d_%H-%M-%S_" -CreateDate "$f" | awk '{print $4".jpg"}')"
#done


clear
echo "01. Delete former converted directory content"
rm -rf $dir_converted


echo
echo "02. Creation of new converted directory"
mkdir $dir_converted


echo
#echo "03. Copy content of original folder to converted folder \n"
#cp -r --preserve=timestamps $dir_original/* $dir_converted


echo
echo "03. Rename all files of converted folder with creation date and time at their name beginning"


#cd $dir_converted


for file in `ls -1 *.wav`
  do name=`stat -c %y $file | awk -F"." '{ print $1 }' | sed -e "s/\-//g" -e "s/\://g" -e "s/[ ]/_/g"`.wav
  cp -r --preserve=timestampcp $dir_original/$file $dir_converted/$name
done


echo

```

but if previous step 03 kept timestamp of files, the new step 03 does not do it.
any help would be appreciated.

thx

---

### Post by TheFu on 2017-05-01
I think only root can keep timestamps. Check the cp manpage to be certain. Also, the file system will need to support that.

I'd use rsync and lame and prepending the timestamp doesn't require any sed action at all.  Lame accepts an output location, so there isn't any reason to copy the WAV files, unless there is some other reason for doing it.  Of course, there are 500 ways to solve this issue.

BTW, there are problems with the cp options. They are not correct.  '-p timestamps' or '--preserve=timestamps' is what my manpages say.

Where you planning to put ID3 tags into the files?  Why mp3 instead of ogg or vorbis?  mp3 is a little dated. Vorbis is the best lossy format for audio files today, according to all the data I've been reading.  The webm video files use vorbis for audio tracks, so it is well supported on most players. Can't speak for Apple stuff. Don't have any.

---

