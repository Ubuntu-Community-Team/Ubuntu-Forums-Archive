---
title: "Bash script and mkdir create sub folders with spaces"
date: 2017-02-28
forum: General Help
---

### Post by vnavna on 2017-02-28
I am able to run the following command through a terminal:
mkdir -p Documents/{Pictures,Music,Notes,Projects,Spreadsheets,"Downloaded files","Personal Files"} | chmod -R 700 Documents/ | touch Documents/{Test1,"test 2.txt"}
as soon as I put this into a script the results are not the same. I know that the quotes are causing the issue but I am at a loss on what I need to do to fix this. I have tried multiple time to add double quotes and single quotes but the results come back the same.
Results of the script:
ls Documents/
Pictures,Music,Notes,Projects,Spreadsheets,Downloaded                One folder

ls ~
files Files} {Test1, test 2.txt}

---

### Post by steeldriver on 2017-02-28
Hello and welcome to the forums

How do you know that the quotes are the issue?

How exactly are you running the script? A common issue for people not familiar with Ubuntu is using `sh` rather than `bash` - `sh` on Ubuntu systems is the dash shell (which doesn't support brace expansions)

---

### Post by vnavna on 2017-02-28
You are correct I was using the following #! /bin/sh
So if i were to run the following #! /bin/bash it may work correctly?

#! /bin/bash

mkdir -p Documents/{Pictures,Music,Notes,Projects,Spreadsheets,""Downloaded\ files"",""Personal\ Files""} | chmod -R 700 Documents/ | touch Documents/{Test1,""test\ 2.txt""}

---

### Post by vnavna on 2017-02-28
OMG, that was it. The problem that I have is that I asked my instructor and he just told me to do the following "Lookup escape characters for special chars." I have been wrestling with this for three days.
Thank you so much

---

### Post by steeldriver on 2017-02-28
Glad to help - I hope it gets less frustrating from here on in ;)

---

### Post by sisco311 on 2017-02-28
> **vnavna said:**
> OMG, that was it. The problem that I have is that I asked my instructor and he just told me to do the following "Lookup escape characters for special chars." I have been wrestling with this for three days.
Thank you so much

A wrong quote or couch can ruin your week. :evil:



A bit off topic...

Brace expansions are very useful in an interactive (bash) shell, but when you write a shell script you have to focus on other things, like readability, scalability and POSIX compliance. ;)

---

