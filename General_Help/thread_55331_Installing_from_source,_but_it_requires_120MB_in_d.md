---
title: "Installing from source, but it requires 120MB in dependencies."
date: 2005-08-08
forum: General Help
---

### Post by sk545 on 2005-08-08
So, [Kaffeine 0.7](http://kaffeine.sourceforge.net/) was released and i wanted to try it out right away.  After downloading the source, i did the configure step which exited with:

"checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!"

I was like, ok, so it just need the kde dev package, so i go on and do 'apt-get install kde-devel' and now it wants to download 120MB in packages so satisfy all the dependencies.  My question is:  Is there any other way to do this without downloading so much of KDE?  Yes, i could remove them later on, but is there any other way at all?

Please don't answer with "why don't you put a request in backports" or "hey, thats what you get for using a binary distro, use gentoo instead."  I just wanna know if its possible to do this without downloading 120MB of files.

Thanks.

---

### Post by Lord Illidan on 2005-08-08
What kind of dependencies does it have? Can u give them to us?

kaffeine seems to be a pretty integral part of KDE, if you like KDE apps, better get kubuntu...

---

### Post by SGC on 2005-08-08
kde-deval is used for developing kde-based packages, to compile kaffeine make sure that you have only the following packages (6 MB download/26 MB after install):

libxine-dev	             
libqt3-headers	           
libqt3-mt-dev	            
libqte-mt3		      
libqte-mt3-dev	           
qt3-dev-tool	             
kdelibs4-dev	            

I compiled Kaffeine 0.7 when it released and every thing went well.

Are you using Ubuntu (Gnome)?, if so you need more than the above. I think apt-get will download them for you when you download the above packages, but I'm not sure about that.

---

