---
title: "batch file transfer from multiple subfolders"
date: 2007-07-01
forum: General Help
---

### Post by chinaski on 2007-07-01
I have a .doc main folder which contains many subfolders

I need to move all .doc files from all subfolders contained in the main folder to a single folder, I thought the terminal it's fine for this kind of task but I do not know which commands and syntax I should use

example:

[command_to_move] [recursive] *.doc /main_folder /new_folder

is that possible?

and if it is, please how?

---

### Post by McNils on 2007-07-01
The find command can be used. 

find /main_folder -name \*doc -exec mv '{}' /new_folder \;

NB. You can overwrite files with this command if they have the same name in different folders.

---

### Post by chinaski on 2007-07-01
thanks a lot McNils ;)

---

