---
title: "Automatic unzip and copy using shell script"
date: 2007-04-15
forum: General Help
---

### Post by dbrmik on 2007-04-15
Hi

I am a Linux novice, just moved over from windows. I must say that I dont regret it.

I was wondering if it was possible to monitor the contents of a directory for zip files, if any are found then unzip and copy the unzipped archive to another directory, then delete the original zip file. The script would then wait indefinitely for another zip file to process.

Is this possible with a script?

Anyone have any ideas on how I would go about this? 

Thank You

---

### Post by =0verlord= on 2007-04-15
Yeah, a simple bash script should be able to handle this if you don't need it to unzip as soon as the file appears.  Additionally there is the more advanced [http://www-128.ibm.com/developerworks/linux/library/l-inotify.html](http://www-128.ibm.com/developerworks/linux/library/l-inotify.html) that I found and it looks interesting.  I would get you started but I am really rusty on bash scripting.  Basically your program would look kinda like this (hopefully I haven't made it too hard to understand):

```
cd /your/directory

while (1) {
    for (files in directory) {
        if (filename ends in .zip) {
            unzip file
            rm file
        }
    }

    wait (5000)
}
```

---

### Post by dbrmik on 2007-04-15
Thanks Overlord

Yes I understand your pseudo code but I have no experience of scripting.

Any idea on how I would determine if there are any files in the directory with a files extension of zip,  then pass this info to unzip/gzip


Thanks

---

### Post by =0verlord= on 2007-04-15
Sigh - I've been meaning to get up to speed, so give me a while and I'll see what I can do.  No promises, but I will try to get it out in less than an hour.  You're lucky I'm incredibly bored and restless right now ;)

---

### Post by =0verlord= on 2007-04-15
HA! 50min, not too bad.  Here ya go, and adjust to suit yourself - it currently overwrites existing files (the -o) and has no output (the -qq).  You can remove those and change the sleep time as necessary.  You may also need to run dos2unix on it prior to running (and make sure to set executable flags with chmod +x script.sh) to get the newlines good to go.

I suggest putting it into the directory with the zips so you don't lose it, but you can run it from anywhere once you replace the DIR variable (background with "./script &" if you want).
Hope it works for you!  And PLEASE test it on a throwaway first!  If you need a better explanation please ask, I can make a step by step.

```
#!/bin/bash

shopt -s nullglob  #prevent lameness from glob matching

DIR="/t/testing123"  #directory for operation, NO TRAILING SLASH

while [ 1 -le 2 ]
do
	for file in ${DIR}/*\.zip
	do
		unzip -oqq $file
		rm -f $file
	done
	
	sleep 30
done
```

---

### Post by dbrmik on 2007-04-15
Thanks Overlord

I need help to underrstand this line

   for file in ${DIR}/*\.zip

Could you please explain how this bit ${DIR}/*\.zip generates a filename

Once again, thanks for youre time

Best Regards

---

### Post by =0verlord= on 2007-04-15
Sure, it breaks down into 5 parts:

${DIR} - fills in the contents of the DIR variable
/ - adds a foreslash to finish the directory name
* - matches anything, in this case for grabbing the non-extension part of the filename
\. - this is a way to match an actual period (backslashes are escape characters), not the way regular expressions normally work in which a period matches any character
zip - matches the last part of the filename

Put those all together, and you have a REGEX that grabs only the files we want :)

---

### Post by dbrmik on 2007-04-20
Overlord

I have only just had a chance to test this, it works just how I wanted it to.

Thanks once again for your help

---

