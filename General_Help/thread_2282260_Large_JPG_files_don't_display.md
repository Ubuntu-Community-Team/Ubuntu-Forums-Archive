---
title: "Large JPG files don't display"
date: 2015-06-12
forum: General Help
---

### Post by RayTomes on 2015-06-12
I have just loaded some JPG files from my phone. The ones that are 1920x1080 and about 0.5MB display fine wit the default picture display program (I am clicking on file in files display). But the 5312x2988 and about 5MB ones do not display. Is this because they are bigger than the screen or what?

On Win-XP I used Irfanview and it rescales everything to fit to the screen. Do I need to learn about WINE?

---

### Post by papibe on 2015-06-12
Hi RayTomes.

The 'image viewer' can be called as 'eog' from the command line. Try opening a big picture from the terminal so if there are any error message, you can see it on the terminal:

First change to the directory where the pictures are. For instance:
```
cd Pictures 
```
and then open a big picture like this:
```
eog name_of_big_picture.jpg
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by RayTomes on 2015-06-13
Thanks papibe.

The first time I put the long file name of the file and it didn't load so I closed the window and there was a message:
(eog:5871): EOG-WARNING **: Failed to open file ' .... '   and a lot of stuff with a wrong file name and extension

To simplify things I renamed the file test.jpg and tried to reload with the eog command again. This time the picture was still not displayed and there was no error message. I don't understand that at all.

---

### Post by coldraven on 2015-06-13
> (eog:5871): EOG-WARNING **: Failed to open file ' .... '   and a lot of stuff with a wrong file name and extension


If you had posted the whole of the error message we could help solve your problem.
Also what is the file extension of these big files?

---

### Post by sudodus on 2015-06-13
Papibe's tip to start the image viewer from a terminal window is good.

My 2 cents worth of advice is to try other image viewers or image editors and hope one of them will either manage to display the picture or print an error message, that will help us find the problem.

viewers: (you have ***eog***), ***feh***, ***ristretto***, ***gpicview***, ***display*** (install imagemagick), ***gthumb*** ...

editors: start with [SIZE=3]***gimp***[/SIZE]

---

### Post by RayTomes on 2015-06-13
I was obviously trying to load JPG. The error message had a very long sequence of random stuff and was PNG. I tried to copy and paste but couldnt work out how to copy from terminal window.

---

### Post by RayTomes on 2015-06-13
I tried to open with "open with" and the only other viewer was shotwell and it did successfully load the image. I looked at list of more applications but could not see gimp. It was good to find out about this viewer as it has a couple of useful features. It took me some time to find out how to go to next image in folder. OK, now I learned to hit F1 for help.

Is there any way to make showell viewer my default image viewer?

---

### Post by RayTomes on 2015-06-13
OK, I searched for defaults and changed my default image program to shotwell. SOLVED

---

### Post by sudodus on 2015-06-14
> **RayTomes said:**
> I tried to open with "open with" and the only other viewer was shotwell and it did successfully load the image. I looked at list of more applications but could not see gimp. It was good to find out about this viewer as it has a couple of useful features. It took me some time to find out how to go to next image in folder. OK, now I learned to hit F1 for help.

Is there any way to make showell viewer my default image viewer?

If you haven't got a program, you can easily install it from the Ubuntu repositories, many good programs are there :-)

1.with the Ubuntu Software Center

2. or the command line line a terminal, for example

```
sudo apt-get install gimp
```

---

### Post by sudodus on 2015-06-14
Congratulations :KS

I'm glad ***shotwell*** works with this file (these files). Did you notice that shotwell is primarily a ***photo organizer***, a tool to import photos from your camera and to keep track of all your photos?

```
man shotwell
```

```
shotwell(1)                                                                                shotwell(1)

NAME
       shotwell - a digital photo organizer

DESCRIPTION
       shotwell is a digital photo organizer designed for the GNOME desktop environment. It allows you
       to import photos from disk or camera, organize them in various ways, view them  in  full-window
       or fullscreen mode, and export them to share with others.

AUTHOR
       shotwell was written by Jim Nelson, Lucas Beeler and Allison Barlow.

       This  manual  page  was  written  by Devid Antonio Filoni <d.filoni@ubuntu.com>, for the Debian
       project (and may be used by others).

                                           December 30, 2009                               shotwell(1)

```

---

