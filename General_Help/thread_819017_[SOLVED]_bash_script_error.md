---
title: "[SOLVED] bash script error"
date: 2008-06-05
forum: General Help
---

### Post by uncannybuzzard on 2008-06-05
hey, i'm just writing a simple script to join multi-part avi files so i don't have to look up the mencoder arguments each time i have to do it and just as an exercise in learning bash script. this keeps giving me a syntax error at line 28 ( the first "fi"). nothing pops out at me. can anyone see something i dont?

```
#!/bin/bash

echo "Joining the files. This may take awhile. . ."
cat $1 $2 >> temp.avi

if [ -e ./output.avi ]

	read -p "This script outputs the final file as output.avi but it appears as though this file already exists. Do you wish to overwrite it? y/n" overwrite

		case "$overwrite" in

			"Y" | "y")
			rm -rf output.avi
			;;

			"N" | "n")
			echo "Please choose a final name for your file:"
			read new_final
			;;

			* )
			echo "Invalid response. Exiting."
			exit 0
			;;

		esac

fi

echo "Starting mencoder to rebuild the index."

if [ -e $new_final ]

	mencoder -forceidx -oac copy -ovc copy temp.avi -o $new_final

else

	mencoder -forceidx -oac copy -ovc copy temp.avi -o output.avi

fi

echo "Removing the temporary and base files."
rm -rf temp.avi $1 $2

echo "Done."
exit 0
```

---

### Post by dagnabit dang doohickey on 2008-06-05
The **if** construct is missing **then**.
```
if [ *something* ] **; then**
    *something_else*
fi
```

It can also be written as:
```
if [ *something* ]
  **then**
    *something_else*
fi
```

---

### Post by uncannybuzzard on 2008-06-05
yeah. i totally knew that too. one of those blonde moments. :|
thanks.

---

