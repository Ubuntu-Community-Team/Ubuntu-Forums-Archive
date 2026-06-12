---
title: "Default Text Editor"
date: 2007-07-30
forum: General Help
---

### Post by shiznatix on 2007-07-30
I have been trying to set the default text editor for a bit now without any progress. I installed gphpedit and would like to use it as my text editor instead of gedit.

If it is possible, I would only want to change it for html, css, js, php, and htc files. I figured I would try to just right click on the file with that type, and go to the 'open with' stuff. That does not work since there is no entry for gphpedit in the list of applications and when I tried to enter a custom command it never worked.

Then I found this tutorial: [http://ubuntuforums.org/showthread.php?t=299086](http://ubuntuforums.org/showthread.php?t=299086) and decided to just change all file types to gphpedit no matter what. Well now when I right click on a text file and go to the properties and go to the open with tab gphpedit is selected as the default but when I try to open it, it just loads in gedit.

Here is my ~/.local/share/applications/defaults.list file:

> [Default Applications]
application/x-perl=gphpedit.desktop
text/plain=gphpedit.desktop
text/x-chdr=gphpedit.desktop
text/x-csrc=gphpedit.desktop
text/x-dtd=gphpedit.desktop
text/x-java=gphpedit.desktop
text/mathml=gphpedit.desktop
text/x-python=gphpedit.desktop
text/x-sql=gphpedit.desktop

If someone could help me out that would be fantastic because I really just do not like gedit and gphpedit is perfect for my needs.

---

### Post by heimo on 2007-07-30
> **shiznatix said:**
> 
If it is possible, I would only want to change it for html, css, js, php, and htc files. I figured I would try to just right click on the file with that type, and go to the 'open with' stuff. That does not work since there is no entry for gphpedit in the list of applications and when I tried to enter a custom command it never worked.

That's the way I'd have tried to do it. Did you use 
```
/usr/bin/gphpedit
```
as the custom command?

---

### Post by shiznatix on 2007-07-30
Ok so actually the problem only exists when I am trying to open files that are mounted ftp or ssh stuff. Like I mount my test server through SSH and when I try to open a file that is in that computer it opens it in gedit instead of gphpedit. But when I open a file stored on my local machine it opens in phpedit no problem.

How can I fix this? I want all files to be opened though gphpedit because I am mostly working through the ssh so thats where all the real work is.

---

### Post by mannheim on 2007-07-30
If the remote volume is accessed as a gnome share (for example, using gnome's "Places-->Connect to Server" menu item, then very few applications (even very few gnome applications) will be able to read and write to it. gedit is one of the few. Probably gphpedit is not one of the few.  (To test, can you open files on the ssh volume using gphpedit's "Open" command?)

If gphpedit **is** one of the few that can do this, then I'm afraid I don't know the answer.

For most applications, the answer is to mount the ssh volume using fuse and sshfs. (First step, "sudo apt-get install fuse sshfs".) These tools allow you to mount the volume as a regular part of your filesystem, in which case any app can access them as usual.

---

### Post by shiznatix on 2007-07-30
> **mannheim said:**
> If the remote volume is accessed as a gnome share (for example, using gnome's "Places-->Connect to Server" menu item, then very few applications (even very few gnome applications) will be able to read and write to it. gedit is one of the few. Probably gphpedit is not one of the few.  (To test, can you open files on the ssh volume using gphpedit's "Open" command?)

I am able to open files in gphpedit no problem using the Open command so I don't see why there is a problem.

---

### Post by mannheim on 2007-07-30
OK. Assuming that gphpedit is able to do this, try the following. As you've done before, right-click on a file of the type you want to be opened by gphpedit. Select "Properties-->Open with" and then click "Add" and "Use custom command". Enter
```
gphpedit %U
```
I'm hoping that the "%U" will make it work. (If not, I'm afraid I give up.)

---

### Post by stchman on 2007-07-30
> **shiznatix said:**
> I have been trying to set the default text editor for a bit now without any progress. I installed gphpedit and would like to use it as my text editor instead of gedit.

If it is possible, I would only want to change it for html, css, js, php, and htc files. I figured I would try to just right click on the file with that type, and go to the 'open with' stuff. That does not work since there is no entry for gphpedit in the list of applications and when I tried to enter a custom command it never worked.

Then I found this tutorial: [http://ubuntuforums.org/showthread.php?t=299086](http://ubuntuforums.org/showthread.php?t=299086) and decided to just change all file types to gphpedit no matter what. Well now when I right click on a text file and go to the properties and go to the open with tab gphpedit is selected as the default but when I try to open it, it just loads in gedit.

Here is my ~/.local/share/applications/defaults.list file:



If someone could help me out that would be fantastic because I really just do not like gedit and gphpedit is perfect for my needs.

Easiest way is when you want to open a text file right mouse click, go to Open With tab and select your text editor of choice.

If the text editor is not there then you will have to do a custom command.  Do this for all the text files you wish to open.

Gedit is a great text editor IMO.

---

### Post by shiznatix on 2007-07-31
> **stchman said:**
> Easiest way is when you want to open a text file right mouse click, go to Open With tab and select your text editor of choice.

If the text editor is not there then you will have to do a custom command.  Do this for all the text files you wish to open.

Gedit is a great text editor IMO.

I have done this and when I go to the 'open with' stuff it shows the appropriate thing checked (gphpedit). But when I open it, it just bypasses gphpedit and opens in gedit.

I have some problems with gedit such as lack of php functions recognized, (dont know what its called but...) when you hold control and press a cursor direction gedit has some funky rules on where it goes next, and last but not least it adds blank tabs everywhere which is just annoying.

Thats why I want everything to always open in gphpedit but even though gphpedit can read from gnome shares no problem it won't open them directly from the file browser when browsing a gnome share.

---

### Post by mannheim on 2007-07-31
Did the "%U" thing work?

---

### Post by shiznatix on 2007-07-31
> **mannheim said:**
> Did the "%U" thing work?

No it did not work :(

---

### Post by heimo on 2007-07-31
Just to  make sure - this seems unlikely to work if your local files already open with gphedit - have you tried to right click, select properties, open with tab, choose gphedit, close and double clicking on the file? I don't have gphedit installed, but I just tested this with gvim over ssh and it works.

EDIT: Ok, I installed gph**p**edit and tried the method above, it doesn't work.

EDIT2: More testing. I forced gphpedit to open files from ssh shares by renaming gedit and symlinking gphedit to gedit. Double clicking resulted in an error that the file ssh://username@host/path/file.txt doesn't exist, asking if I'd like to create it. I clicked no, then went to file menu -> open, and it asks if I want to let gphpedit access keyring, in other words, password for ssh connection username@host. Allowing access will let me open files over ssh. Selecting *always allow* doesn't solve problem of opening files directly from nautilus by double clicking on them, it still says file doesn't exist. Hopefully this helps someone to tell how to solve this, or to file a bug report if necessary.

EDIT3: Tried googling for solution, don't you hate when you google for some problem and end up reading your own post? ;D

---

### Post by shiznatix on 2007-08-03
Thanks for going to indepth into helping find a solution but ya, it seams that this one is stuck for right now.

*sigh*

---

