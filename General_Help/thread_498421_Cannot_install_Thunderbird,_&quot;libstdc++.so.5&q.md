---
title: "Cannot install Thunderbird, &quot;libstdc++.so.5&quot; error."
date: 2007-07-11
forum: General Help
---

### Post by snakyjake on 2007-07-11
I'm trying to install Thunderbird v2.0.0.4 from source.  When doing so, I receive an error message about libstdc++.so.5 as shown below.

How do I install the library?  I've tried looking for it within Adept and cannot find it (and I updated my repository listings).  I already have installed "libstdc++6" and "libstdc++6-4.1-dev".  And I'm running Feisty 7.04.


```
root@jake-desktop:/home/jake/Desktop/thunderbird-2.0.0.4/thunderbird# ./thunderbird

./thunderbird-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
```

Thank you,

---

### Post by linuxwizard on 2007-07-11
Try installing with this. Works great have used many times for Firefox and Thunderbird.

[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla#Update_Official_Mozilla_Build_of_Thunderbird](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla#Update_Official_Mozilla_Build_of_Thunderbird)

---

### Post by davidjmayo on 2007-07-11
> Try installing with this. Works great have used many times for Firefox and Thunderbird.

[http://pykeylogger.sourceforge.net/w..._Thund](http://pykeylogger.sourceforge.net/w..._Thund) erbird

I'll second that

---

### Post by nanotube on 2007-07-12
> **snakyjake said:**
> I'm trying to install Thunderbird v2.0.0.4 from source.  When doing so, I receive an error message about libstdc++.so.5 as shown below.

How do I install the library?  I've tried looking for it within Adept and cannot find it (and I updated my repository listings).  I already have installed "libstdc++6" and "libstdc++6-4.1-dev".  And I'm running Feisty 7.04.


```
root@jake-desktop:/home/jake/Desktop/thunderbird-2.0.0.4/thunderbird# ./thunderbird

./thunderbird-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
```

Thank you,

the package you are looking for is "libstdc++5"
but as the previous poster suggested, you'd have had an easier time if you use the ubuntuzilla script to install - it will take care of all dependencies for you. 
(and, as the author of said script, i am somewhat partial to it, i'll admit. :) ).

---

### Post by snakyjake on 2007-07-12
Fantastic, got Thunderbird to work with the Ubuntuzilla script.  Thanks 'linuxwizard'!

I had to do it differently than the wiki.

1.  I changed to the directory to where I downloaded the script.
2.  Then ran the following command.  I had to use the version numbers.

```
python ubuntuzilla_4.1.1.py -a install -p thunderbird
```

I have to vent a little about Linux or Mozilla's website (not the Ubuntuzilla script, it worked wonderfully)...why is installing something so popular, so complicated?  Why isn't it like a Windows install?  I had my Windows version done and running in seconds.  Can someone post a link to such subject and for any news about improvements in this area  (I'm sure I'm not the first one to be disappointed)?

Thanks.

---

### Post by nanotube on 2007-07-12
> **snakyjake said:**
> Fantastic, got Thunderbird to work with the Ubuntuzilla script.  Thanks 'linuxwizard'!

I had to do it differently than the wiki.

1.  I changed to the directory to where I downloaded the script.
2.  Then ran the following command.  I had to use the version numbers.

```
python ubuntuzilla_4.1.1.py -a install -p thunderbird
```

I have to vent a little about Linux or Mozilla's website (not the Ubuntuzilla script, it worked wonderfully)...why is installing something so popular, so complicated?  Why isn't it like a Windows install?  I had my Windows version done and running in seconds.  Can someone post a link to such subject and for any news about improvements in this area  (I'm sure I'm not the first one to be disappointed)?

Thanks.

glad to see that it worked. :) i have a question to you about the ubuntuzilla wiki page - was it not clear when it said "save it as 'ubuntuzilla.py'" ? to me, that says, name the file 'ubuntuzilla.py', which means remove the version number from the filename. that would enable you to run the commands as is - and lets me not worry about updating the wiki every time i push out a new version.

do you think that "save it as" part should be clearer, or reworded somehow? your suggestions would be welcome. :)

as to why it's more difficult on linux than windows - the equivalent of the windows .exe installer is the ubuntu .deb. since mozilla doesn't release ubuntu debs, you end up having to play with tar.gz if you want to go out-of-repository. that's why people would generally encourage you to stick to the official repositories for the software - which is not always as optimal as we'd like, unfortunately.

---

### Post by davidjmayo on 2007-07-12
> **nanotube said:**
> glad to see that it worked. :) i have a question to you about the ubuntuzilla wiki page - was it not clear when it said "save it as 'ubuntuzilla.py'" ? to me, that says, name the file 'ubuntuzilla.py', which means remove the version number from the filename. that would enable you to run the commands as is - and lets me not worry about updating the wiki every time i push out a new version.

do you think that "save it as" part should be clearer, or reworded somehow? your suggestions would be welcome. :)
.

FWIW I didn't read the wiki clearly either and did the same with the filename. I Downloaded it as ubuntuzilla.py.x.y.z Only after, when it didn't work did I discover my error and fix it. What the wiki says is correct but I think people tend to speed read when they do something they "think" they know about, like saving a file.
Maybe to make it clearer it should say save the download file ubuntuzilla.py.x.z.y. as ubuntuzilla.py

I was impressed with it though. Couldn't find an easier way to upgrade. That's why I seconded linuxwizard.
Thanks nanotube--good work

---

### Post by snakyjake on 2007-07-12
> **nanotube said:**
> i have a question to you about the ubuntuzilla wiki page - was it not clear when it said "save it as 'ubuntuzilla.py'" ? to me, that says, name the file 'ubuntuzilla.py', which means remove the version number from the filename. that would enable you to run the commands as is - and lets me not worry about updating the wiki every time i push out a new version.

do you think that "save it as" part should be clearer, or reworded somehow? your suggestions would be welcome. :)


My bad.  I should have read the directions completely.  I'm the type of user that just wants to click n' run (not to be confused with Linspire's CNR).  So I ended up skim reading too much.

What might be another option is having the file name SourceForge forgo the version number.  The version is already contained in the Release column.  And when the file is downloaded according to the directions, it forgoes the version number anyways.

A big thanks to you for doing the script.

---

### Post by snakyjake on 2007-07-12
> **davidjmayo said:**
> 
Maybe to make it clearer it should say save the download file ubuntuzilla.py.x.z.y. as ubuntuzilla.py


Here's the exact directions in the Wiki:
"Download the script (follow this link to the file release servers), and save the latest ubuntuzilla_X.X.X.py as ubuntuzilla.py to your home directory. "

If many people do what we did by skim reading, perhaps nice huge, red, and bold text would help us :-)

Or maybe a script can be written to do all these other steps?

But...geez!  The script is wonderful, and so is the wiki.  I'm happy that something like it exists :-)

---

### Post by davidjmayo on 2007-07-12
Sorry I wasn't clear. I used .ubuntuzilla.py.x.y.z as an example.

I should have written ubuntuzilla.py.x.x.x

But it seems snakyjake and I both did the same thing, speed/skim reading. 
I like snakyjakes suggestion about [SIZE="6"][COLOR="Red"]big red letters[/COLOR][/SIZE]

---

### Post by nanotube on 2007-07-12
> **snakyjake said:**
> My bad.  I should have read the directions completely.  I'm the type of user that just wants to click n' run (not to be confused with Linspire's CNR).  So I ended up skim reading too much.

What might be another option is having the file name SourceForge forgo the version number.  The version is already contained in the Release column.  And when the file is downloaded according to the directions, it forgoes the version number anyways.

A big thanks to you for doing the script.

thanks to all for your comments. :)
about having the filename on sourceforge without the version - well, there's the rub - it is not allowed to have two files with the same name on the file release system, so if ubuntuzilla 4.0.0 is named "ubuntuzilla.py", then no other "ubuntuzilla.py" can exist. that's why the files have version numbers in the first place - if they didn't have to, that'd make everyone's lives just a little easier. ;)

i don't think i will go for something as dramatic as [COLOR="Red"][SIZE="5"]big red letters[/SIZE][/COLOR] :), but thanks to your suggestions, i will definitely make that bit stand out somehow... maybe **bold.** :)

---

