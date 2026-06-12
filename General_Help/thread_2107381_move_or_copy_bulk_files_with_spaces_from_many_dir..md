---
title: "move or copy bulk files with spaces from many dir. to one dir."
date: 2013-01-21
forum: General Help
---

### Post by irv on 2013-01-21
OK, I have a directory with 439 directory and all have spaces in the names. Now I move all to a directory name temp in my home directory. All have  files with extensions  (epub, pdf, jpg, opf) Now all I want is the .epub files from all the directories and I want to move or copy them to a directory named temp2 in my home directory.
Now I wrote a small script file to do this, but I get errors that none of the directories or files can be found and that is because of the spaces in the names. Here is my script file. What do I need to change to make it work.
```
#!/bin/bash

main_search_dir="/home/irv/temp/";
save_dir="/home/irv/temp2/";
extention="epub";

cp `find $main_search_dir -name "*.$extention"` $save_dir
```

---

### Post by steeldriver on 2013-01-21
This is the way I've learned to do this kind of thing (from the wiser folks on here):

```
while read -r -d $'\0' file; do echo cp "$file" "$save_dir"; done < <(find "$main_search_dir" -name "*.$extention" -print0)
```Take out the 'echo' once you've checked it's doing the right thing

---

### Post by sisco311 on 2013-01-21
Please check out BashFAQ 020 (link in my signature).

I'd try something like:
```
find "$m_s_d" -name "*.$e" -exec cp -t "$s_d" {} +
```

---

### Post by irv on 2013-01-22
OK I am going to mark this solved. Here is what I did.
I created two directories, "temp" and "temp2". Then I created a script file cpepubfiles.sh and put it in /home/irv/temp/
```
#!/bin/bash

main_search_dir="/home/irv/temp/";
save_dir="/home/irv/temp2/";
extention="epub";

find "$main_search_dir" -name "*.$extention" -exec cp -t "$save_dir" {} +
```
Then I copied all the directories with the .epub files in them to the temp directory.
Then I open a terminal and changed to the temp directory and ran
```
. cpepubfiles.sh
```
It copied all the epub files from all the directories to /home/irv/temp2.
Worked great.
Thanks for all the help.

---

