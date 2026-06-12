---
title: "How to rename Multiple files at once ?"
date: 2017-05-03
forum: General Help
---

### Post by rob141 on 2017-05-03
Hello everyone, i would like to know if it is possible to rename 500 files at once ? All file have a different name and i want/need to keep it this way but the problem is that they have a number from - 0001 to - 0500 in front of them and i would like to loose those numbers.

So basically for example, how do i rename 0001 - whatever.something until 0500 - filename.something  TO   whatever.something until filename.something

Thank you very much in advance

---

### Post by LastDino on 2017-05-03
Well, simple tutorial is here

[http://www.tecmint.com/rename-multiple-files-in-linux/](http://www.tecmint.com/rename-multiple-files-in-linux/)

Never tried to rename that many files though. But it should work

---

### Post by sisco311 on 2017-05-03
If you prefer a GUI tool you can try: gprename, pyrenamer, krename or thunar (file manager).


In the CLI you can use the above mentioned perl based rename command:
```
rename **--dry-run** 's/^[0-9]{4} - //' *
```

With the --dry-run option the command will only print the name of each file that would be renamed.

---

### Post by rob141 on 2017-05-03
> **LastDino said:**
> Well, simple tutorial is here

[http://www.tecmint.com/rename-multiple-files-in-linux/](http://www.tecmint.com/rename-multiple-files-in-linux/)

Never tried to rename that many files though. But it should work


Thank you very much but this tutorial seem to be only changing the extensions!!  I do not want to change the extension and/or the file name, i only wish to remove every number from 0001 to 0500 in front of the files.

---

### Post by rob141 on 2017-05-03
> **sisco311 said:**
> If you prefer a GUI tool you can try: gprename, pyrenamer, krename or thunar (file manager).


In the CLI you can use the above mentioned perl based rename command:
```
rename **--dry-run** 's/^[0-9]{4} - //' *
```

With the --dry-run option the command will only print the name of each file that would be renamed.


Thank you so much, i will try gprename later this evening ( at work right now loll )  and will let you know if it work or can do what i want.    ;)

---

### Post by rob141 on 2017-05-03
Ok, after all gprename could not do what i wanted but it did work with the default file manager. loll silly me i had not even tried that before. sorry, my bad !!!

Thank you all for your help in any case ;)

---

