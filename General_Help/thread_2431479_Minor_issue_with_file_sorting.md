---
title: "Minor issue with file sorting"
date: 2019-11-17
forum: General Help
---

### Post by nocruoro on 2019-11-17
I have a minor pet peeve with Bionic Beavers 18.4 File Browser (Nautilus style) :?
 I have thousands of pictures in many folders which sometimes use the **& **symbol for example** [COLOR=#008000]"[/COLOR]**[COLOR=#008000]Mom & Dad 01"[/COLOR] while others might no icons have just letters or numbers or both.

I was a Windows user beforehand (and switched for greater security) and in File Explorer all files with **& **in the name niftily appear on top, always ahead of numbered images with only name and number like **Dad 01**. 
But Ubuntu isn't user friendly and just wants to push those to the bottom.

Is there any software, script or command which **always** places any icon names like **"Mom & Dad 01 **named files to the very top in a file explorer format. I already have them **Alphabetic Order Ascending (A-Z)**. (I want to avoid any tedius process of renaming thousands of images just to add a **and **word).

---

### Post by uRock on 2019-11-17
From what I've seen, Linux file managers will put filenames starting in special characters if they are to first charater of the filename, otherwise numbers are put first like in your situation. Mass renaming in Nautilus is easy.

Don't give up hope, yet, though. Someone else may know a workaround.

---

### Post by nocruoro on 2019-11-17
> **uRock said:**
> From what I've seen, Linux file managers will put filenames starting in special characters if they are to first charater of the filename, otherwise numbers are put first like in your situation. Mass renaming in Nautilus is easy.

Don't give up hope, yet, though. Someone else may know a workaround.

I hope so **&** is a tradition in my namings. I hate to change it. Ubuntu is already a hard decision after i nearly lost my current laptop to viruses.

---

### Post by uRock on 2019-11-17
> **nocruoro said:**
> I hope so **&** is a tradition in my namings. I hate to change it. Ubuntu is already a hard decision after i nearly lost my current laptop to viruses.

I was actually surprised when I tested to see that it treats filenames differently when the special character vs number wasn't at the beginning of the filename.  I tested it in both Thunar and PCmanFM.

---

### Post by nocruoro on 2019-11-17
> **uRock said:**
> I was actually surprised when I tested to see that it treats filenames differently when the special character vs number wasn't at the beginning of the filename.  I tested it in both Thunar and PCmanFM.

And people say ubuntu is flexible yet it drags you down if you're not careful.

---

### Post by uRock on 2019-11-17
> **nocruoro said:**
> And people say ubuntu is flexible yet it drags you down if you're not careful.

Something like that would never get me down. I can't blame ubuntu as that's how the file managers work on all Linux distros to my knowledge. I haven't used Windows at home since roughly 2010, so haven't thought much of how Windows Explorer displays files.

---

### Post by Holger_Gehrke on 2019-11-17
It probably can be done, but it would be **a lot** of work. You'd have to redefine the collation rules in your locale definition. See 'man locale', 'man localedef', 'man 5 locale' and probably 'man 5 charmap'. The sources for the definitions are in /usr/share/i18n/locales and the binary / compiled version are in /usr/lib/locale. You should only view these, you can create your own in your $HOME and make the system use those. The manual pages I mentioned give some examples on how to do that, but they are dense reading as man pages often are.

Holger

---

### Post by xadder on 2019-11-21
I am not sure why you blame linux for this. Linux uses a normal alphabetical order. How is it supposed to know that a & in the middle of the name means something special in the Windows world? In any case, no need to 'tediously' rename files; the command line is your friend. With the bash shell you can easily rename 1000s of files if you want. Just to get started, test something like (no need to type the # and following comments):

for i in "*\&*"   # this matches anything with & in the name.
do
  wc $i            # just do a work-count to test your script
done


Now, if this looks okay and you are feeling brave (test on a copied directory first!), you could replace the "wc  $i" with e.g. "mv $i 000icon_$i", which would move e.g. ''aaaa & bbb' to '000icon_aaa & bbb'. This which would ensure that all such files are alphabetically grouped at the beginning of the list.

More elegant, one could skip all those for loops, and just type:

rename "s/&/and/" *

in the directory and all is renamed :-)

I've only done brief tests on my system, but something like the above should work if this is what you need.

---

### Post by dragonfly41 on 2019-11-21
There is also [pyrenamer]("https://ubuntuforums.org/showthread.php?t=2425344&highlight=pyrenamer") to try.

[This 16.04 (last version) download seems to work in 18.04.]("https://ubuntu.pkgs.org/16.04/ubuntu-universe-amd64/pyrenamer_0.6.0-1.2_all.deb.html")

...

A second option. Since you refer to File Explorer (Nautilus) there are
python extensions to add to Nautilus.

[https://www.giuspen.com/nautilus-pyextensions/](https://www.giuspen.com/nautilus-pyextensions/)

[Download Nautlius PyExtensions.]("http://www.giuspen.com/software/nautilus-pyextensions_3.4.1-1_all.deb")

---

### Post by oldfred on 2019-11-21
Are you sure it is the & and not the spaces?

When I used Windows I often had spaces in file names. But in Linux that is not recommended and you have to either quote or escape names with spaces if typing into a command line. Not sure then how each gui program handles the spaces.
I learned to just use CamelCase, under_score, or justaname.

When you mount Windows NTFS partitions it also is recommended to use windows_names.
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20)

---

