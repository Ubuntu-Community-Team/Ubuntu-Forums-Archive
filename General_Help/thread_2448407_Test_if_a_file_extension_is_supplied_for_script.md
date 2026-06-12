---
title: "Test if a file extension is supplied for script"
date: 2020-08-07
forum: General Help
---

### Post by raleigh3 on 2020-08-07
How can I test if .jpg file extension is supplied?

```
#!/bin/bash
# 
#----------------------------------------------------------------------------
# Convert a jpg file(that is a scan of text like a book page) to a text file
#  Image MUST be a jpg file !!
#
#----------------------------------------------------------------------------

#!/bin/bash
clear
[ -z "$1" ] && {
echo 
echo -e "Error!! NO JPG SPECIFIED. !!"
echo
echo -e "Convert jpg to text file."
echo 
echo -e "Image2File.sh [name of jpg file WITHOUT file extension.]"
echo
exit 1; }
convert "$1.jpg" "$1.tiff" &&
tesseract "$1.tiff" "$1"
rm *.tiff
```

---

### Post by ActionParsnip on 2020-08-07
Something like this:
```

if [ ${file: -4} == ".jpg" ]
then
#      do stuff here
fi

```

---

### Post by ActionParsnip on 2020-08-07
[https://stackoverflow.com/questions/407184/how-to-check-the-extension-of-a-filename-in-a-bash-script](https://stackoverflow.com/questions/407184/how-to-check-the-extension-of-a-filename-in-a-bash-script)

---

### Post by aromo2 on 2020-08-07
> **raleigh3 said:**
> How can I test if a file extension is supplied?

```
#!/bin/bash
# 
#----------------------------------------------------------------------------
# Convert a jpg file(that is a scan of text like a book page) to a text file
#  Image MUST be a jpg file !!
#
#----------------------------------------------------------------------------

#!/bin/bash
clear
[ -z "$1" ] && {
echo 
echo -e "Error!! NO JPG SPECIFIED. !!"
echo
echo -e "Convert jpg to text file."
echo 
echo -e "Image2File.sh [name of jpg file WITHOUT file extension.]"
echo
exit 1; }
convert "$1.jpg" "$1.tiff" &&
tesseract "$1.tiff" "$1"
rm *.tiff
```

Try this:
```

EXTENSION=$( echo $1|egrep -o ".[a-z]+$" )
if [ -z "$EXTENSION" ] then
   # no extension provided
else
   # extension is $EXTENSION
fi

```

---

### Post by CatKiller on 2020-08-07
As another thing to consider; whether a file contains JPEG data is actually unrelated to what its name is. It's only by convention that JPEG files' names end with jpg, or jpeg, or JPG, or...

You could instead test for what type of file you're manipulating, rather than what it's called.

---

### Post by HermanAB on 2020-08-07
The file name is not a reliable indication of whether it is a JPEG file.  In UNIX, a file can have any name.  A JPEG file can be named picture or picture.txt or picture.gif for that matter.

The correct way to test for a file type is with a utility called... wait for it... drum roll... file.

Read 'man file'.

---

### Post by raleigh3 on 2020-08-07
I changed my post.

How can I test if .jpg file extension is supplied?

---

### Post by SeijiSensei on 2020-08-07
```

#!/bin/bash

if [ $(echo "$1" | grep \.jpg$) != "" ]
then
   # ends in .jpg
   do stuff
else
   # doesn't end in .jpg
   do other stuff
fi

```
The regular expression "\.jpg$" uses the $ character to denote the end of the string. The period is "escaped" with \ because it is to be taken literally. (Usually "." in a regex means any character.)

---

### Post by kneutron on 2020-08-07
--Don't forget to check CAPitalized extensions and jpeg/JPEG variants

---

### Post by raleigh3 on 2020-08-07
> **SeijiSensei said:**
> ```

#!/bin/bash

if [ $(echo "$1" | grep \.jpg$) != "" ]
then
   # ends in .jpg
   do stuff
else
   # doesn't end in .jpg
   do other stuff
fi

```
The regular expression "\.jpg$" uses the $ character to denote the end of the string. The period is "escaped" with \ because it is to be taken literally. (Usually "." in a regex means any character.)

I am getting this message.

```
/home/andy/bin/test.sh: line 3: [: !=: unary operator expected
continuing.

```

```
#!/bin/bash

if [ $(echo "$1" | grep \.jpg$) != "" ]
then
   # ends in .jpg
   echo "You included a file extension."
else
   # doesn't end in .jpg
   echo "continuing."
fi
```

---

### Post by raleigh3 on 2020-08-07
Thanks for your help.

It needed a double bracket conditional compound command [[ ... ]]

[https://stackoverflow.com/questions/13617843/unary-operator-expected-error-in-bash-if-condition](https://stackoverflow.com/questions/13617843/unary-operator-expected-error-in-bash-if-condition)

---

