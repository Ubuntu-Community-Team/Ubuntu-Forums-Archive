---
title: "BASH user input"
date: 2013-01-12
forum: General Help
---

### Post by SpeedoJoe on 2013-01-12
I'm currently experimenting with some BASH scripting and I have noticed a potential problem with a script that I am working on.

The first reference to the $fileext variable in the below line isn't purple like the second and third, probably due to the front slash. How do I go about separating that reference from the front slash but still have it remain in the code?

[IMG]http://i.imgur.com/MievU.png[/IMG]

---

### Post by steeldriver on 2013-01-12
The syntax highlighting is going to depend on what editor your using, I think - most likely the purple color is because the editor is recognizing everything between single quotes as a string literal  

What are you actually trying to do?

---

### Post by SpeedoJoe on 2013-01-12
Recursively copy hundreds of gigs of PhotoRec recovered files into directories respective to their filetypes.

```

#!/bin/bash
echo
echo "Enter a filename extension"
echo
read fileext
sudo mkdir $fileext
sudo find -name *.$fileext > $fileext.sh_temp1
sudo nl -s 'cp ' $fileext.sh_temp1 | cut -c7- > $fileext.sh_temp2
sudo awk '{ print $0 " $fileext/" }' < $fileext.sh_temp2 > $fileext.sh
chmod 777 $fileext.sh
sudo ./$fileext.sh

```

---

### Post by steeldriver on 2013-01-12
er... ok... I can't see how that's going to work, maybe I`m missing something

I don't have time to help right now but if you search for examples I'm pretty sure you will find a script that works for you - basically I'd recommend a loop of the form

```

while read -r -d $'\0' file
do 
[I]  something with "$file"
[/I]done < <(find . -type f -print0)

```where something is (1) extract the extension (you can use the bash ${file##*.} and ${file%.*} to get the basename and extension) (2) check the dir exists and if not create it (3) do the copy

Hope this helps

---

### Post by SpeedoJoe on 2013-01-12
Thanks for the advice.

It does actually work if I don't use a variable but I was getting annoyed at having to change the script each time I wanted to sort another filetype.

---

