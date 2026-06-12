---
title: "recursive rename of many files in many directories?"
date: 2024-05-31
forum: General Help
---

### Post by pnuke on 2024-05-31
Hi, 

Im looking for a way to rename tens of thousands of files in hundreds of subdirectories. The majority of the renaming shall be "JPG" to "jpg" for example or similar. 

I was researching the net for a few days already but every single time the solution works only for one directory (using a for loop). Is there really no neat solution that works recursively?

---

### Post by currentshaft on 2024-05-31
There's plenty of solutions, perhaps you could share ones you'd tried and what failed, or just try something like this (obviously, at your own risk):

find /path/to/parent/directory -type f -iname "*.JPG" -execdir rename 's/\.JPG$/\.jpg/' {} \;

---

### Post by Rubi1200 on 2024-06-01
Not sure if you are in a position to do this, but I would urge caution and perhaps test in a VM first.

If that is not an option, then add echo before rename in the code above. That will perform a dry run in the terminal so you can check if the desired results come out right.

But then again if we are talking about tens of thousands of files...

Perhaps test first on just **one **directory or sub-directory to make sure it works.

---

### Post by pnuke on 2024-06-01
> **currentshaft said:**
> There's plenty of solutions, perhaps you could share ones you'd tried and what failed, or just try something like this (obviously, at your own risk):

find /path/to/parent/directory -type f -iname "*.JPG" -execdir rename 's/\.JPG$/\.jpg/' {} \;

Hi, 

this was actually the one Ive tried but Ive messed up the installation of rename and thought its not a standard package of Ubuntu and therefore skipped it. Tried it again now and it works like a charm.

Just one remark:
the option must be "-name" and not "-iname" as I only want to rename the ones with uppercase and not all files. iname is case-insensitive and also returns *.jpg. Luckily there is no mixed case.

Thank you, especially for the sed syntax, this was also the next hassle for me, as Ive struggle every single time to create a working sed replacement.

---

### Post by dragonfly41 on 2024-06-01
Late idea since you have found a script.

Now I am sure you can find a compressed regexp script to do the job. But with tens of thousands of jobs you must ensure you have backups and a testbed for your renaming scripts.
I am engaged in a similar exercise of getting some order out of chaos. I do not understand why you need to change extension JPG into jpg. That is just cosmetics.
> The majority of the renaming shall be "JPG" to "jpg" for example or similar.
I don't think that renaming each file offers much help. Who can remember tens of thousands of file names? Instead you might develop an AI front end to view the features of each jpg to look for image patterns.
My approach is to use Recoll (GUI) to index every file on my desktop.  It might take a few hours for initial scan. But thereafter &#8220;update index&#8221; daily.
Now I can visualise hundreds of files.
In your case run the query &#8220;ext:jpg&#8221;.
Optionally a UI automation script can be run to walk through every (filtered and short listed) file (in GUI) and use  right click to access file ... Copy File Path.

Note that you can shorten the Recoll indexing time by pointing to specific directories and excluding directories. And another similar tool is SearchMonkey.

[Postscript] Looking at my own GUI (query ext:jpg) I see 24,000 jpg images. All in one view which can be sorted, filtered, searched by keywords ... etc.  No need to re-name.  But certainly possible if you prefer some invented file naming plan. Like passwords they are forgotten. Better to ask using natural language. For this you might use Albert as front end which brings up a prompt field to apply to Recoll. i.e. a toolchain. Or Actiona might be easier. Experiment.

---

