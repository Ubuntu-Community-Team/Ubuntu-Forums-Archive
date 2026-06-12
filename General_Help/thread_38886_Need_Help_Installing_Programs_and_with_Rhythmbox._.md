---
title: "Need Help Installing Programs and with Rhythmbox.  Please Help!!"
date: 2005-06-02
forum: General Help
---

### Post by linuxn00b86 on 2005-06-02
I have to start off by saying that after a long run with windows, i decided to switch to linux.  that being said, this is my second day and needless to say, im extremely overwehelmed.  I honestly dont really understand how to install software, but im trying to install a media player and attempted to install XMMS, from other people's reccomedations.  Yet, during the install when i typed ./configure in the terminal i got the error message

*** The glib-config script installed by GLIB could not be found
*** If GLIB was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GLIB_CONFIG environment variable to the
*** full path to glib-config.
configure: error: *** GLIB >= 1.2.2 not installed - please install first ***

I searched the internet for glib 1.2.2 and could not find it anywhere, if thats even the problem.  this all stems from me not being able to play music from my ipod or even add files into rhythmbox.  i would prefer to use that but honestly dont understand it.

please please help, i am completely lost and really want to use linux

thanks! ](*,)

---

### Post by duff on 2005-06-02
If it's only your first or second day with Linux you shouldn't start off by trying to track down dependancies to build a program, that's what package managers are for.  To install xmms, run Synaptic, search for xmms and install it.

But what's your problem with Rhytmbox?  Just go to the File menu and select Import Folder and then select the folder containing all your music.  It'll bring it all in.  And since you're coming from windows, your music is probably all MP3..so before you import it into Rhythmbox go into Synaptic and install 'gstreamer0.8-mad' to be able to decode MP3s.

And check out this site: [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)

---

### Post by linuxn00b86 on 2005-06-02
im sorry i dont know what im doing wrong but when i search synaptic package manager..they are not there..and i dont know whats wrong with the rhythmbox but it says it doesnt have the required files needed to play my mp3s. also, i have mp4 files too..please help

thanks


ps what does synaptic do

---

### Post by couchwarrior on 2005-06-02
just been through all this myself ,
[http://ubuntuforums.org/showthread.php?t=38699](http://ubuntuforums.org/showthread.php?t=38699)
now got rhythm box and xmms working

---

### Post by gonenowhere on 2005-06-23
[QUOTE=linuxn00b86]im sorry i dont know what im doing wrong but when i search synaptic package manager..they are not there..and i dont know whats wrong with the rhythmbox but it says it doesnt have the required files needed to play my mp3s. also, i have mp4 files too..please help

thanks


ps what does synaptic do[/QUOTE]


go to ubuntuguide.org you find out how to install the codecs you need to play mp3's. and for your synaptic question its a package manager you can install and uninstall programs using it. look at the ubuntuguide it helps allot and will answer allot of your questions. always look there first if they dont have your answer come here.

---

