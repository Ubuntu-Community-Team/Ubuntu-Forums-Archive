---
title: "Find all image files in a directory..."
date: 2007-06-12
forum: General Help
---

### Post by Rocketeer on 2007-06-12
Hi there,
I am writing a script which creates thumbnails of all images on the drive. The creation of the images works fine, but only for one fileextension per call.

To get the list for the process i call

> find * -iname \*.JPG

But I want also have the files with extensions like PNG, TIF, PSD etc etc. - I was not able to manage to get this working. I also considered using identify (from the ImageMagick library) but it does not give back a status code, so it's not quite easy or am i wrong?

How would you do that?

My current script looks like this:

```
#!/bin/bash
for f in `find * -iname \*.JPG -iname \*.PSD -printf "%h/%f\n" |grep -v _thumb`;
do
        BASE=`basename $f`;
        DIR=`dirname $f`;
        if [ ! -f _thumb/$DIR/$BASE ]
        then
                echo -n Converting \'$f\' ...;
                mkdir -p _thumb/$DIR
                convert -format jpeg -strip -quality 80 -thumbnail 800x800 $f _thumb/$DIR/$BASE.jpg
                echo OK;
        else
                echo \'$f\' already converted.
        fi
done

```

---

### Post by stylishpants on 2007-06-12
First of all, you can shorten this up by using a while loop instead of a for loop.  This solves the problem of filenames with spaces being split into multiple pieces, so you don't need that printf stuff anymore.

```

find . -iname \*.jpg | while read f; do echo "<$f>"; done

```


Next, I see you're trying to chain multiple -iname arguments together.  You have to separate each -iname argument with an "or" or "and" operator.  Use '-o' for 'or', and use '-a' for 'and'.

```

find . -iname \*.jpg -o -iname \*.png -o -iname \*.tiff

```


Now, this can get kind of long, so it would probably be more readable to use a single grep instead of a lot of chained -iname flags:

```

find . -type f | egrep -i "\.(png|jpg|tif|psd)$"

```

So the first line of your script would look like this:
```
find . -type f | egrep -i "\.(png|jpg|tif|psd)$" | grep -v _thumb | while read f;
```


Your next problem is that you're getting all these different file types, but your 'convert' command specifies '-format jpeg'.  You better take that out.  I think that convert can automatically recognize the input file format.

---

### Post by Rocketeer on 2007-06-15
Now thats a solution with a very exact explanation. Thank you a lot! :popcorn:

---

