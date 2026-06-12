---
title: "Does anyone know how MP3 audio streams can be played back via Digitally Imported?."
date: 2005-06-26
forum: General Help
---

### Post by itxweather on 2005-06-26
Hi,

Does anyone know how MP3 audio streams can be played back via Digitally Imported ([http://www.di.fm/](http://www.di.fm/)) within Ubuntu Linux?. Rhythmbox opens by default but the following error message appears:

There is no element present to handle the stream's mime type audio/mpeg.

Thank you in advance for any help.
Best Regards.

---

### Post by jasmuz on 2005-06-26
[QUOTE=itxweather]Hi,

Does anyone know how MP3 audio streams can be played back via Digitally Imported ([http://www.di.fm/](http://www.di.fm/)) within Ubuntu Linux?. Rhythmbox opens by default but the following error message appears:

There is no element present to handle the stream's mime type audio/mpeg.

Thank you in advance for any help.
Best Regards.[/QUOTE]
 I recomend you download from the repositories a program called Streamtuner, that will allow you to stream it into Xmms :)
 have fun listening to music.

---

### Post by itxweather on 2005-06-26
[QUOTE=jasmuz]I recomend you download from the repositories a program called Streamtuner, that will allow you to stream it into Xmms :)
 have fun listening to music.[/QUOTE]

Hi Jasmuz,

Thank you for your reply. Please excuse my ignorance but where exactly can the repositories be found or do I need to do a quick google search?. Guess I really do need to read through the docs on ubuntuguide.org.

Like your avatar by the way.

Impressed with Ubuntu Linux so far just a few things I need to learn more about, what to do with Tarballs, RPMs, tar.gz (guess these are Tarballs?) etc..

Thank you.
Best Regards.

---

### Post by art on 2005-06-26
Go System->Administration-> Syanptic Package Manager and search for Streamtuner, download and install it.Also would suggest to install Streamripper, which will let you record streams. The repositories are listed in the /etc/apt/sources.list file. You can add or remove repos from this list. A very nice guide is located here [http://ubuntuguide.org/](http://ubuntuguide.org/).  Tarballs are juct archives, packed files, to untar do "tar xf filename.tar" , when tar.gz do "tar zxf filename.tar.gz" , also possible are .bz or .tar.bz, then first do "bunzip2 filename.bz(or tar.bz)" and then the previous one. RPMs are precompiled packages coming from RedHat linux, similar to .deb packages (easy to install). When installing from source you need to compile the source first.  
HTH

---

### Post by itxweather on 2005-06-26
[QUOTE=art]Go System->Administration-> Syanptic Package Manager and search for Streamtuner, download and install it.Also would suggest to install Streamripper, which will let you record streams. The repositories are listed in the /etc/apt/sources.list file. You can add or remove repos from this list. A very nice guide is located here [http://ubuntuguide.org/](http://ubuntuguide.org/).  Tarballs are juct archives, packed files, to untar do "tar xf filename.tar" , when tar.gz do "tar zxf filename.tar.gz" , also possible are .bz or .tar.bz, then first do "bunzip2 filename.bz(or tar.bz)" and then the previous one. RPMs are precompiled packages coming from RedHat linux, similar to .deb packages (easy to install). When installing from source you need to compile the source first.  
HTH[/QUOTE]

Hi Art,

Thank you for your reply. Am downloading Streamripper as we speak. Have read through quite a lot of the guide at ubuntuguide.org and have found the guide to be an invaluable resource for getting things to work under Ubuntu Linux. Whoever wrote that guide should be very highly commended imho. Have tried other Linux distro's previously and have never known a guide such as that one which has kind of put me off trying out Linux distros. Am glad that i've found Ubuntu and this excellent forum, a big thank you to all that have offered help to date. Am really impressed with Ubuntu Linux.

One more question i'm afraid. Now that i've downloaded Streamripper how can I get streams from let's say di.fm to work via a Netgear MP101 DMP?.

Thank you.
Best Regards.

---

### Post by art on 2005-06-26
Yeah, that one I have no clue... Even in Windows:) Never had one.

---

### Post by fizz on 2006-03-04
I have a premium account with di, is there a way i can listen to that? You have to authenticate with thier server unfortunatly for it to work, and i havent had any luck with that yet, however streamtuner, and xmms did the trick for regular listening :)

---

