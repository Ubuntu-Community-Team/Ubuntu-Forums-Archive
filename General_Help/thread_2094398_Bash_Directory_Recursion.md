---
title: "Bash Directory Recursion"
date: 2012-12-13
forum: General Help
---

### Post by PinkFloyd102489 on 2012-12-13
Background: I work as a photographer for a car dealership that has photos of every single vehicle on the lot on their website. For new cars, I'm allowed to keep a library, so that when a vehicle with similar specs come in, I can upload those pictures without having to photograph again. I have them sorted out into a hierarchy directory like model, exterior color, interior color, transmission, package, etc. Ex: ~/2013/MODEL/Red/Black/Auto/Convenience/*.jpg

Goal: Recurse into directories, check whether jpg files exist in it, and append pwd to a file. Basically, I want a listing of the directories in a nice, compact, readable format. This will allow me to see if I have pictures of that particular vehicle.

Potential problem: In some of the directories, there are two or more under it, especially with the exterior color directories.

---

### Post by Vaphell on 2012-12-13
```
#!/bin/bash

shopt -s nullglob
while IFS= read -rd $'\0' d
do
  jpgs=( "$d"/*.jpg )
  (( ${#jpgs[@]} )) && echo "$d (${#jpgs[@]})"
done < <( find "$PWD" -type d -print0 ) > out.txt
```

i used find with $PWD to make sure full paths are printed.
find prefixes results with the root path you provide, eg
*find ~/2013* or *find /home/you/2013* => /home/you/2013/a/b/c/result
*cd 2013; find .* => ./a/b/c/result

---

### Post by PinkFloyd102489 on 2012-12-13
> **Vaphell said:**
> ```
#!/bin/bash

shopt -s nullglob
while IFS= read -rd $'\0' d
do
  jpgs=( "$d"/*.jpg )
  (( ${#jpgs[@]} )) && echo "$d (${#jpgs[@]})"
done < <( find "$PWD" -type d -print0 ) > out.txt
```

i used find with $PWD to make sure full paths are printed.
find prefixes results with the root path you provide, eg
*find ~/2013* or *find /home/you/2013* => /home/you/2013/a/b/c/result
*cd 2013; find .* => ./a/b/c/result


```
brandon@brandon-mint ~/work/New/2013 $ sh recur ~/work/New/2013/
recur: 3: recur: shopt: not found
recur: 6: recur: Syntax error: "(" unexpected (expecting "done")
```

Running without an argument yields the same error.

---

### Post by steeldriver on 2012-12-13
I should probably leave this for Vaphell to answer, but I believe that since it's a **bash** script you shouldn't be trying to run it via **sh** (which will probably invoke a **dash** shell)

Just make it executable

```
chmod +x recur
```then run it directly as

```
./recur */path/to/dir*
```

---

### Post by PinkFloyd102489 on 2012-12-13
> **steeldriver said:**
> I should probably leave this for Vaphell to answer, but I believe that since it's a **bash** script you shouldn't be trying to run it via **sh** (which will probably invoke a **dash** shell)

Just make it executable

```
chmod +x recur
```then run it directly as

```
./recur */path/to/dir*
```

Thanks, got it to run.

However, it only chose the first directory and didn't recurse into every single one like I need. Ex: Only went into the TRIM1 dir when TRIM2 exists also.

---

### Post by JKyleOKC on 2012-12-13
Since the "find" command is starting from $PWD, and the script never references any command-line argument, the suggested command to launch the script won't work. 

If you want to pass the directory in as an argument, replace "$PWD" in the script with "$1" but you could also save the script itself in ~/bin (creating the directory if it does not exist), then doing a "cd" to the directory you want to look through and just using the bare command "recur" since the ~/bin directory gets added to your path automatically making the script runnable from anywhere...

---

### Post by steeldriver on 2012-12-13
> **JKyleOKC said:**
> the script never references any command-line argument

oops... didn't notice <hangs head in shame>

---

