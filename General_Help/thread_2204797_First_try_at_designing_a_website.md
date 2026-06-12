---
title: "First try at designing a website"
date: 2014-02-10
forum: General Help
---

### Post by mattdlyons00 on 2014-02-10
Although I have been trolling around the Ubuntu forums for about 8 years now this I believe is my very first post. I am starting a website and basically I am looking for advice. The websites basic need are as follows 


[LIST]
[*]HTML5 and CSS3 only no specific local software on the users computer or device.
[/LIST]

[LIST]
[*]An Open Source framework.
[/LIST]

[LIST]
[*]An Open Source CMS.
[/LIST]

[LIST]
[*]An Open Source PDF, EPUB reader.
[/LIST]

[LIST]
[*]An Open Source CBZ, CBR reader.
[/LIST]

[LIST]
[*]Ability to tag files so that users can search by Author, Title, ISBN, Genre.
[/LIST]

[LIST]
[*]Ability for users to upload files.
[/LIST]

[LIST]
[*]User accounts for users to save preferences suggestions and other information across visits.
[/LIST]

I am looking at Symfony and Silverstripe as a framework and CMS. Any other suggestions on what would be better would be extremely appreciated. I am planning on purchasing server space and collecting as many public domain works as I can get my hands on for my users to read anytime anywhere and creating a space for independent authors, and comic book writers to share their works.

---

### Post by lykwydchykyn on 2014-02-10
So are you committed to PHP on the server side?  I'm not sure if ebook, PDF, CBZ, or CBR libraries exist for PHP.  That's probably the first point you want to look into before commiting to a server-side language.  If you find a language that has libraries for those things, the rest is probably fairly trivial in any language.

If you can't find PHP libraries, Python or Java would be the next place to check.

---

### Post by mattdlyons00 on 2014-02-12
Sorry about the late reply I work full-time plus school and thanks for the advice. Do you know any specific libraries which might accommodate my needs?

---

### Post by Bucky Ball on 2014-02-12
*Thread moved to[I] **General Help***[/I].

This is really a support request and you have a better chance of getting advice here. ***The Cafe*** is a non-support area. 

And welcome, finally, to the forums! There is an 'introduce yourself' thread in Community Discussions somewhere. ;)

---

### Post by mattdlyons00 on 2014-02-12
Thanks for the move, I will go ahead and introduce myself and I noticed your distro and to you sir I say good job Xubuntu is where I live.

---

### Post by Bucky Ball on 2014-02-12
Well, it's kind of a lie, really. I use minimal installs with xfce4 as the desktop environment with apps added to suit the machines role in life. Not 'off the shelf', although I do have a regular install of Xubuntu around somewhere. The last resort if everything else falls over! ;)

---

### Post by mattdlyons00 on 2014-02-12
And the similarities just keep piling up I use xfce4 in about the same way with openbox. Xfce has always been my go to manager I am pretty minimal and so it fits my needs.

---

### Post by lykwydchykyn on 2014-02-12
> **mattdlyons00 said:**
> Do you know any specific libraries which might accommodate my needs?

I do not.

---

### Post by SeijiSensei on 2014-02-12
> **lykwydchykyn said:**
> So are you committed to PHP on the server side?  I'm not sure if ebook, PDF, CBZ, or CBR libraries exist for PHP.  That's probably the first point you want to look into before commiting to a server-side language.  If you find a language that has libraries for those things, the rest is probably fairly trivial in any language.

If you can't find PHP libraries, Python or Java would be the next place to check.

PDF for PHP:  [http://www.php.net/manual/en/book.pdf.php](http://www.php.net/manual/en/book.pdf.php)

CBZ looks like a simple [ZIP-compressed collection of images]("http://whatis.techtarget.com/fileformat/CBZ-Comic-book-or-paperback-ZIP-file-decompress-with-WinZip-or-similar-program").  You could write a PHP routine to unzip the file, then display the images.  I don't know how the order is encoded into the file though; you'd have to read the file specification.  I did see some websites talking about using [Imagemagick]("http://www.imagemagick.org/") to manage CBZ files; the Imagemagick libraries are accessible in PHP [via a PEAR class]("http://us1.php.net/manual/en/class.imagick.php").

And remember that you can [run shell commands]("http://us1.php.net/manual/en/book.exec.php") within PHP, in case there are routines for which you need command-line tools.

---

### Post by mattdlyons00 on 2014-02-12
Well thank you sensei I will look into those i appreciate the response. If yo dont mind my asking what anime is your avatar from? The animation style looks familiar but I cant quite place it.

---

### Post by SeijiSensei on 2014-02-13
He's the Emperor of En from [Junni Kokki](http://en.wikipedia.org/wiki/The_Twelve_Kingdoms) ("Twelve Kingdoms").

---

