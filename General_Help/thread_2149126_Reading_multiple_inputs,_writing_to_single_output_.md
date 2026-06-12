---
title: "Reading multiple inputs, writing to single output file"
date: 2013-05-27
forum: General Help
---

### Post by Chris Papamitrou on 2013-05-27
Hello,

I have numerous files with the following format "Ni.wire.ten.10500.xyz" where the only thing changing in the filename is the numerical value 10500.  Lets say i have 100 of these types of files, or however many, and want to write a loop in fortran to open them starting with Ni.wire.ten.10500.xyz and enging with Ni.wire.ten.15500.xyz.  the files are identical in filename except the number starts on 10500 and each subsequent file is 500 more than the previous, for example lets say i have 5 files they would be callled

Ni.wire.ten.10500.xyz
Ni.wire.ten.11000.xyz
Ni.wire.ten.11500.xyz
Ni.wire.ten.12000.xyz
Ni.wire.ten.12500.xyz

i need to write a do loop (or a for loop) in either fortran (or bash) that will open each file, in sequence, starting with the 10500 and read its contents then write it to some other file and then do the same for the 11000 file, 11500 file, ...etc 

any thoughts or clarifications needed please feel free

---

### Post by HiImTye on 2013-05-27
```
mkdir out; cat * > out/out.txt
```

edit: if you only want to do specific files, you could do
```
mkdir out; cat Ni.wire.ten.{10500,11000,11500}.xyz > out/out.txt
```

[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by mikeym on 2013-05-27
A for loop in Bash would look something like:

```

# make sure not to break up filenames with spaces
IFS="
"
# you can easily test and modify the "ls" command to select the files you want
for file in $(ls *.xyz); do
  echo "Adding: $file"
  # append $file to out.txt
  cat "$file" >> out.txt
done

```

---

