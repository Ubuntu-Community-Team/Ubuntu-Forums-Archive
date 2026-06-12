---
title: "Quickly individually zipping files"
date: 2008-03-10
forum: General Help
---

### Post by Muzer on 2008-03-10
Is there a program/shell script/whatever I can download/make/copy + paste to quickly indivdually zip loads of files (there are directories, so it'd have to go into a directory, individually zip all of the files, go out of it, go into the next one, individually zip the files in there and so on).

Remember I want them individually zipped ie each file in a zip of its own

And it has to be zips, not RARs, 7Zs, GZs, BZs, whatever.

---

### Post by Kerry_W on 2008-03-10
winrar will do what you need.  just install under wine.

start winrar and browse to the appropriate folder, select the files you want to zip, right click and "Add files to archive".
choose the zip format and your compression level then choose the "Files" tab and check off "Put each file to separate archive" then click "Ok"

you'll get a seperate zip file for each file you selected.

Kerry

---

### Post by Muzer on 2008-03-10
Thanks, I already have WinRAR on my Windows boot, I'll try just directly launching it in Wine.

---

### Post by Muzer on 2008-03-10
Doesn't work, it just puts the folders into indivual zips, not the files. As I said, they are all in folders (named #0,A-Z), and I want to maintain the folders but only put the files into their own zips, not the folders. Doing your method just makes #0.ZIP, A.ZIP, B.ZIP etc.

---

### Post by Muzer on 2008-03-10
Sorry for the triple post guys, it's just so it bumps. I think what I'll do is to zip it without folder heirachy using the WinRAR method, then use another program to sort it into folders again (as I said, it's only alphabetically sorted). However, my drive has **** all space left on it, and my Windows is hibernated so I can't put it onto there, and I can't seem to get network locations working in Wine, so it'll have to wait.

---

### Post by lloyd_b on 2008-03-10
> **Muzer said:**
> Is there a program/shell script/whatever I can download/make/copy + paste to quickly indivdually zip loads of files (there are directories, so it'd have to go into a directory, individually zip all of the files, go out of it, go into the next one, individually zip the files in there and so on).

Remember I want them individually zipped ie each file in a zip of its own

And it has to be zips, not RARs, 7Zs, GZs, BZs, whatever.

Here's a short shell script to do what I think you want:
```
#!/bin/bash
#
# Recursively zip all files under the specified directory
#
# If no directory specified, start in the current directory...

# Setting IFS to handle files/directories with spaces in the names
IFS="|"

# Check if we got a command line argument
if [ -n "$1" ]; then
   STARTDIR="$1"
else
   STARTDIR="."
fi

# Get a list of files to process
FILES=`find "$STARTDIR" -type f -printf "%p|"`

# Loop through them
for CURFILE in $FILES; do

   # Zip file name = "filename.zip"
   ZIPFILE="$CURFILE.zip"

   # Zip the file
   zip "$ZIPFILE" "$CURFILE"

   # Uncomment the following line to remove to delete the original file
   # once the zip file has been created
   # rm "$CURFILE"
done
```

Save it to "masszip", then in a terminal "chmod 700 masszip", and then in the terminal "./masszip {directory}", where {directory} is the top directory for the zipping.

Note: I have *not* heavily tested this script, so use at your own risk.  I'd leave that line for deleting the original file alone until you're sure the script is working...

Lloyd B.

---

