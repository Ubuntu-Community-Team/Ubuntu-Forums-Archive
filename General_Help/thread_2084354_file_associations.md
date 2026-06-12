---
title: "file associations"
date: 2012-11-15
forum: General Help
---

### Post by Wim Sturkenboom on 2012-11-15
I like programs to be associated with the file content (as returned by the file command) and not with the file extension. If I have e.g. a picture called 'screenshot.txt' (yes, you can call me an idiot), it needs to be opened with an image viewer and not with gedit if I double click it in Nautilus.

How do I achieve this?

Using both 10.04 and 12.04.

---

### Post by rnerwein on 2012-11-15
> **Wim Sturkenboom said:**
> I like programs to be associated with the file content (as returned by the file command) and not with the file extension. If I have e.g. a picture called 'screenshot.txt' (yes, you can call me an idiot), it needs to be opened with an image viewer and not with gedit if I double click it in Nautilus.

How do I achieve this?

Using both 10.04 and 12.04.
hi
yeah for nautilus it would be useful to use the file command. but on the side somtimes
it's funny that some software don't use this command.
if i try to send a file ends with .exe mail mailer tells me: it's not allowed to executable files !
ok i renamed the file to .txt - and here we go :-))

---

### Post by Wim Sturkenboom on 2012-11-18
Bug reported

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1080328](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1080328)

---

### Post by zombifier25 on 2012-11-18
Don't mind if I mark that bug as affecting me :P

---

### Post by LewisTM on 2012-11-18
Playing around with the File Types Editor (assogiate), I found some important info but no solution.

1) The MIME subsystem gives precedence to file extension over file contents when guessing a file type.

2) The solution would be to edit type text/plain and remove extension .txt
However, in practice, that's impossible. The file type is LOCKED for anything but adding stuff.

Perhaps the bug report should contain a reference to this potential but inoperable workaround.

Cheers!

---

### Post by Peter Maunder on 2012-11-18
Should this not be a request for new function rather than a bug?  The file extension, on some systems  the filetype, has been used to define the format of the associated file for quite a while. Only some types of file incorporate a heading  which gives a definitive clue to the type of file. 
Would there not also be a performance hit if you always had to open a file to find out what it was, unless you had the ability to turn off the function? Also if you had to open the file to find out you could not process it further. Perhaps you could limit the function to particular folders?

---

### Post by Morbius1 on 2012-11-18
> **Peter Maunder said:**
> Should this not be a request for new function rather than a bug?  The file extension, on some systems  the filetype, has been used to define the format of the associated file for quite a while. 
Is that true? UNIX had no file extensions. A "." was just another legal character. Windows is another matter.

---

### Post by mc4man on 2012-11-18
As far as the bug report - not really Ubuntu's problem/issue/concern, you should file upstream
(whether you get any positive response from the gnome/nautilus/redhat dev's is questionable
[https://bugzilla.gnome.org/](https://bugzilla.gnome.org/)

---

### Post by Wim Sturkenboom on 2012-11-18
I agree that extensions don't exist in a NIX environment and therefor it's a bug and not a request.

And support in the bug report is always welcome ;)

And it's an Ubuntu problem; I don't know how far the Ubuntu developers have modified the code to tailor it to Ubuntu's needs and therefor those developers might have introduced the bug. So I drop it in their lap and they can take it upstream if that is where the problem is.

---

### Post by LewisTM on 2012-11-18
> **Peter Maunder said:**
> 
Would there not also be a performance hit if you always had to open a file to find out what it was, unless you had the ability to turn off the function?
I agree, there is nothing magical about MIME type determination by content, it does take its toll. You don't enter a store and open every box and bag to learn what's inside, you read the labels. For the same reason, files are opened only when the extension is absent or unknown. It's not a bug, it's a compromise.

---

### Post by mc4man on 2012-11-18
> **Wim Sturkenboom said:**
> 

And it's an Ubuntu problem; I don't know how far the Ubuntu developers have modified the code to tailor it to Ubuntu's needs and therefor those developers might have introduced the bug. So I drop it in their lap and they can take it upstream if that is where the problem is.
Well I'm running the latest nautilus git on 13.04 & the behavior is the same - nothing that Ubuntu has done.

---

### Post by Wim Sturkenboom on 2012-11-18
> **LewisTM said:**
> I agree, there is nothing magical about MIME type determination by content, it does take its toll.I don't know how it exactly works (often the first few bytes in a file indicate something) but it takes about 0.03 seconds for a 11MB jpeg on an i3 system and double of that for a 2MB jpeg on an old Atom netbook.

Not really something that will bother me, starting the application takes more time.

```

wim@i3-2120:~/Desktop/photos/fortyfourgalena$ time file IMGP2303.jpg
IMGP2303.jpg: JPEG image data, JFIF standard 1.01

real	0m0.032s
user	0m0.000s
sys	0m0.000s
wim@i3-2120:~/Desktop/photos/fortyfourgalena$ ls -l IMGP2303.jpg 
-rw-r--r-- 1 wim wim 11178055 Jan  4  2011 IMGP2303.jpg
wim@i3-2120:~/Desktop/photos/fortyfourgalena$ 

```

---

### Post by Wim Sturkenboom on 2012-11-18
> **mc4man said:**
> Well I'm running the latest nautilus git on 13.04 & the behavior is the same - nothing that Ubuntu has done.
Bit much asked from an ordinary user to start using something outside the repositories to check if a bug is an ubuntu bug or an application bug.

---

### Post by zombifier25 on 2012-11-19
> **Wim Sturkenboom said:**
> I don't know how it exactly works (often the first few bytes in a file indicate something) but it takes about 0.03 seconds for a 11MB jpeg on an i3 system and double of that for a 2MB jpeg on an old Atom netbook.

Not really something that will bother me, starting the application takes more time.

```

wim@i3-2120:~/Desktop/photos/fortyfourgalena$ time file IMGP2303.jpg
IMGP2303.jpg: JPEG image data, JFIF standard 1.01

real	0m0.032s
user	0m0.000s
sys	0m0.000s
wim@i3-2120:~/Desktop/photos/fortyfourgalena$ ls -l IMGP2303.jpg 
-rw-r--r-- 1 wim wim 11178055 Jan  4  2011 IMGP2303.jpg
wim@i3-2120:~/Desktop/photos/fortyfourgalena$ 

```

You are correct. The part of the file that identifies its type is called [magic numbers](https://en.wikipedia.org/wiki/List_of_file_signatures).

---

