---
title: "Extracting and assembling .RAR files, How?"
date: 2008-06-05
forum: General Help
---

### Post by Benbow on 2008-06-05
I have 2 cd files each with 49 .RAR files in them. The whole, when extracted and assembled should produce one video to copy to DVD. Is there an easy way to do this - I am a fairly new guy.

---

### Post by F4l3 on 2008-06-05
> **Benbow said:**
> I have 2 cd files each with 49 .RAR files in them. The whole, when extracted and assembled should produce one video to copy to DVD. Is there an easy way to do this - I am a fairly new guy.
you have to install rar-nonfree ;)

---

### Post by milton1 on 2008-06-05
if you have unrar installed, simply extracting the main .rar file should assemble the rest.

---

### Post by dolman29 on 2008-07-12
how do u do this from the command line
 
unrar-free, which i used first wouldn't extract all the rar's to the avi file, then when i tried unrar it told me, no files to extract. previously i copied the folder to my desktop, so i tried "unrar e file.01.rar" and it worked. All files was extracted with one command. so unrar-free must of messed the files up.  is there away to reverse the unrar-free problem.

---

### Post by iaculallad on 2008-07-12
> **Benbow said:**
> I have 2 cd files each with 49 .RAR files in them. The whole, when extracted and assembled should produce one video to copy to DVD. Is there an easy way to do this - I am a fairly new guy.

I had just successfully downloaded UFC 86 torrent (CD1 and CD2), it contained 50 files (1=.rar file, 1=.svf file, and 48 files numbered from r00-r48 )) for disk 1. The way I extracted this is just to right-click on file named **aaf-ufc86a.r00** and choose "Extract Here". Final output: all files are extracted to just 1 file named **aaf-ufc86a.avi**.
I did the same procedure with the disk 2.

---

### Post by jonlemur on 2008-07-12
To install unrar ```
sudo apt-get install unrar
```
If there is a main rar file, then ```
unrar -x main.rar
```should do it (man unrar for more details.  You may have to include a destination path).  If there is one file with a bunch of "non-main" rar files in it, you should be able to use ```
unrar -x ./*.rar
``` to extract all .rar files in the current directory.

---

### Post by syxbit on 2008-07-13
that command 'unrar -x ./*.rar' doesn't work
(for starters, i don't think you need the '-' before the 'x'
but still can't get it to work

---

### Post by kaligus on 2008-07-13
I simple use the various archive managers, right click, "extract here" from the file manager.

Just for fun prior to installing my registration to rar or the unfree rar component I dug out floppy, cd, and dvd media with various sizes and types of split rar files... then repeated the tests after installing unfree rar, and again after installing my registration.

filename.partxx.rar
filename.rxx 

Some on multiple media, from winrar as early as 2.x and as late as 3.7x (first registered version through last registered version)

I just tried again with 
"unrar x archive.rar"
and
"unrar x archive.rar /path-to-extract/"
with the same success, though if I don't get the replacement media rapidly enough I will get errors.

(Ubuntu 8.04, AMD 64)

---

### Post by sofasurfer on 2008-08-17
In my situation I have a directory call "my movie". Inside this directory is 90 files called... 
sample.avi
my movie (cam).part001.rar
my movie (cam).part002.rar
my movie (cam).part003.rar
etc

I installed unrar.

Now I click on "my movie (cam).part001.rar.
Archive manager open with the file "my movie (cam).avi" in the window.
I click on it and it asks for my password. I enter it and archive manager says "extracting files".  After a few minutes it asks for password again. And I go through the process again and again. Is the process working or am I stuck in an endless loop?

---

