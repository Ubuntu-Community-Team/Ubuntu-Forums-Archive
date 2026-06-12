---
title: "Nautilus script, jpegtran rotate help"
date: 2007-04-16
forum: General Help
---

### Post by Subban on 2007-04-16
```
#!/bin/sh
for arg 
do
 filetype=`file -i "$arg"`
if [ -n "`echo $filetype | grep -i 'jpeg' `" ]; then
 jpegtran -rotate 90 "$arg" > temp.jpg;
 mv temp.jpg "$arg"
else
 convert -rotate 90 "$arg" "$arg"
fi
done
```

This doesn't seem to work any longer (original thread from 2005), if the convert -rotate line is commented out no action is taken on jpeg files. Convert isn't lossless on jpg hence the preference.

It doesn't seem to match on jpeg is all I can say, would someone be able to help and correct the problem please

---

### Post by Brucevdk on 2007-04-16
Looks like jpegtran is successfully called in my case. Note that if you comment out the "convert -rotate 90 "$arg" "$arg"" line a syntax error will be thrown since each block requires at least one statement.  I couldn't tell from your post, but does the script actually result in anything for you?

 Could you bring up the terminal and execute the following command: 
```
file <image filename>
``` 

Where <image filename> is the filename of the image you want to convert.

What's the output? Does it mention JPEG?

If you want to see what happens when the script executes (e.g. any errors) call it directly instead of using Nautilus, inside a terminal use:

```
~/.gnome2/nautilus-scripts/<script filename> <image filename>
```

Here's a commented version of the script in question, I hope it helps you to understand what exactly is going on.

[PHP]
#!/bin/sh

# nautilus passes every file selected as an argument to this script, what happens
# here is that it loops through each of the arguments (filenames).
for arg; do
	# uses the file command to determine the type of file (uses the "magic numbers")
	# and stores it in a variable called filetype
	filetype=`file -i "$arg"` 

	# -n tests to see if the argument is non empty, if it doesn't match jpeg
	# the echo would return nothing (i.e. it would be empty and so the condition
	# would fail).
	if [ -n "`echo $filetype | grep -i 'jpeg'`" ]; then
		# so if the filetype matches jpeg it'll use jpegtran to rotate it
		jpegtran -rotate 90 "$arg" > temp.jpg;
		mv temp.jpg "$arg"
	else
		# if it can't determine if the file is a jpeg it uses convert from
		# imagemagick to manipulate it, which is a bit strange because it might
		# aswell be a text file (ASCII text).
		convert -rotate 90 "$arg" "$arg"
	fi
done
[/PHP]

---

### Post by Subban on 2007-04-16
Thank you for your reply, with a couple more hours fighting with it and your tips it is now all working fine. I hdan't realised that commenting out 

```
convert -rotate 90 "$arg" "$arg"
```
would make the script error, silly of me I guess,.Then changes I made to the script to correct things clearly made no difference due to the script having that fatal error stopping it running at all. Running it from Nautilus I never saw what had happened :S

In future I will be checking from a terminal, I learned a valuable lesson here at least ;)

---

