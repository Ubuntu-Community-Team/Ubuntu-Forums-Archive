---
title: "Command to name files sequentially?"
date: 2012-11-03
forum: General Help
---

### Post by Stonecold1995 on 2012-11-03
I'm making a script that has to create a file but has to name it like all the other files in the directory sequentially.  So if a directory has file01.txt, file02.txt, and file03.txt, the script has to name the new file file04.txt.  And if it adds another file later it would be named file05.txt.  What command do I use to do that?

---

### Post by StephGbzh on 2012-11-03
Here are several elements that you could use to make your script.

If you are sure you will always have a complete set of files beginning at 1 and incrementing by 1 for each new file, you just have to count the files:
```
ls | wc -l
```

If some files are missing (eg: file02.txt, file05.txt and file07.txt are missing), you have to take the last one and extract the number from its name:
```
ls | tail -1 | sed -r 's/^[^0-9]*([0-9]*).*$/\1/'
```
(this assumes you put only one number in the filename!)

Once you have this number, you can increment it like this in your script:
```
let INDEX+=1
```

Good luck!

---

### Post by Stonecold1995 on 2012-11-03
How do I make it work if there's a gap?  So if I have 01, 02, and 04, it'll create 03?

Also, "let INDEX+=1" (or "INDEX=$(($INDEX + 1))") doesn't work because it won't keep zero-padded files.  So if I have 004 it'll give out 5, but I want 005.  I know how to zero-pad files but is there an easier way?

---

### Post by Vaphell on 2012-11-03
unfortunately you have to do it the hard way. When you cast the string to number to increment, it will lose the information about its format so you need to restore padding later.
```
**$ ls**
001.txt  002.txt  004.txt
[B]$ n=1; w=3
$ for f in *.txt; do i="$( printf "%0${w}d" $n )"; [[ $f =~ .*$i[.].* ]] || break; (( n++ )); done
$ printf "%0${w}d.txt\n" $n[/B]
003.txt
[B]$ > 003.txt
$ ls[/B]
001.txt  002.txt  003.txt  004.txt
[B]$ n=1; w=3
$ for f in *.txt; do i="$( printf "%0${w}d" $n )"; [[ $f =~ .*$i[.].* ]] || break; (( n++ )); done
$ printf "%0${w}d.txt\n" $n[/B]
005.txt

```
example above jumps out of the loop as soon as it finds first mismatch or ends naturally when everything is peachy. Value 'returned' is the index where the gap was spotted or TOTAL+1 if no gaps were found.

---

### Post by Stonecold1995 on 2012-11-03
> **Vaphell said:**
> unfortunately you have to do it the hard way. When you cast the string to number to increment, it will lose the information about its format so you need to restore padding later.
```
**$ ls**
001.txt  002.txt  004.txt
[B]$ n=1; w=3
$ for f in *.txt; do i="$( printf "%0${w}d" $n )"; [[ $f =~ .*$i[.].* ]] || break; (( n++ )); done
$ printf "%0${w}d.txt\n" $n[/B]
003.txt
[B]$ > 003.txt
$ ls[/B]
001.txt  002.txt  003.txt  004.txt
[B]$ n=1; w=3
$ for f in *.txt; do i="$( printf "%0${w}d" $n )"; [[ $f =~ .*$i[.].* ]] || break; (( n++ )); done
$ printf "%0${w}d.txt\n" $n[/B]
005.txt

```
example above jumps out of the loop as soon as it finds first mismatch or ends naturally when everything is peachy. Value 'returned' is the index where the gap was spotted or TOTAL+1 if no gaps were found.

I tried using this to get the number, but it's not working:
```
alex@kubuntu:~/Pictures/Wallpapers/Beako$ ls
Beako 001.jpg  Beako 002.jpg  Beako 003.jpg
alex@kubuntu:~/Pictures/Wallpapers/Beako$ for f in *.*; do i="$( printf "%0${w}d" $n )"; [[ $f =~ .*$i[.].* ]] || break; (( n++ )); done
alex@kubuntu:~/Pictures/Wallpapers/Beako$ printf "%0${w}d\n" $n
0
```

I want the output to be "004", so I can do something like this:
```
filename="Beako $(function_to_get_filenumber).jpg"
mv newfile.jpg $filename
```

If it helps at all, I attached the script I'm trying to make.

---

### Post by Vaphell on 2012-11-03
you skipped
```
n=1; w=[COLOR="Blue"]3[/COLOR]
```
n is a starting value, if you don't set it to 1 it will compare 0 to the first file and jump out. w is the number width, you can plug it in directly if you don't need flexibility so the format is "%03d" not "%0[COLOR="Blue"]${w}[/COLOR]d".
```
$ ls *.jpg
Beako 001.jpg  Beako 002.jpg  Beako 003.jpg
$ n=1
$ for f in *.jpg; do i="$( printf "%0[COLOR="Blue"]3[/COLOR]d" $n )"; [[ $f =~ .*$i[.].* ]] || break; ((n++)); done
$ filename=$( printf "Beako %0${w}d.jpg" $n )
$ echo "$filename"
Beako 004.jpg

```

what is your scenario exactly? Do you need a single firstmost number or do you have a big bunch of randomly named files and you want to blend them with some tidily named set by filling gaps and/or adding at the end?

edit: i looked at the script but have trouble understanding logic behind it (or should i say i lack motivation to do so). Could you elaborate what should happen there?

```
./$(ps -p $$ | tail -1 | awk '{print $4}')
``` ?
how about **$0** ?

```
$( ls -l "$file" | awk '{print $5}' )
``` is not cool either because ls is for human eyes, not for scripts :)
if you want size:
```
$( stat -c %s "$file" )
```


edit #2:
try this
```
wallpapers="$HOME/Pictures/Wallpapers"   # main dir
directory="$wallpapers/$wallpapername"   # dir of selected wallpaper
w=3                                      # index width

# find firstmost unused index
n=0
while :
do
  (( n++ ))
  filename="$wallpapername $(printf "%0${w}d" $n ).jpg"
  [ -f "$directory/$filename" ] || break
done
# $filename now stores proper value
echo "$filename"
```

---

### Post by Stonecold1995 on 2012-11-04
Basically I'm just trying to make a script where I can enter a Wallpaper name and URL and it'll download and name the file correctly, and if the image is PNG it'll convert it to JPEG.  My wallpaper directory scheme is like this:
```
Pictures/
&#9492;&#9472;&#9472; Wallpapers
    &#9500;&#9472;&#9472; Pics
    &#9474;   &#9500;&#9472;&#9472; Pics 001.jpg
    &#9474;   &#9500;&#9472;&#9472; Pics 002.jpg
    &#9474;   &#9492;&#9472;&#9472; Pics 003.jpg
    &#9500;&#9472;&#9472; Stuff
    &#9474;   &#9500;&#9472;&#9472; Stuff 001.jpg
    &#9474;   &#9500;&#9472;&#9472; Stuff 002.jpg
    &#9474;   &#9492;&#9472;&#9472; Stuff 003.jpg
    &#9492;&#9472;&#9472; Walls
        &#9500;&#9472;&#9472; Walls 001.jpg
        &#9500;&#9472;&#9472; Walls 002.jpg
        &#9492;&#9472;&#9472; Walls 003.jpg
```

The script is for downloading an image from a URL, putting it in the right directory, and naming it correctly.  So if I were to run "./script.sh Stuff www.example.com/pic_of_stuff.png" it will create "Stuff 004.jpg" and put it in the right directory.  But the only method of naming the zero-padded files correctly seems like a really round-about way to do it.

---

### Post by Vaphell on 2012-11-04
i figured the basics out
my code from edit #2 should be good and it's much cleaner than your hardcore destination=... line :)

>  But the only method of naming the zero-padded files correctly seems like a really round-about way to do it.
what is really roundabout way about it? the whole thing is done in a loop 3 lines long, and that's with detection of firstmost free space
(2 if you compress this:
```
  (( n++ ))
  filename="$wallpapername $(printf "%0${w}d" $n ).jpg"
```
to this:
```
filename="$wallpapername $(printf "%0${w}d" $(( ++n )) ).jpg"
```

Filesystems don't know what 'number' and 'format' is and you would want some automagical method that will do those things? Sorry, it's all strings of chars and they all look the same from the script's point of view. If there is a logic you need to tell the script about it and i don't think 3 trivial lines of code is too much.
Be glad printf is available, not having it would be a real pain with true roundabout feel to it ;)

---

### Post by Stonecold1995 on 2012-11-04
Well, I guess not roundabout so much as just confusing for me, I'm use to using echo.  Although I know about printf from my limited knowledge of C and Python, it's still hard for me to read (although I think I've got it mostly now).

I'm just having trouble finding out why the script isn't working, even when reading the output of "bash -x script.sh".

---

### Post by Vaphell on 2012-11-04
so what the code looks like now? did you use my snippet?
for debugging purposes sprinkle the script with echos liberally and print everything that moves to see if the variable values in the script fit expectations.

---

