---
title: "Aptana issues, thinks chrome is default"
date: 2014-07-30
forum: General Help
---

### Post by theller on 2014-07-30
I am trying to load Aptana on Ubuntu 14.04 and I cannot get it to work. Well...it works, it's just the preview gives me this error <Unhandled event loop exception No more handles [Could not detect registered XULRunner to use]>. When I searched this error the hits were 2+ yrs old so I figured I must have done something. 

I did add Oracle Java, 
~$ java -version
java version "1.7.0_65"
Java(TM) SE Runtime Environment (build 1.7.0_65-b17)
Java HotSpot(TM) 64-Bit Server VM (build 24.65-b04, mixed mode)

When I used Aptana for the first time as root it gave me a popup saying something about Chrome being the default browser...it seems Aptana or Eclipse thinks I am using Chrome but Chrome/Chromium is not on the system? If I delete .metadata file for the normal user, opening Aptana gives me < We were unable to load the Chromium browser. Please check documentation for details on possible workarounds/fixes. >.

I found this post: [http://superuser.com/questions/308290/how-to-really-set-chrome-as-the-default-ubuntu-browser](http://superuser.com/questions/308290/how-to-really-set-chrome-as-the-default-ubuntu-browser)
~$ sudo update-alternatives --config x-www-browser
[sudo] password for theller: 
There is only one alternative in link group x-www-browser (providing /usr/bin/x-www-browser): /usr/bin/firefox
Nothing to configure.

Should I try creating ~/.local/share/applications/mimeapps.list mentioned in superuser post? Any other ideas?

---

