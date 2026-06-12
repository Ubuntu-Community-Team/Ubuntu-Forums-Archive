---
title: "Help with Directory Structure Naming"
date: 2012-11-07
forum: General Help
---

### Post by Quarkrad on 2012-11-07
I'm trying to copying my photo collection of thousands of photos that are in a folder structure into a single folder so that I can look at managing my collection via tagging rather than having a fixed folder structure.  I have looked at several terminal commands and I'm getting to understand(!) what they mean.  However, they all fall down with the folder names - I keep getting messages such as **No such file or directory** - so my naming must be wrong. I keep trying different things like /Home/Pictures/photos, or I cd to Pictures and try photos/ or /photos/ but I'm not getting it right. My latest failure is:

dad@dadubuntu:~$ find /Home/Pictures/photos -type f -exec cp {} /Home/Pictures/single folder/ \;
find: &#8216;**/Home/Pictures/photos**&#8217;: No such file or directory
dad@dadubuntu:~$ 


so in my **Pictures** folder I have my photo collection in a top level folder called **photos**.  I'm trying to copy all the files into another folder in **Pictures** called **single folder**.  Any help appreciated as I have too many photo files to copy and paste - this would truely help if I can get this naming convention right.

---

### Post by muteXe on 2012-11-07
it's 'home'. not 'Home'

---

### Post by Quarkrad on 2012-11-07
Still doesn't work.

[B]dad@dadubuntu:~$ find /home/Pictures/photos -type f -exec cp {} /home Pictures/single folder/ \;
find: ‘/home/Pictures/photos’: No such file or directory
dad@dadubuntu:~$ sudo find /home/Pictures/photos -type f -exec cp {} /home Pictures/single folder/ \;
[sudo] password for dad: 
find: ‘/home/Pictures/photos’: No such file or directory
dad@dadubuntu:~$ [/B]

note.  this is a test of only four sub folders and a small number of files within each in Picures/photos.   If I can get this to work I will try on my actual collection.

---

### Post by Cheesemill on 2012-11-07
You're missing your username, the full path should be:
```
/home/dad/Pictures/photos
```
or
```
~/Pictures/photos
```
~ is a shorthand way of writing your home directory.

---

### Post by Quarkrad on 2012-11-07
That did it - many thanks.

---

### Post by Quarkrad on 2012-11-18
For some reason I'm getting outputs with a lock and cross when I use this command:

sudo find /home/dad/Desktop/old -type f -exec cp {} /home/dad/Desktop/new \;

or 

sudo find /home/dad/Desktop/old -type f -exec cp {} /home/dad/Desktop/new/ \;
 
see attached.  

I can't understand while this is happening.  Also, despite my efforts to get rid or rename duplicates before I execute this command some do get through. Is there a way to ammend this command so that if a duplicate file (they are photos)  is found it is renamed reather than over written?

---

### Post by Cheesemill on 2012-11-18
Its because you're using sudo when you don't have to.

Because you are using sudo then the file copy operation is being carried out by root, which is changing the ownership of the files accordingly. As you are only working with files in your own home folder there is no need to use sudo at all.

To change them back you can do:
```
sudo chown -R dad.dad /home/dad/Desktop/new
```

---

### Post by Quarkrad on 2012-11-18
That did it - many thanks.  Can you help on adding an additional element to my 'folder copying' command that will address the issue about duplicate file names?   It is poosible for me to have duplicate file names in differenr sub folders that are different photos - so, if possible, I would rather not have duplicates over-written if found - but ideally renamed.

---

### Post by steeldriver on 2012-11-18
maybe not exactly what you want but a quick and dirty way to handle that might be to use the --backup parameter in cp

```
$ find . -type f -exec cp -v -t ./ --backup=numbered '{}' \;
`./dir2/file2' -> `./file2'
`./dir2/samefile' -> `./samefile'
`./dir1/file1' -> `./file1'
`./dir1/samefile' -> `./samefile' (backup: `./samefile.~1~')

```i.e. it renames the 'old' file(s) rather than the 'new' file

```
$ ls -R
.:
dir1  dir2  file1  file2  samefile  samefile.~1~

./dir1:
file1  samefile

./dir2:
file2  samefile
```

---

### Post by Quarkrad on 2012-11-18
Sorry - I'm a newbie so need a bit of hand holding.  Thanks for your help.  In **old** I have 28 sub folders and probably that many again sub sub folders.  In all, there are 6573 items - 99%+ of these are actual photos plus a few 'system' files inserted in various places by the Photo Applications like Picasa or Digikam.  I can, sort of, work out what your first line is doing if I enter it into the Terminal (assume I cd to the **old** directory).

 find . -type f -exec cp -v -t ./ --backup=numbered '{}' \;

But I'm not sure where these lines fit in.  I think I have too many directories.

`./dir2/file2' -> `./file2'
`./dir2/samefile' -> `./samefile'
`./dir1/file1' -> `./file1'
`./dir1/samefile' -> `./samefile' (backup: `./samefile.~1~')

---

### Post by Vaphell on 2012-11-18
this is just an example what is supposed to happen if you have duplicates.
**cp -v** is copying in verbose mode and you get to see something along the lines of 
```
`./dir1/samefile' -> `./samefile' (backup: `./samefile.~1~')
```
in its output.

---

### Post by steeldriver on 2012-11-18
yes my apologies - those other lines are just the verbose **output** from cp because I added the -v switch (just to show you the steps it was doing)

For your case, you'd probably want to keep your current command but just add the --backup=numbered parameter

```
find /home/dad/Desktop/old -type f -exec cp **[COLOR=Red]--backup=numbered[/COLOR]** {} /home/dad/Desktop/new/ \;
```If you have LOTS of files you might want to consider using a form that handles long argument lists a bit more robustly, either

```
$ while read -r -d $'\0' file; do cp **[COLOR=Red]--backup=numbered[/COLOR]** "$file" /home/dad/Desktop/new/ ; done < <(find /home/dad/Desktop/old -type f -print0)
```

or

```
find /home/dad/Desktop/old -type f -print0 | xargs -0 cp **[COLOR=Red]--backup=numbered [/COLOR]**-t /home/dad/Desktop/new/
```

---

### Post by Quarkrad on 2012-11-19
I've done some work and I think I am 'there' but I still need some help -if that's OK.  In **old** I have 6530 items of which 258 are directories.  So after running the command I should get 6272 items/photos in **new**.  When I run all three versions of your command I get in **new** 4726 jpg photos and 1546 files in the form xxxx.jpg~1~  so the command is working - in **new** I get 6272 items.  For example in **old** I have 4 different photos, with the same file name called DSCF0012.jpg.  After I run the command I get in **new** DSCF0012.jpg, DSCF0012.jpg~1~, DSCF0012~2~, DSCF0012.jpg~3~.  In nautilus I can see the image of DSCF0012.jpg but the other 3 ~x~ files are shown with a text type icon (see attached).  I guess I need a new command to change these ~x~  into something like DSCF00121, DSCF00122, DSCF00123.  I have 1546 of these files - and they are all unique file name wise.

---

### Post by steeldriver on 2012-11-19
You can probably just bulk rename those using the perl-based 'rename' command so that they have the correct .jpg suffix - something like

```
$ rename -vn 's/\.jpg\.~([0-9]+)~/-$1.jpg/' *.jpg.*
```The '-vn' switches make it report what it would do but not actually do it - once you have checked that it does the right thing you can remove the 'n' - it should produce something like

```

file.jpg.~1~ renamed as file-1.jpg
file.jpg.~2~ renamed as file-2.jpg
file.jpg.~3~ renamed as file-3.jpg

```We can play with the replacement name format if file-N.jpg is not to your liking

---

### Post by Vaphell on 2012-11-19
try this
```
rename -nv 's/(.+)[.](.+)[.]~(.+)~/$1$3.$2/' *~?~
```
n means dry run, if you are sure proposed names are ok, remove that n from the parameter.

oops, too late

---

### Post by steeldriver on 2012-11-19
> **Vaphell said:**
> 
oops, too late

but more elegant - as always :biggrin:

---

### Post by Quarkrad on 2012-11-19
Done it - thank you so much for all your help.  I believe your solutions will help a lot of people.

---

