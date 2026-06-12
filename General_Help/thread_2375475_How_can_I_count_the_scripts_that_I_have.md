---
title: "How can I count the scripts that I have?"
date: 2017-10-24
forum: General Help
---

### Post by baxter-abe on 2017-10-24
[COLOR=#2D3B45][FONT=LatoWeb]This is my script for an online class I'm taking. I'm wanting to count which files are scripts but am stuck. [/FONT][/COLOR]
#!/bin/bash
echo $PATH  | tr : '\n' | 
while read e; do 
    for i in $e/*; do
        if [[ -x "$i" && -f "$i" ]]; then     
            echo $i
        fi
    done
done

[COLOR=#2D3B45][FONT=LatoWeb]I just get a massive out put of files. I've tried piping through grep and wc but still get a count of 0. I'm looking for a count of scripts. How can I count my scripts and have an output to read? I'm still learning Linux but loving it![/FONT][/COLOR]

---

### Post by TheFu on 2017-10-25
Please use code tags when posting code or shell output.  Adv Reply (#).

To count scripts/files in a directory, I use **wc -l** - as in ```
ls -1 |wc -l
```

If I need to exclude files - like data stuff, then  ```
ls -1 |egrep -v .dat |wc -l
```

And don't forget to add any .dot files and/or remove the current and parent directories.

If you want to find all the scripts in the PATH, I don't think your method will work.  Probably need to use **head** on every file to figure out if the files begin with #! or not. Being executable doesn't matter at all.  I would create a list of files and store those into a TMP location/file, then work my way through each file in that list.  **fgrep** and/or **find** would be handy, I bet.

---

