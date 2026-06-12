---
title: "gedit external tool"
date: 2018-08-23
forum: General Help
---

### Post by plasmagr-78 on 2018-08-23
I have setup a script in gedit external tool given below. The tool executed for example on a "test.c" file does not respect the "py" matching and executes python compile command anyway. 
Kindly guide me on this matter.
```
#!/bin/sh
file=${GEDIT_CURRENT_DOCUMENT_NAME%}
ext=${file##*.}
if [ "$ext"=="py" ]; then
python  $file
else
printf "A C file"
fi
```

---

### Post by steeldriver on 2018-08-23
Hello and welcome to the forums

The issue is with your test bracket I think. The POSIX form is

```

if [ "$ext" = "py" ]; then

```

Note in particular the whitespace around the operator - otherwise you are testing the single (string) argument "$ext"=="py" (which will always be true)

You could also consider using a case:

```

case $ext in
  py) python  "$file"
  ;;
  *) printf "A C file\n"
  ;;
esac

```

---

