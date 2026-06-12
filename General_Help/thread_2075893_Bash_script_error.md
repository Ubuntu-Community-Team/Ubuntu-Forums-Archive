---
title: "Bash script error"
date: 2012-10-24
forum: General Help
---

### Post by rmockler on 2012-10-24
I'm posting this in hopes that someone can help me solve my dilemma. I have created a script which I found in the following link: [http://www.labnol.org/software/print-files-on-linux/17841/](http://www.labnol.org/software/print-files-on-linux/17841/)
This is supposed to enable moving a file to a Dropbox folder named PrintQueue and then have it sent to a remote printer when the script runs.  The script is giving me problems. I have attached the script and also a screen print of the error message that I receive whenever I attempt to run the script.  If anyone can see what is wrong with this script, I would greatly appreciate any assistance in resolving the problem.
Thanks,
Richard Mockler

---

### Post by Vaphell on 2012-10-24
missing ; before **do**

frankly that script is full of fail, it has at least 3 things seriously wrong in 6 lines of code total
- using ls: ls is for human eyes not for scripts
- ls-ing the dir only to merge it with the filename later
- redefining IFS to avoid problems with spaces

all of these are non-issue if one uses builtin globs
```
#!/bin/bash

PrintQueue="/root/Dropbox/PrintQueue";

for PrintFile in "$PrintQueue"/*
do
  lpr -r "$PrintFile"
done
```

---

### Post by rmockler on 2012-10-25
Vaphell, my sincere gratitude for your help.  Your suggestion and your attached script worked perfectly for me.  I simply did a copy, paste of your script, set the proper path of my Dropbox/PrintQueue folder, set up a cron job to run the script every minute, and now remote printing works exactly the way I want.  
Thanks again,
Richrd Mockler

---

