---
title: "Unoconv - cron watch for new/updated files in folder"
date: 2015-06-04
forum: General Help
---

### Post by greavette on 2015-06-04
Hello,

I've recently discovered Unoconv to convert libreoffice files.  I'm hoping to use this to convert .docx and .xlsx files to PDF.  

I'm looking for tips on how I can use a cron job to watch a folder for new or updated document files so they can be converted to PDF.

Anyone done this before?

Thank you.

---

### Post by SeijiSensei on 2015-06-04
Sure.  Will the folder be emptied after any documents are processed?  That makes life much easier.

I have a script running at a client's site that runs from cron every two minutes to see if there are files it needs to process.  In root's crontab (/var/spool/cron/root) I have:
```
*/2 * * * * /path/to/the/script
```

Here's an excerpt of the relevant section:
```

#!/bin/bash

CHECK_DIR=/path/to/some/directory
LOG=/var/log/mylog

cd $CHECK_DIR

# count the number of files to be processed
NFILES=$(ls -1 | wc -l)

if [ "$NFILES" = "0" ]
then
     echo "$(date +%c) - No files found" >> $LOG
     exit 0
fi

echo "$(date +%c) - Processing $NFILES files" >> $LOG

# process the files
for f in *
do
     # commands to process files go here
     # $f = file name
done

echo "$(date +%c) - Processing finished" >> $LOG

exit 0

```

---

### Post by matt_symes on 2015-06-04
Hi

You can also use inotifywait from the package inotify-tools to perform the conversion after the file has been uploaded.

I use this technique to automatically re-source all the zsh shell instances i have open (in screen sessions and such like) on this laptop after i make a change to ~/.zshrc or my aliases and functions files that are sourced from ~/.zshrc.

Kind regards

---

### Post by greavette on 2015-06-08
Thanks to you both for your replies.  I did some more research and had testing using Unoconv for this conversion but I could not get it to work in a .sh (bash) script.  It worked perfectly from the terminal but using the same instruction in my shell didn't work.  I had also looked at using inotify to watch the folder.  Is inotifywait the same thing?  I thought inotifywait would only let me know when the files were uploaded but didn't give me the ability to do anything else except let me know?

SeijiSensei - the folder I'm watching for new files will be empty until the new files arrive.  My plan is to convert the files that get dropped into that folder and once converted rsync (with remove source files option) the files to a completed folder.  With the trouble I was having with unoconv I thought I might use soffice (headless libreoffice) to convert the documents to pdf in a cron job (running every two minutes).  I will review your script and probably use it for my processing as I see it's formulated very well with good checking.

If anyone has experience with using Unoconv and can get it to work with inotify (or inotifywait) I'd be happy to give these another shot for my solution.

Thanks.

---

