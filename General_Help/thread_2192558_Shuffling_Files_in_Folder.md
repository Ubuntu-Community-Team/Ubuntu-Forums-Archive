---
title: "Shuffling Files in Folder"
date: 2013-12-08
forum: General Help
---

### Post by sammyp90 on 2013-12-08
hi, i have a simple script that will play files in a folder however i  have been trying to shuffle the order using 'shuf' with no luck.

the current script is ```
#!/bin/bash


for file in $1/*
do
 omxplayer -o local "$file"
done


```
my 100 previous attempts are based on a line of code posted in another thread by steeldriver which is
```
while read -r -d $'\0' file; do echo play "$file"; done < <(shuf -ze *.mp3)
```
any ideas how i will get the functionality of this line of code in the bash script?

---

### Post by papibe on 2013-12-08
Hi sammyp90.

It's all in there. Try this:
```
#!/bin/bash

while read -r -d $'\0' song
do
    omxplayer -o local "$song"

done < <(shuf -ze "$1"/*.mp3)
```
Let us know if that works for you.
Regards.

---

### Post by sammyp90 on 2013-12-08
yeah some slight ajustments can get it working now thanks :)

any ideas how i would get this to include all sub folders (albums) aswell as the individual tracks inside selected folder?

---

### Post by evilsoup on 2013-12-08
> any ideas how i would get this to include all sub folders (albums) aswell as the individual tracks inside selected folder?

You can use the globstar shell option:

```

#!/bin/bash
shopt -s globstar

while read -r -d $'\0' song
do
    omxplayer -o local "$song"

done < <(shuf -ze "$1"/**/*.mp3)

```

---

### Post by sammyp90 on 2013-12-09
thanks [**[COLOR=#000000]evilsoup[/COLOR]**]("http://ubuntuforums.org/member.php?u=1175696")

this script works, but not perfectly sadly, sometimes it skips a load of tracks that are actually there, maybe because of the characters in the song maybe. sometimes it misses the 1st letter of the song, or half of it.

the output is like
```
File "/Eminem-WANTED-(Bootleg)-2010-[NoFS]/11-Rihanna Ft. Eminem - Love The Way You Lie Pt. II (Prod. By Alex Da Kid) (Mastered).mp3" not found.
File "GaGa - The Fame Monster 2CDRip 2009 [Cov+2CD][Bubanee]/CD1/05. Dance In The Dark - Lady GaGa -.mp3" not found.
File "Deluxe Edition) (2013)/CD1/05 - Life For Rent.mp3" not found.
File "bird.mp3" not found.
File "ata/Media/Music//Queen - The Ultimate Best Of Queen (2011) [mp3][www.lokotorrents.com]/16. It's A Hard Life.mp3" not found.
File "d/data/Media/Music//Emeli Sandé - Read All About It, Pt. III.mp3" not found.
File "hdd/data/Media/Music//Akon Trouble/Akon - Trouble - Don't Let Up.mp3" not found.
File "key_do.mp3" not found.


```

any ideas why this is?

however will be marking this thread as solved as the original title is solved now, thanks guys

---

### Post by papibe on 2013-12-09
Glad you're making progress.

Could you post the actual code you're testing.

Since the list of files-not-found does not have the same starting path, my guess is that either you are quoting your bash variables, or you are not being consistent on using zero terminated string (shuf's option -z and read's option -d).

Regards.

---

