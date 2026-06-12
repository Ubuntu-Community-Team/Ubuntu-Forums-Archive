---
title: "script to convert archive files"
date: 2007-08-10
forum: General Help
---

### Post by firehammer on 2007-08-10
I'm looking for help creating a script to convert several directories full of comic book archive  
files that are in the .cbr (rar) format to the .cbz (zip) format.  The files may have spaces in them which I would also like to convert to underscores.

I know that the general structure of the script would look something like this: 
[LIST=1]
[*]get directory to start in
[*]loop through directories looking for *.cbr files
[*]rename to *.rar (replace spaces here?)
[*]either
      [LIST]
      [*] unrar the archive and zip
      [*] convert the rar to zip
      [/LIST]
[*]rename to *.cbz
[/LIST]

but I'm not sure how to get started.

---

### Post by bodhi.zazen on 2007-08-10
use rename :

rename " " _ *\ *

that will rename the spaces to _ ... 

you may need to run that command a few times to get 'em all

same for .cbr

rename .cbr .rar *.cbr

or do you need to extract (unzip) and re-package (rar) ?

You know with linux you do not *need* to rename ?

---

### Post by lloyd_b on 2007-08-10
> **firehammer said:**
> I'm looking for help creating a script to convert several directories full of comic book archive  
files that are in the .cbr (rar) format to the .cbz (zip) format.  The files may have spaces in them which I would also like to convert to underscores.

I know that the general structure of the script would look something like this: 
[LIST=1]
[*]get directory to start in
[*]loop through directories looking for *.cbr files
[*]rename to *.rar (replace spaces here?)
[*]either
      [LIST]
      [*] unrar the archive and zip
      [*] convert the rar to zip
      [/LIST]
[*]rename to *.cbz
[/LIST]

but I'm not sure how to get started.

1. Useful command: "find":
find /home/whatever *.cbr
will search "/home/whatever" (recursively scanning subdirectories) and producing a list of all ".cbr" files.

2. I don't think the file needs to be named ".rar" for unrar to work properly (but I'm not an expert on ".rar" files, so I could be wrong.

3.  Once you have a list, you'll need to unpack them in a working directory somewhere (AFAIK, there's no direct way to convert from .rar to .zip).

One problem you'll probably encounter is that the looping mechanisms in a shell script tend to break if there are spaces in a file name.  But there's a trick using a special shell variable called "IFS" that can handle this.

Here's a "rough draft" of your script (name it "cbr2cbz"):
```
#!/bin/bash

# Set the "field separator" to something other than spaces/newlines" so that spaces
# in the file names don't mess things up.  I'm using the pipe symbol ("|") as it is very 
# unlikely to appear in a file name.
IFS="|"

# The script should be invoked as "cbr2cbz {directory}", where "{directory}" is the 
# top-level directory to be searched.  Just to be paranoid, if no directory is specified,
# then default to the current working directory (".").  Let's put the name of the
# directory into a shell variable called WORKDIR.  
# Note: "$1" = "The first command line argument"
if test -z $1; then
     WORKDIR="."
else
     WORKDIR="$1"
fi
echo "Working from directory $WORKDIR"

# Now, execute a loop, based on a "find" command in the specified directory.  The 
# "-printf "$p|" will cause the file names to be separated by the pipe symbol, rather than
# the default newline.  Note the backtics ("`") (the key above the tab key on US
# keyboards).
for CBRFILE in `find $WORKDIR -name *.cbr -printf "%p|"`; do
     # Now for the actual work.  First, extract the base file name (without the extension)
     # using the "basename" command.  Warning: more backtics.
     BASENAME=`basename $CBRFILE ".cbr"`

     # And the directory path for that file, so we know where to put the finished ".cbz"
     # file.  You could potentially hard code this to a single directory - your choice...
     # backtics again...
     DIRNAME=`dirname $CBRFILE`

     # For the new file name, let's convert any spaces to underscores.  We'll do this with
     # a "sed" (stream editor) command.  Backtics again.
     NEWBASEFILE=`echo "$BASENAME" | sed "s/ /_/g"`

     # Now, build the "new" file name,
     NEWNAME="$NEWBASEFILE.cbz"

     # We need a guaranteed empty directory to work in, so I'm creating a temp
     # directory under the current working directory.  It will be deleted when we're
     # done with it:
     mkdir cbr2cbztemp
     cd cbr2cbztemp

     # Now that the preliminaries are done, we start doing some work.
     # We need to copy the ".cbr" into the current "temp" directory for 
     # unpacking/repacking.
     cp "$CBRFILE" .

     # rename the file to a ".rar" file.  I don't think this is necessary, but it shouldn't
     # cause any problems...
     mv "$BASENAME.cbr" "$BASENAME.rar"

     # Unpack the rar file
     unrar e "$BASENAME.rar"

     # Delete the .rar file
     rm "$BASENAME.rar"

     # Create the ".cbz" file
     zip "$NEWNAME" *

     # And move it to the directory where we found the original ".cbr" file
     cp "$NEWNAME" "$DIRNAME"

     # Finally, "cd" back to the original working directory, and delete the temp directory
     # created earlier. 
     cd ..
     rm -r cbr2cbztemp

     # At this point, you could potentially 'rm "$CBRFILE"' to delete the original, but
     # I'd suggest not doing so until you're certain you've got a good ".cbz" file...

done
```

Warning: I have *not* actually tested this script.  Your mileage may vary.  Not responsible to accidents.  But this should give you an excellent starting point that you can customize to your needs...

Lloyd B.

---

### Post by firehammer on 2007-08-11
@lloyd_b

Perfect!  The script worked flawlessly, I did test it as-is and with the {rename cbr->rar} lines commented out, the results are the same so I left it commented out.

Thanks for your time, I appreciate it!

---

