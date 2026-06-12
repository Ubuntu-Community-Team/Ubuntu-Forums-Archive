---
title: "imagemagik batch script"
date: 2013-04-29
forum: General Help
---

### Post by supersopa on 2013-04-29
Hi everyone!

I am trying to make a flexible bash batch script using convert for manage pics.

```
# FOR RESIZING: change/remove -resize option for decide about resizing
# FOR CONVERSION: change the extention into the last string if you want (also) convert into another format
# remove "converted" if you want overwrite the existing files
# you can define which files you want modify by editing the first string. if you specify *.* all files will be modified
# see $man convert for more string options

#!/bin/bash
for i in *.*; do convert $i -resize 25% $(basename $i)converted.jpg; done
```

if the file name(s) contain spaces this script does not work! how can I fix it?

can you suggest me any better batch script about imagemagik/convert?

thanks guys!

---

### Post by Vaphell on 2013-04-29
rule of thumb: put all your variables in ""

when you do something like this
```
i='abc 001.jpg'
convert **$i** -resize 25% $(basename $i)converted.jpg
```
after substitution you get this
```
convert [COLOR="#008000"]abc[/COLOR] [COLOR="#0000FF"]001.jpg[/COLOR]  -resize 25% ....
```
ie, multiple parameters where 1 is expected. Double quotes prevent that


```
$ i='abc 001.jpg'
$ printf "[%s]\n" $i
[abc]
[001.jpg]
$ printf "[%s]\n" "$i"
[abc 001.jpg]
```

printf puts its parameter(s) in place of %s placeholder(s) so it can be used to easily show the difference between $var and "$var".

---

### Post by supersopa on 2013-04-29
thanks but right now I have resolved with this simple command

mogrify -resize 25% -quality 60 -format jpg *.jpg

know I would like to know the difference between the command convert and mogrify, can anyone help me?

---

### Post by Vaphell on 2013-04-29
afaik mogrify modifies the source file, while convert creates a modified copy.

[http://www.imagemagick.org/script/mogrify.php](http://www.imagemagick.org/script/mogrify.php)
> This tool is similiar to convert except that the original image file is overwritten (unless you change the file suffix with the -format option) with any changes you request.

---

