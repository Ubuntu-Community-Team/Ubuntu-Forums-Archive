---
title: "mobi to epub conversion (or the opposite)"
date: 2015-01-08
forum: General Help
---

### Post by benpietras on 2015-01-08
I leave this as a guide to my future self, as I am forgetful.
(if you want epub -> mobi, just swop the two in the commands below)


If you have a folder full of mobi files in separate folders, and you want to convert to epub format, do this

mkdir mobi (where a copy of just the .mobi files will be sent
shopt -s globstar
cp **/*.mobi mobi/
cd mobi
for book in *.mobi; do echo "Converting $book"; ebook-convert "$book" "$(basename "$book" .mobi).epub"; done  
mkdir ../epub
mv *.epub ../epub

Now calibre can be used to put them on your nook, or just directly copy and paste.

---

