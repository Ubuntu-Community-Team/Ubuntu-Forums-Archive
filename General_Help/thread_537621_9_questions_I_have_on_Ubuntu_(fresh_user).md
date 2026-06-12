---
title: "9 questions I have on Ubuntu (fresh user)"
date: 2007-08-29
forum: General Help
---

### Post by ExtraEye on 2007-08-29
1)Make windows in beryl maximize when title bar is double clicked (instead of folding the window).

2)How to make a software the default opener for certain files (aka: make smplayer always open media files).

3)How to assign global hotkeys for certain tasks. Like being able to lower the volume of a player while surfing the net without shifting the focus of the window.

4)Is it possible to make two monitors be different parts of one tube(in beryl). Say there are 4 desktops to a tube, one monitor will show desktop1, and the second monitor will show desktop2. So it will be possible for both monitors to show the same desktop or different desktops. This behaviour will be different than the normal two separate tubes behaviour in beryl.  

5)Is it possible to play a game through wine and still have the display on the other monitor? right now when I start a game through wine I lose view on the other monitor (becomes a blue screen while I play).

6)Are there ways to speed up ubuntu's response? maybe the startup? Right now it isn't really slow but I always want to know if there are ways to improve performance. The startup though, is relatively slow.

7)I use dual monitors and my second monitor is a HDTV LCD screen. Being a TV screen, it naturally loses the edges of the picture of the screen. Is there a way to add black borders to the picture that is sent to the TV so that it will still show the edges of the screen? (Or maybe send a lower resolution picture to the screen). I use that method with SMPlayer but It would be nice to have it for everything and not just video. So in short, this is the opposite of cropping. 

8 )One of the few things I liked in windows vista was the search feature. In this area I found Ubuntu to be lacking. First of all the ability to search by date and other specific criteria was not available. Secondly the search isn't as imidiate and easy as it is in Vista. I know there is software that does the indexing search for Ubuntu like Google's and beagle but it wasn't as integrated into the system and still didn't have the option to search by date. Is there a way to add such functionality to Ubuntu?

9)There are still some things I wish to do in windows. How do I make it the first choice in the operating system choice menu (I think it's called Grub right?).

---

### Post by jusmurph on 2007-08-29
> 1)Make windows in beryl maximize when title bar is double clicked (instead of folding the window).

**No idea but if you look in the settings its fairly customisable**

2)How to make a software the default opener for certain files (aka: make smplayer always open media files).
[B]
Right click the file and open the properties and follow your nose. It should be obvious (not in frount of ubuntu atm)
[/B]
3)How to assign global hotkeys for certain tasks. Like being able to lower the volume of a player while surfing the net without shifting the focus of the window.

**System > Preferences > Keyboard**

4)Is it possible to make two monitors be different parts of one tube(in beryl). Say there are 4 desktops to a tube, one monitor will show desktop1, and the second monitor will show desktop2. So it will be possible for both monitors to show the same desktop or different desktops. This behaviour will be different than the normal two separate tubes behaviour in beryl.  

**I have never heard of it...**

6)Are there ways to speed up ubuntu's response? maybe the startup? Right now it isn't really slow but I always want to know if there are ways to improve performance. The startup though, is relatively slow.

**Google and Blogs...**

8 )One of the few things I liked in windows vista was the search feature. In this area I found Ubuntu to be lacking. First of all the ability to search by date and other specific criteria was not available. Secondly the search isn't as imidiate and easy as it is in Vista. I know there is software that does the indexing search for Ubuntu like Google's and beagle but it wasn't as integrated into the system and still didn't have the option to search by date. Is there a way to add such functionality to Ubuntu?

[B]sudo apt-get install beagle
[/B]
9)There are still some things I wish to do in windows. How do I make it the first choice in the operating system choice menu (I think it's called Grub right?).
[B]
It is called GRUB, but i do not know how to change the preference.[/B]

Answered the best i could...

---

### Post by forestpixie on 2007-08-29
This is the beginning of my menu list

> # menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
[COLOR="Red"]default		0[/COLOR]


What you need to do is to change the 0 to correspond to your windows entry - it starts counting from 0 :)

[This]("https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS") should help you

Edit - if you get lost/confused etc post your menu.lst here - someone will surely help you with it.

---

### Post by ExtraEye on 2007-09-28
Thanks for the comments.
This is a very late response... 
jusmurph - about chaging the default player for movies - I tried doing that but i can't change the default for some reason.
I go to Properties>open with and there Ihave "Movie player"(marked) and below it SMPlayer. i try double clicking or draging them but nothing does anything.

about the global keybord shortcuts - I still don't understand how i can make global shortkeys for program specific tasks. I know there's a keybord shortcuts GUI but it only has ready actions you can asign keys to, you can't add new ones.

beagle doesn't seem to amount to what vista has... besides, I wanna search by date and etc. I there really no way to do it without installing anything?

forestpixie  - thank you. I will try that.

---

### Post by lintoon on 2007-09-28
For number 2.

Right click on your media file and select "Open With" and choose "Other" at the bottom of the list.  Select your default application and put a tick in the box for "Remember application association for this type of file"

---

### Post by lintoon on 2007-09-28
My last post was for KDE.  I haven't checked out gnome yet but I imagine it should be more or less the same instructions.

---

### Post by aJayRoo on 2007-09-28
For number one:
You need to open Emerald Theme Manager for this (not Beryl Settings Manager as you might think), Then click on the Emerald Settings tab, you should then see a drop down box allowing you to select what happens when a title bar is double clicked.

Just in case you aren't sure, Emerald Theme Manager is accessed by right clicking on the beryl-manager icon in the notification area (system tray equivalent). This of course assumes you have beryl manager installed and running, which I'm sure you will!

---

### Post by ExtraEye on 2007-09-29
thx for the replies. 
lintoon  - that doesn't exist in gnome. 
[IMG]http://img264.imageshack.us/img264/1909/screenshotopenwithft3.png[/IMG]
From what I know what I need to do is right click, Properties>Open With and then select Smplayer. The problem is i can't select it. I think this happens beacuse I don't have the permission. Is there a way to make Smplayer the default opener of video/audio files through command line? (so that i can use sudo).

aJayRoo  - thank you very much!

---

### Post by meindian523 on 2007-09-29
On Gnome,you right click a file of the type you want to be opened with SMplayer,go to Open With and click the Radio button for the SMPlayer,click close and you're done.

If SMplayer doesn't appear in the list,click add and select SMPlayer in the new list,then go back to the properties dialog box and click the radio button for SMPLayer,close and you're done.Now hopefully,your problem is solved??

---

### Post by ExtraEye on 2007-09-29
[IMG]http://img385.imageshack.us/img385/3348/screenshotlightspeedrusao9.png[/IMG]
I don't see any radio button...

---

### Post by meindian523 on 2007-09-29
Referring your screenshot,you would see that the RADIO Button next to Movie Player has a dot inside it while the one for SMPlayer doesn't.Now what you do is click on the button next to SMPlayer so that it contains the dot and the one for Movie Player doesn't and click close.........OK?

---

### Post by ExtraEye on 2007-09-29
I already tried that. when i click on the one next to Smplayer it doesn't do anything. Like I said before I think it has something to do with permissions.

---

### Post by meindian523 on 2007-09-30
You mean the radio button doesn't contain the dot even after you click it?

If it's about permissions,check whether you are the owner of that file by right clicking and going to the permissions tab.If yes,give yourself all permissions for that file.....If no,in terminal

```
sudo chmod go+rw <name_of_file>
```

The above is valid if you are part of the admin group on your machine [OR] you know the root password......

---

### Post by ExtraEye on 2007-09-30
On the NTFS drive it said in permissions "root".
I moved a file from there to ubuntu's desktop and now it says "yarden" (which is my username).
I still can't change the radio button for either of them.
I tried your command and it didn't change anything :(

---

### Post by meindian523 on 2007-09-30
please ignore this post..

---

### Post by meindian523 on 2007-09-30
You are not supposed to get any output from the command if that's what you mean.BTW,that was supposed to be used IF you are not the owner.Since you are(the owner of the file that is),give yourself full permissions by the method described above or in terminal
```

chmod u+rwx <file_name>
```

Now retry selecting SMPlayer from the dialog box so that it's button contains a dot....if this doesn't work,I don't know what can.

Also,apologies for misunderestimating you.:)

---

### Post by MarkieB on 2007-10-01
you may feel that starting from 'sudo nautilus' is more straightforward/less risky than mucking around with chmod

[after needing to reinstall ubuntu when I chmod'ed my entire /home directory to back it up!]

---

