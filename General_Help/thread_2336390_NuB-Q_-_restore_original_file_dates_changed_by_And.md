---
title: "NuB-Q - restore original file dates changed by Android"
date: 2016-09-07
forum: General Help
---

### Post by eric68 on 2016-09-07
I have tens of thoisands of files neatly sorted. Unfortunately, I sorted them on android, losing the original date stamps.

I still have a copy of all files with original date - unsorted.

So this is what i propose to do.

Find a file's duplicate from among original-date files.

Then somehow extract the date and assign it to the new file's attributes.

Or convert date to string and concatenate to end of file name.

This might be in a nested FOR loop
  FOR i = 1 .. EOF (correct order file)
    FOR i = 1 .. EOF (correct date file) DO
      Compare the files with DIFF
        Diff returns a run-time flag with a
          a null value if both files are same
  
I've seen tutorials for much of the foregoing. 

But I still dont know HowTo ..
  Access a file's created/modified date.
  Assign them to another file's dates.
  Use an exit code from DIFF command
    to CONDITIONALLY assign 
    1 file date to another

I am excited re learning linux command line. There's a sense of freedom, provided you have a good distro/pc combo. BTW, I'm using LUBUNTU 14.04.

This will be my first script ever, & I'm excited to get it up & running

Thanks all.

Eric

---

