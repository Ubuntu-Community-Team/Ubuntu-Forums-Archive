---
title: "convert pictures to a smaler size."
date: 2007-04-29
forum: General Help
---

### Post by Elena678 on 2007-04-29
hi hi, I would like to post some pictures, but they are much to big, is there a program that i can use to change all my pictures in one time to a smaler resolution??

greetings
Elena

---

### Post by madmetal on 2007-04-29
> **Elena678 said:**
> hi hi, I would like to post some pictures, but they are much to big, is there a program that i can use to change all my pictures in one time to a smaler resolution??

greetings
Elena

if you want just to post them , then you can use free online services like [http://www.imageshack.us/](http://www.imageshack.us/) who will provide you with a forum thumbnail..

UAResolved.

---

### Post by bashologist on 2007-04-29
#Install imagemagick:
sudo apt-get install imagemagick

#Use a loop to convert:
for img in *.jpg; do convert "$img" -resize 600x600 "re_$img"; done

#Links:
[http://www.imagemagick.org/script/command-line-tools.php](http://www.imagemagick.org/script/command-line-tools.php)
[http://www.imagemagick.org/script/convert.php](http://www.imagemagick.org/script/convert.php)

---

### Post by Elena678 on 2007-04-29
mmm, what you mean with the loop, when i have 3 pictures, 1.jpg, 2.jpg, 3.jpg in the folder pictures in my mane folder, what loop do i need to make than??

greetings

---

### Post by Steven_B on 2007-04-29
The loop is:
> for img in *.jpg; do convert "$img" -resize 600x600 "re_$img"; done
Open a terminal, change to the directory where your pictures are, and paste this into the terminal.
Essentially, you are saying "For each image named (anything).jpg, resize (name of image) to 600x600, and call it "re_(name of image)".  You can change the size and renaming to be whatever you need.

---

### Post by Elena678 on 2007-04-29
Thanks A Lot

---

