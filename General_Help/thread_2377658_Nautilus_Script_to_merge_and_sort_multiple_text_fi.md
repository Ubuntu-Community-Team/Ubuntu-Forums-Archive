---
title: "Nautilus Script to merge and sort multiple text files"
date: 2017-11-15
forum: General Help
---

### Post by adec2 on 2017-11-15
Hi i'm adapting a script to merge multiple text files of different names and outputting the updated text file alphabetically so i can just select the text file, right click and combine them alphabetically and then automatically open the new text file in the default text editor
This is what I have and it works to a point but for some reason doesnt merge 2 or more selected files

#!/bin/sh
#Nautilus Script to join selected text files in a single file and open the joined file with default text editor
#
IFS=$'\n'
FILENAME="Updated.txt"
cat "$@" > "$FILENAME"
sort -d "$FILENAME" > UpdatedText.txt
rm "Updated.txt"
xdg-open "UpdatedText.txt"

Can anyone help please?

---

