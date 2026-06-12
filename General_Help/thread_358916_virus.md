---
title: "virus ?"
date: 2007-02-11
forum: General Help
---

### Post by warri0r on 2007-02-11
seriously i lost everything in my home folder. i had some 5gb of data but now it has only the desktop folder.

wat cud be the problem and i m a damn newbie to this linux so plz help me.

this is wat i did before i lost my data.

" i upgraded my firefox version from 2.0 to 2.0.0.1 by manually downloading the file from firefox website and upgraded using the guide provided in the link below

[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

i followed the instructions given under **"Manual Install"**

everything went right and firefox is working properly, so i decided to add the launcher to my desktop.

went to applications-->internet--> firefox and made a right click and selected **"add this launcher to desktop"**

THATS IT :(

my desktop wallpaper changed to a brown colour. nothing in my home folder.here is a screenshot. plz kindly help me to get the data back or atleast the reason.plz :(
[IMG]http://img262.imageshack.us/img262/8780/screenshotqx2.png[/IMG]

---

### Post by koenn on 2007-02-11
show us the output of this command :

```
ls -al /home
```

---

### Post by warri0r on 2007-02-11
Thanks for replying me sir,

i got this

total 60
drwxr-xr-x  4 root    root     4096 2007-02-11 21:44 .
drwxr-xr-x 21 root    root     4096 2007-02-11 21:46 ..
drwxr-xr-x  2 root    root    49152 2007-02-11 21:36 lost+found
drwxr-xr-x 27 warri0r warri0r  4096 2007-02-11 23:57 warri0r

kindly help me sir

---

### Post by koenn on 2007-02-11
> my desktop wallpaper changed to a brown colour
exactly when did that happen ? When did you notice it ?
during the download of firefox ? during the installation ? while you were creating a launcher ?

---

### Post by warri0r on 2007-02-11
sorry sir i forgot one thing to tell.

after installing the the firefox 2.0.0.1, i double clicked the laucher created on desktop for firefox 2.0. the icon simply disappeared.

so i went to application--->internet--->firefox and made a right click and selected tat add launcher to desktop. i waited for some seconds.the desktop wallpapers changed and the laucher appeared in my desktop.

i went to the home folder and found the desktop folder alone :(

---

### Post by Ramses de Norre on 2007-02-11
Can you remember the exact name of a file that was in your home directory but isn't anymore now? If so, can you execute these commands and post the output:
```
sudo updatedb   ##shouldn't output anything, updates the locate database
locate *name*
find / -name *name*
```
Where *name* indicates the name of the file.

---

### Post by warri0r on 2007-02-11
i executed this command sir as i had a folder named "Music"

sudo updatedb
locate Music


got the output (long output but short sample)

```
/home/warri0r/.mozilla/firefox/vlwcw6ch.default/Music/Tamil/Mudhalvan
/home/warri0r/.mozilla/firefox/vlwcw6ch.default/Music/Tamil/Mudhalvan/MUDHAL~1.MP3
/home/warri0r/.mozilla/firefox/vlwcw6ch.default/Music/Tamil/Mudhalvan/MUDHUL~1.MP3
/home/warri0r/.mozilla/firefox/vlwcw6ch.default/Music/Tamil/Mudhalvan/MUDHUL~2.MP3
/home/warri0r/.mozilla/firefox/vlwcw6ch.default/Music/Tamil/Mugavari
/home/warri0r/.mozilla/firefox/vlwcw6ch.default/Music/Tamil/Mugavari/ANDAY ZUITTAN.MP3
/home/warri0r/.mozilla/firefox/vlwcw6ch.default/Music/Tamil/Mugavari/EN KATHAL(G).MP3
/home/warri0r/.mozilla/firefox/vlwcw6ch.default/Music/Tamil/Mugavari/EN KATHIL.MP3
/home/warri0r/.mozilla/firefox/vlwcw6ch.default/Music/Tamil/Mugavari/O NEVJEA.MP3
/home/warri0r/.mozilla/firefox/vlwcw6ch.default/Music/Tamil/Mugavari/O VEDINSAIUS.MP3
```

i had some five folder and this is one folder named "music" where i had a 3000 mp3 files.

the output displays the exact files tat i had in the lost "music" folder.

hope i get them back. help me plz sir :(

---

### Post by warri0r on 2007-02-11
sorry for double post :(

output of another folder tat i lost named "asimo vids"

warri0r@warri0r-desktop:~$ locate Asimo
/home/warri0r/.mozilla/firefox/vlwcw6ch.default/Tempfiles/Asimo vids
/home/warri0r/.mozilla/firefox/vlwcw6ch.default/Tempfiles/Asimo vids/01_Walking.wmv
/home/warri0r/.mozilla/firefox/vlwcw6ch.default/Tempfiles/Asimo vids/03_Inside_ASIMO.wmv
/home/warri0r/.mozilla/firefox/vlwcw6ch.default/Tempfiles/Asimo vids/capabilities_300.wmv
/home/warri0r/.mozilla/firefox/vlwcw6ch.default/Tempfiles/Asimo vids/intelligence_tech_300.wmv
/home/warri0r/.mozilla/firefox/vlwcw6ch.default/Tempfiles/Asimo vids/new_mobility_300.wmv
/home/warri0r/.mozilla/firefox/vlwcw6ch.default/Tempfiles/Asimo vids/Stairs.wmv

plz help me sir :(

---

### Post by Ramses de Norre on 2007-02-11
I get the impression that somehow your home directory got moved to /home/warri0r/.mozilla/firefox/vlwcw6ch.default/Tempfiles/
If so: check whether the lost files and directories are the only ones in that location and if so execute this: ```
sudo mv /home/warri0r/.mozilla/firefox/vlwcw6ch.default/Tempfiles/* /home/warri0r/ && sudo chown `whoami`:`whoami` /home/warri0r/* && chmod o+rwx /home/warri0r/*
```

If there are other files in that location too you'll have to manually move the files you want back to your home directory..

---

### Post by akshaysrinivasan on 2007-02-11
Well it is quite difficult to recover files from the standard ext3 filesystem.You may try foremost , magicrescue and testdisk to get back some of your data.

---

### Post by Ramses de Norre on 2007-02-11
He never deleted them.. It seems like they're just moved to someplace else.

---

### Post by warri0r on 2007-02-11
i manually moved all those folders back. its all safe :)

THANKS A LOT for all ppl helping me. 

but i wish to learn something, 

y those files were moved to my firefox profiles directory. 

is tat due to some commands i used to install the new firefox?

i followed the guide in the link below and followed the commands under "manual install"

[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

plz if anyone knew the reason kindly tell me

thanks again :)


~EDIT~

i got the reason. in the guide they asked to execute this commands

cd ~/Desktop/ffsettings
 mv * ~/.mozilla/firefox/*.default

so when i executed the first command i got a reply "no file or directory"

so when executed the second command consecutively (damn wat a brain i m having) it moved all those folders into the profiles directory :P

---

### Post by koenn on 2007-02-11
> those files were moved to my firefox profiles directory.
is tat due to some commands i used to install the new firefox?
possibly - but probably only if you made a mistake.

eg this one
> 
Restore your old data:

 cd ~/Desktop/ffsettings
 mv * ~/.mozilla/firefox/*.default

if you forgot the cd command, or it fails for some reason, and you happen to be in your home directory, the mv command would move the contents of the home dir to the profile folder.

EdIt : i see you found it too.

---

### Post by warri0r on 2007-02-11
yeah its me blindly issuing the commands. hope this is a start, ll learn a lot more.

once again thanks for all ppl spending your valuable time :D

---

### Post by koenn on 2007-02-11
By going back to the instructions and finding out where things went wrong,  at least you've shown that you are willing and able to learn from your mistakes.
You'll get there in time

have fun

kn

---

