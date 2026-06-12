---
title: "KMplayer?"
date: 2005-10-29
forum: General Help
---

### Post by Gijith on 2005-10-29
Hi everybody. 

I'm brand new. I was introduced to linux about 16 hours ago. So please excuse any stupidity. I got ubuntu, then installed kubuntu (kde is beautiful). I got Mplayer all set up, including the plugins. I really want to setup up KMplayer: [http://kmplayer.kde.org/](http://kmplayer.kde.org/) so I can incorporate it into konquerer.  In typical newbie fashion, I tried to install the debian packages, before realizing they wouldn't work. Then I tried the suggested ubuntu packages: [http://www.oheric.com/breezy-debs/](http://www.oheric.com/breezy-debs/) , but found that 3 of the files listed there are missing... or something...

Does anybody know of any other sources for this? I can't find it in any repository. If anyone can help, please post. Thanks a lot.

-Gijith

---

### Post by Mr Wonka on 2005-10-30
I've just encountered this. It is a complete pain. However I got around it by building from source available from the kmplayer site.

Since your new to this it will be a bit of a trial by fire but I'm sure you'll get there. Don't forget to search search and search for any help you need. By the end of it you'll be well on your way to losing newbie status. 

I'll give you your first hint for free. To compile software with ubuntu/kubuntu you'll need a package called 'build-essential'. You'll need a lot of other stuff but searching on this forum alone will give you all the hints you need.

Hope this help

Adam

---

### Post by mrmarco on 2005-10-30
Some more hints in order to have a chance to make these packages :
[LIST]
[*]use the debian/rules script (with "build" keyword, then "binary" (must be root), "clean" can be useful also)
[*]modify the debian/control file in order to have the package kmplayer-lib depend on kdelibs4c2 and libxine1c2 (and not on the "non-c2" libs)
[*]even if everything went good, one has still to install kmplayer* packages with a dpkg -i --force-overwrite because of various files shared with a (kaffeine?) package
[/LIST]

Then you'll be able to see some videos embedded in web pages in konqueror!

Hope It Helps,


Mr Marco

---

### Post by skyboy on 2005-10-30
I use it but I compiled it from source. Give it a try, not so difficult. just untar the source, go the the diretory, run ./configure and cut and paste if any trouble.
then sudo checkinstall to create your own deb file
have fun.
Btw, it is a create app

---

### Post by Gijith on 2005-10-30
Thanks a lot for responding guys.

Here's where I'm at (again, please bear with me):
I got build essential... more on that in a sec.

I went ahead and got downloaded the tar and used the procedure I found here: [http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html) . First off, I'm not sure if that was the right procedure to follow or not (I've really never felt more ignorant than I have in the past day)  I didn't use the debian/rules script (because, unfortunately, I did all this before mrmarco made his post)... It went all right. But I wasn't sure what I needed to cut and paste... After I had gone through the procedure, I checked the debian/control file. It seems to have dependency for both (if that's possible???) c2 and non c2. Here's the text:

Package: kmplayer-lib
Architecture: any
Section: sound
Depends: kdelibs4 (>= 4:3.1.0-1) | kdelibs4c2 (>= 4:3.4.0-1), libxine1 | libxine1c2, libgstreamer0.8-0, libgstreamer-plugins0.8-0
Description: KMPlayer shared library

Should I get rid of those non c2 bits?

So that's where I'm at now. I have the stand alone player. It works (it's great actually). But it also worked when I just installed the debian packages yesterday. The plugins still don't work. On the internet, mpegs cause mplayer to open and run separately(I guess I can't really complain there), and quicktime files cause some kind of xine error that I never get a chance to read cause it just crashes the program... So, yeah, I have a feeling I did this wrong... Throughout all this, I never heard from, or did anything with, build-essential (is this an obvious sign I did something wrong, or was I not supposed to use it directly?)

If anyone can maybe point me in the right direction or tell me what to search for (did I at least untar the source correctly?), I'd be very thankful. I'm in a bit over my head here. I probably need to get more comfortable and try this some other time.

---

### Post by skyboy on 2005-10-30
ok, 2 things :
 Have you checked in Konqueror if you scan for new plugins ?? 
then if you want to compile it from source, follow those steps :
- download the source from the official we site 
- untar the source
- open a konsole 
- "cd" to directory where you untared the source.
- "type "./configure" in the konsole 
- check any mistake and output from this step until it tells you "you can start by typing "make" 
- if no mistake, type "make" or "sudo checkinstall" (make sure you have installed checkinstall first by apt-get install checkinstall) 
- if you find any error message from the "./configure" step, copypaste here 
- if everything is find after "make", type "sudo make install" and you are done

---

### Post by skyboy on 2005-10-30
By the way, debian package are not compatible with ubuntu. So you should not install them even thought sometimes it works. Prefer building yourself the package. Once you did it few times, you'll become a real expert and do it in few sec. Trust me, it is not as hard as it sounds. Remember the first time you learnt how to write :D

---

### Post by Gijith on 2005-10-30
skyboy, thanks again for responding. 
You're all quickly disproving some of the things I'd heard about linux users.

yeah, the site I was using went through those same steps. Everything went fine from configure to install. So hopefully, I'm cool there...

I guess the problem must be with Konquerer. It's set to scan for plugins (mostly through the Mozilla folders). But upon looking at the plugins tab, I'm finding that the only plugins it actually has listed are the Netscape ones for Macromedia, even after scanning. No Mplayer, nothing... Is this an issue with permissions? Does your Konquerer have KMplayer plugins listed under that tab? 

And yes, thanks for the advise on not just installing debian packages. 

Thanks once again.
-Gijith

---

### Post by Gijith on 2005-10-30
never mind. It took me a sec to realize I was looking in the wrong place for plugins!

I got it all sorted out. It's working. Thank you all very much. you've been a huge help.

 :smile:

---

### Post by skyboy on 2005-10-30
Great news :)

---

### Post by mrmarco on 2005-10-30
[QUOTE=Gijith]
After I had gone through the procedure, I checked the debian/control file. It seems to have dependency for both (if that's possible???) c2 and non c2. Here's the text:

Package: kmplayer-lib
Architecture: any
Section: sound
Depends: kdelibs4 (>= 4:3.1.0-1) | kdelibs4c2 (>= 4:3.4.0-1), libxine1 | libxine1c2, libgstreamer0.8-0, libgstreamer-plugins0.8-0
Description: KMPlayer shared library
[/QUOTE]

The contol file must be newer than the one I have, it should be now a no-brainer to do a "debian/rules build && sudo debian/rules binary" to get clean ubuntu deb packages ( I must say that these debs are thought to be cleaner than the checkinstall ones)

---

### Post by skyboy on 2005-10-31
> ( I must say that these debs are thought to be cleaner than the checkinstall ones)
You are right if you intended to distribute your deb file. Otherwise, for your own collection, checkinstall deb files are very safe and easier to create.

---

