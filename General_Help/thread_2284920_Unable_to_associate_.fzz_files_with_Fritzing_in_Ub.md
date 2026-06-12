---
title: "Unable to associate .fzz files with Fritzing in Ubuntu 12.04 LTS"
date: 2015-07-02
forum: General Help
---

### Post by boxcorner on 2015-07-02
Hello

I have installed Fritzing via Ubuntu Software Centre
Could someone please tell me how to associate .fzz files with Fritzing ?

What I have tried : 

Right-clicking .fzz file > Properties > Open With
but Fritzing is missing from Other Applications.

Right-clicking .fzz file > Properties > Open With
then clicking on Reset

With gedit I have edited 
~/.local/share/applications/mimeapps.list
I have added application/fzz=fritzing.desktop; under [Added Associations]

Also, I have tried re-booting Ubuntu after making the changes above, all to no avail :~\

---

### Post by mc4man on 2015-07-02
To show up in the context menu > open with > ....  fritzing.desktop's Exec= line needs to end in %a letter,  %f would be ok, ex. in screen
So open /usr/share/applications/fritzing.desktop in a root text editor & add it  to the end of the  line

As far as defaults  - .fzz would be seen as a zip archive  (application/zip) so changing the default for that would change for all zip files, not just .fzz
(- maybe possible to add a new mime, I've no time for that now, should be posts in forum on how to do (or try...

---

### Post by mc4man on 2015-07-02
had a few minutes, pretty easy. Really just do as described here - 
[http://ubuntuforums.org/showthread.php?t=1976921&p=11924283&viewfull=1#post11924283](http://ubuntuforums.org/showthread.php?t=1976921&p=11924283&viewfull=1#post11924283) or read thru thread, ect
screens show -

ex. of fzz.xml
```
<?xml version="1.0" encoding="UTF-8"?>
<mime-info xmlns="http://www.freedesktop.org/standards/shared-mime-info">
    <mime-type type="application/x-fritz">
        <comment>Fritz files</comment>
        <glob pattern="*.fzz"/>
    </mime-type>
</mime-info>
```

---

### Post by boxcorner on 2015-07-02
Thank you

> **mc4man said:**
> had a few minutes, pretty easy. Really just do as described here - 
[http://ubuntuforums.org/showthread.php?t=1976921&p=11924283&viewfull=1#post11924283](http://ubuntuforums.org/showthread.php?t=1976921&p=11924283&viewfull=1#post11924283) or read thru thread, ect
screens show -

ex. of fzz.xml
```
<?xml version="1.0" encoding="UTF-8"?>
<mime-info xmlns="http://www.freedesktop.org/standards/shared-mime-info">
    <mime-type type="application/x-fritz">
        <comment>Fritz files</comment>
        <glob pattern="*.fzz"/>
    </mime-type>
</mime-info>
```
Thank you.
I created fzz.xml in ~/Documents
then did
sudo xdg-mime install --novendor  ~/Documents/fzz.xml 
which took its time, but eventually returned to ~$
Now, I expect this is probably a very silly question, but where is the current .desktop file located?

---

### Post by mc4man on 2015-07-02
> **boxcorner said:**
> Thank you.
I created fzz.xml in ~/Documents
then did
sudo xdg-mime install --novendor  ~/Documents/fzz.xml 
which took its time, but eventually returned to ~$
Now, I expect this is probably a very silly question, but where is the current .desktop file located?
```
sudo -H gedit /usr/share/applications/fritzing.desktop
```
edit the Exec= line as shown & remove the existing Mime line, add this to bottom
```
MimeType=application/x-fritz
```
So the .desktop would be this - 

```
[Desktop Entry]
Name=Fritzing
Exec=Fritzing %f
Icon=fritzing_icon.png
Categories=Development;Engineering;Electronics
Type=Application
Terminal=false
Comment=PCB-Suite
GenericName[en]=Easy-to-use electronic design software
GenericName[es]=Software de diseño electrónico de fácil uso
MimeType=application/x-fritz
```

The existing mime in the .desktop makes no sense to me - text/pro

---

### Post by boxcorner on 2015-07-03
> **mc4man said:**
> ```
sudo -H gedit /usr/share/applications/fritzing.desktop
```
edit the Exec= line as shown & remove the existing Mime line, add this to bottom
```
MimeType=application/x-fritz
```
So the .desktop would be this - 

```
[Desktop Entry]
Name=Fritzing
Exec=Fritzing %f
Icon=fritzing_icon.png
Categories=Development;Engineering;Electronics
Type=Application
Terminal=false
Comment=PCB-Suite
GenericName[en]=Easy-to-use electronic design software
GenericName[es]=Software de diseño electrónico de fácil uso
MimeType=application/x-fritz
```

The existing mime in the .desktop makes no sense to me - text/pro

Thank you very much, I have done : 
sudo -H gedit /usr/share/applications/fritzing.desktop
but it produces this :
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory

Also, I have just noticed that I cannot access the CD in my laptop's drive, which contains the .fzz files!
I don't know why, but when I insert the CD (or any other CD) it just spins for a while and then stops. 
When I run the Files app, the CD drive does not appear, .
When I run the Disks app, it shows CD Drive /dev/sr0 (Read-Only) and ejects the CD all right.
I don't know whether the memory leak problem is connected, nor what to do to fix it.

**Addendum**
I downloaded a .fzz file from [http://fritzing.org/projects/fritzing-creator-kit-01-blink](http://fritzing.org/projects/fritzing-creator-kit-01-blink)
Now when I right-click the file, I get :
Open with Ftritzing, which is perfect. Thank you very much!
So my original problem has been solved, but my CD drive (and memory leak) problems(s) remain(s) unsolved.
Should I change the status of this thread to solved, and then create a new thread concerning my CD drive (and memory leak) problem(s)?

---

### Post by mc4man on 2015-07-04
> **boxcorner said:**
> 
So my original problem has been solved, but my CD drive (and memory leak) problems(s) remain(s) unsolved.
Should I change the status of this thread to solved, and then create a new thread concerning my CD drive (and memory leak) problem(s)?
I would start a new thread specific to the cd drive issue

---

### Post by boxcorner on 2015-07-06
All right, wilco

---

