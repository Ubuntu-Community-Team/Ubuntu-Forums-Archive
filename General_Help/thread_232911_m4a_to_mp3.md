---
title: "m4a to mp3"
date: 2006-08-09
forum: General Help
---

### Post by Lunar_Lamp on 2006-08-09
I want to convert a lot of m4a files to mp3 as my mp3 player doesn't support m4a.

I know vaguely how to do it, but as a have >1000 files I want to automate it.  What I want to do is set the script to search in my /home/usr/music folder for m4a files and convert all m4a files to mp3, and then delete all the m4a files.  Would the following script work:

```
#!/bin/bash

for i in *.m4a; do \
    ffmpeg -i "$i" -acodec mp3 -ac 2 -ab 128 "${i%m4a}mp3"; \
done

rm -rf /home/usr/folder-path/*m4a
```

I could just point this to a particular folder (I will have other folders that I do not want it to touch)?

---

### Post by Lunar_Lamp on 2006-08-10
Anyone have any ideas?

---

### Post by aeiah on 2006-08-10
why dont you just test it, rather than ask if it works? change your paths to a sample folder with say, 5 backed up songs in it that you dont mind borking if your script doesnt work right.

---

### Post by Lunar_Lamp on 2006-08-10
Well, I can convert files frm m4a to mp3 using the script I wrote, but I cannot get it to delve recursively into the folders.

I can write a script to delete all the m4a files afterwards ok.  Actually, it's just a single bash command:

```
find ~/Testing* -name "*.m4a" -exec rm -f {} \;
```

I just need to work out how to get the ffmpeg command to be executed recursively.  If I exectue the script in a folder with m4a's in it, the result is great, but I don't know how to make te script look into the subdirectories of my current location.

I almost have it with this:

```
find ~/Testing* -name "*.m4a" -exec ffmpeg -i "$i" -acodec mp3 -ac 2 -ab 128 "${i%m4a}mp3" {} \;
```

The problem being that the ffmpeg command requires the filename to be included, which at the moment is $i in the line above, but that will not work as $i hasn't been described previously.

---

### Post by Lunar_Lamp on 2006-08-10
This is what I have at the moment.  It works, I just need to make the last line work - if I leave it out I end up with a load of files called filename.m4a.mp3 and I want to rename them to filename.mp3.

```

#!/bin/bash

#converts the files to mp3's
find ~/Testing* -name "*.m4a" -exec ffmpeg -i {} -acodec mp3 -ac 2 -ab 128 "{}.mp3" \;

#removes the mp3 files
find ~/Testing* -name "*.m4a" -exec rm -f {} \;


#this line DOES NOT WORK
find ~/Testing* -name "*.m4a" -exec mv {} {{i%m4a}mp3} \;


```

---

### Post by Lunar_Lamp on 2006-08-10
OK, I worked it out eventually:

```
#!/bin/bash

#converts the files to mp3's
find ~/Testing* -name "*.m4a" -exec ffmpeg -i {} -acodec mp3 -ac 2 -ab 128 "{}.mp3" \;

#removes the m4a files
find ~/Testing* -name "*.m4a" -exec rm -f {} \;

#renames files to get rip of the m4a part
find ~/Testing/ | perl -ne'chomp; next unless -e; $oldname = $_; s/.m4a.mp3/.mp3/; next if -e; rename $oldname, $_'



```

---

### Post by patwack on 2006-08-10
hi i tried out this script as i've been trying to figure out how to do this for a while but i end up with this error when running it
```

ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --extra-cflags=-fomit-frame-pointer -DRUNTIME_CPUDETECT --build i486-linux-gnu --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --prefix=/usr
  built on Nov 24 2005 10:19:02, gcc: 4.0.3 20051121 (prerelease) (Ubuntu 4.0.2-4ubuntu3)
Input #0, mov,mp4,m4a,3gp,3g2, from '/home/paddy/Testing/7 - Rat Salad.m4a':
  Duration: 00:02:30.5, start: 0.000000, bitrate: 129 kb/s
  Stream #0.0: Audio: mp4a / 0x6134706D, 44100 Hz, stereo
Output #0, mp2, to '/home/paddy/Testing/7 - Rat Salad.m4a.mp3':
  Stream #0.0: Audio: 0x0000, 44100 Hz, stereo, 128 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Unsupported codec for output stream #0.0

```

it leaves me with mp3 files that nautilus thinks are plain text but more alarmingly 0bytes in size, any ideas?

Thanks, Paddy

---

### Post by fletc900 on 2006-08-13
Hi there,
I wrote some code in Python that converts your m4a files to mp3. The program searches recursively for m4a files in your working direcotry and converts them to mp3. I have uploaded the code here:
 [http://ubuntuforums.org/attachment.php?attachmentid=14251&d=1155502600]("http://ubuntuforums.org/attachment.php?attachmentid=14251&d=1155502600"). 

Extract the files and look @ the README file for instaltion/usage instructions.



Cheers!;)

---

### Post by Lunar_Lamp on 2006-08-15
patwack: your problem is with ffmpeg.  It is having problems converting the files, i.e. it's having problems converting your m4a to mp3.

You need to work out what's happening there.

The line you want to experiment is:

ffmpeg -i M4AFILE -acodec mp3 -ac 2 -ab 128 CONVERTEDFILENAME

Try man ffmpeg for more info.


Oh, and if you want to change the script to search your present working directory and subdirectories, just change ~/Testing* to $PWD (I think).

---

