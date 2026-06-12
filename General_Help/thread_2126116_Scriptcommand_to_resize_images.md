---
title: "Script/command to resize images?"
date: 2013-03-16
forum: General Help
---

### Post by Stonecold1995 on 2013-03-16
I have a large collection of images, but I'd like to be able to shrink them to under or equal to a maximum size (in both dimensions and file size).  Is there a command/set of commands I could use to do this?  I have to be able to shrink every image to under 500kb, and with dimensions with less or equal to 480,000 pixels (the amount in a 800x600 image).  What can I do to automate this, because doing it manually would take rougly 80 days at the speed I'd do it?  Is there some way I could do it in a script with GraphicsMagick?

Thanks.

---

### Post by Fintan on 2013-03-16
Have a look here:
[http://www.imagemagick.org/script/mogrify.php](http://www.imagemagick.org/script/mogrify.php)

I use mogrify all the time.

Hope that helps :)

---

### Post by guyr34 on 2013-03-16
You can use nautilus for this job.
Install the package nautilus-image-converter
Then you can select images, right clic and choose 'resize image'

---

### Post by Stonecold1995 on 2013-03-16
> **guyr34 said:**
> You can use nautilus for this job.
Install the package nautilus-image-converter
Then you can select images, right clic and choose 'resize image'
Can that automatically resize only images larger than [COLOR=#000000]480,000 pixels to that size or less automatically?  I don't want it to try and resize smaller images to that size, or re-encode images at that size, reducing the quality unnecessarily.
[/COLOR]

---

### Post by papibe on 2013-03-16
> **Fintan said:**
> I use mogrify all the time.
+1

First, backup your data because any command line error may be risky. Then:
```
mogrify -resize 800x600 *
```
Regards.

---

### Post by SeijiSensei on 2013-03-17
I prefer to use convert instead of mogrify and write the altered images to a separate directory.  Then if everything looks correct, you can delete the originals.

I posted a script [here](http://ubuntuforums.org/showthread.php?t=1951949&p=11814807&viewfull=1#post11814807) that rotates files in the portrait orientation to landscape and leaves the ones already in the landscape orientation alone.  With a couple of tweaks you could adapt it to your needs.

---

### Post by Stonecold1995 on 2013-03-17
> **papibe said:**
> +1

First, backup your data because any command line error may be risky. Then:
```
mogrify -resize 800x600 *
```
Regards.
I don't want to convert everything to exactly 800x600!  I want to scale any images that are larger than 480,000 pixels (the equivalent of 800x600) to that size or lower.  For example, if an image is 2400x800, it should be resized to 1200x400, *not* 800x600 (even though they have the same amount of pixels).  But if it's 400x300, it should be left alone.

I tried using "gm identify", but I can't seem to get it to output only the dimensions, and I can't use "awk {'print $number'}" because it won't work correctly if there's a space in the path.

---

### Post by Vaphell on 2013-03-17
```
#!/bin/bash

src=$HOME/Pictures
dest=$HOME/resized_files
limit=480000

mkdir -p "$dest"

for f in "$src"/*.{jpg,png}
do
  dim=$( identify "$f" | grep -Pow '[0-9]+x[0-9]+' | head -1 )
  w=${dim%x*}
  h=${dim#*x}
#  echo width:$w height:$h $((w*h))
  if (( w*h>limit ))
  then
    echo "* resizing '$f'"
    echo "width:$w, height:$h, pixel count:$((w*h))"
    scale=$( echo "sqrt( $limit/($w*$h))*100" | bc -l )
    scale=${scale:0:6}%
    echo scale:$scale
    rf=$dest/${f##*/}
    convert -scale "$scale" "$f" "$rf"
    rdim=$( identify "$rf" | grep -Pow '[0-9]+x[0-9]+' | head -1 )
    rw=${rdim%x*}
    rh=${rdim#*x}
    echo "* resized file '$rf'"
    echo "new width:$rw, new height:$rh, pixel count:$((rw*rh))"
    echo
  fi
done
```

i don't know what would happen when the img should be scaled to 2/3 of the original size (tidy fraction but infinite decimal form). Loss of precision from Sqrt() and trimming the $scale var might appear. You might want to try to use more digits ( *scale=${scale:0:**6**}%* ) or even skip trimming entirely *scale=${scale}%* )

---

### Post by Stonecold1995 on 2013-03-17
> **Vaphell said:**
> ```
#!/bin/bash

src=$HOME/Pictures
dest=$HOME/resized_files
limit=480000

mkdir -p "$dest"

for f in "$src"/*.{jpg,png}
do
  dim=$( identify "$f" | grep -Pow '[0-9]+x[0-9]+' | head -1 )
  w=${dim%x*}
  h=${dim#*x}
#  echo width:$w height:$h $((w*h))
  if (( w*h>limit ))
  then
    echo "* resizing '$f'"
    echo "width:$w, height:$h, pixel count:$((w*h))"
    scale=$( echo "sqrt( $limit/($w*$h))*100" | bc -l )
    scale=${scale:0:6}% 
    echo scale:$scale
    rf=$dest/${f##*/}
    convert -scale "$scale" "$f" "$rf"
    rdim=$( identify "$rf" | grep -Pow '[0-9]+x[0-9]+' | head -1 )
    rw=${rdim%x*}
    rh=${rdim#*x}
    echo "* resized file '$rf'"
    echo "new width:$rw, new height:$rh, pixel count:$((rw*rh))"
    echo
  fi
done
```

i don't know what would happen when the img should be scaled to 2/3 of the original size (tidy fraction but infinite decimal form). Loss of precision from Sqrt() and trimming the $scale var might appear. You might want to try to use more digits ( *scale=${scale:0:**6**}%* ) or even skip trimming entirely *scale=${scale}%* )

How do I get it to search recursively?  I think this would work but it seems really sloppy:
```
for f in "$src"/*.{jpg,png} "$src"/*/*.{jpg,png} "$src"/*/*/*.{jpg,png} "$src"/*/*/*/*.{jpg,png}; do
# code
done
```
Is there a better way to do that?

---

### Post by Vaphell on 2013-03-17
change to recursive mode is easy, i'll change it. i assume the output dir structure should reflect the structure of the source?

```
#!/bin/bash

[COLOR="#0000FF"]shopt -s globstar[/COLOR]

src=$HOME/Obrazy
dest="$HOME/resized_files"
limit=480000

mkdir -p "$dest"


for f in "$src"/[COLOR="#0000FF"]**[/COLOR]/*{jpg,png}
do
  dim=$( identify "$f" | grep -Pow '[0-9]+x[0-9]+' | head -1 )
  w=${dim%x*}
  h=${dim#*x}
  if (( w*h>limit ))
  then
    echo "* resizing '$f'"
    echo "width:$w, height:$h, pixel count:$((w*h))"
    scale=$( echo "sqrt( $limit/($w*$h))*100" | bc -l )
    scale=${scale:0:6}%
    echo scale:$scale
    [COLOR="#0000FF"]rf=$dest/${f#$src/}[/COLOR]
    convert -scale "$scale" "$f" "$rf"
    rdim=$( identify "$rf" | grep -Pow '[0-9]+x[0-9]+' | head -1 )
    rw=${rdim%x*}
    rh=${rdim#*x}
    echo "* resized file '$rf'"
    echo "new width:$rw, new height:$rh, pixel count:$((rw*rh))"
    echo
  fi
done
```

globstar ** is a bashism that matches 0 or more directories
alternative would be to use find + while read

```
while read -rd $'\0' f
do
   ...
done < <( find "$src" ... -print0 )
```

in case you have images with capitalized extensions (digital cameras often do that) you can use *shopt -s nocaseglob* so you don't have to explicitly list capitalized forms *{jpg,JPG,png,PNG} and all possible variations Jpg Png etc. or write the globs this way: ```
for f in "$src"/**/*.[jJ][pP][gG] "$src"/**/*.[pP][nN][gG]
```

---

### Post by Stonecold1995 on 2013-03-17
They're all like this:
```
* resizing '/path/to/image.jpg'
width:843, height:1471, pixel count:1240053
scale:62.215%
convert: Unable to open file (/path/to/image.jpg) [No such file or directory].
identify identify: Unable to open file (/path/to/image.jpg) [No such file or directory].
identify identify: Request did not return an image.
* resized file '/path/to/image.jpg'
new width:, new height:, pixel count:0
```

---

### Post by Vaphell on 2013-03-17
oh snap, i didnt think about that and didn't bother to check if the script works after the change.

after the *rf=...* line add
```
mkdir -p "${rf%/*}"
```

we need to make sure the destination dir for the output file exists, don't we? initial script had the *mkdir -p $dest* so it was ok for the unstructured output. In fact after this fix that initial *mkdir* line becomes obsolete - each file will have its dest dir created either way.

---

