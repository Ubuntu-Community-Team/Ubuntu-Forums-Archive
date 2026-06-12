---
title: "Collect jpeg"
date: 2020-06-10
forum: General Help
---

### Post by sergiofreeman on 2020-06-10
Hi there, 

I'm looking for an application that allow me to collect all jpeg from many files to just One File. 
I appreciate your help

thank you in advance

---

### Post by ActionParsnip on 2020-06-10
What do you mean? do you mean make a big image out of all images or do you mean put all images into one directory?

Can you please expand the question?

Thanks

---

### Post by CelticWarrior on 2020-06-10
Welcome.

What do you mean by "collect all jpeg from many files to just One File"? To start with something, "jpeg" is a file, not a file characteristic or content to be collect from it, jpeg is a type of image file.

Do you want to have a file containing many jpeg files? If so there are dozens of tools and file formats for that - ZIP and RAR are arguably the most used and know - some are Unix/Linux specific, most aren't, most work in any OS family.
Or you want to make a composite image from different jpeg files? If so you need a image editor.

---

### Post by sergiofreeman on 2020-06-10
Sorry, Yes I have many folders full of jpgs mixed with many other type of  documents, it's a hard process to select one by one each jpg that I want  to save out of so many html, txt, .doc and so many other documents.  then I'm looking for an application that select that jpg for me and save  them on a folder

---

### Post by sergiofreeman on 2020-06-10
yes sorry I said file when should be folder, sorry for my mistake

---

### Post by sergiofreeman on 2020-06-10
put all images into one directory, that's correct, that's what I wanna do

---

### Post by CelticWarrior on 2020-06-10
There's no application specifically for that purpose but anyone can write a script that does that. However...

[LIST=1]
[*]The people here that can do that really don't like to do other people's homework. They can help debugging and suggesting but won't do something from scratch.
[*]Any such script must be very specific with the specific paths of your system; a generic script can be written and it's up to you to adapt it to your specific configuration/needs and that's a problem in itself: Knowing that you're here asking for an "application" it's safe to assume you wouldn't be able to adapt said script to suit your needs.
[/LIST]

Alternatively, you can use the standard file manager where files can be shown by file type. Then just select all of intended file type simply by clicking the first in the list and shift-clicking the last one and using the typical copy/paste in another tab or window.

---

### Post by SeijiSensei on 2020-06-10
```

mkdir /home/yourusername/myimages

cd /path/to/a/directory/with/some/image/files
mv -f *.jpg /home/yourusername/images
mv -f *.JPG /home/yourusername/images
mv -f *.jpeg /home/yourusername/images
mv -f *.JPEG /home/yourusername/images
# if you want to move other types
mv -f *.png /home/yourusername/images
mv -f *.gif /home/yourusername/images

[rinse and repeat]

```

---

### Post by T6&amp;sfpER35% on 2020-06-11
[https://forums.linuxmint.com/viewtopic.php?f=90&t=321638](https://forums.linuxmint.com/viewtopic.php?f=90&t=321638)  should also help

---

### Post by HermanAB on 2020-06-11
Hmm, "*' includes "." and '*' also includes nothing.

There also is an obscure way to make the Bash shell globbing case insensitive:
shopt -s nocaseglob

So the rest becomes:
mkdir /home/yourusername/myimages

cd /path/to/a/directory/with/some/image/files
mv -f *jp*g /home/yourusername/images
# if you want to move other types
mv -f *png /home/yourusername/images
mv -f *gif /home/yourusername/images

[rinse and repeat]

There - saved you some typing.

---

