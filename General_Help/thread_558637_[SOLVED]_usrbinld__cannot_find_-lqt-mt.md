---
title: "[SOLVED] /usr/bin/ld:  cannot find -lqt-mt"
date: 2007-09-24
forum: General Help
---

### Post by blackhole54 on 2007-09-24
I am trying to compile mythtv and getting the error:

/usr/bin/ld:  cannot find -lqt-mt

I found [this post]("http://readlist.com/lists/mythtv.org/mythtv-users/2/14291.html") where the poster was having the same problem in *dapper drake*.  It would appear from the reply that I am missing the symlink *libqt-mt.so* which should be pointing (in my case) to */usr/lib/libqt-mt.so.3.3.6*.  I have installed *qt3-dev-tools* which gave me *libqt-mt.so.3.3.6*, but not the required symlink.  The follow-up poster on the above linked post suggested the symlink would be part of a different package (at least it was on Fedora, which is what he was using).  Is there another package I should be installing to resolve this?

Thank in advance for any help.

EDIT:  I should have mentioned I am running *edgy eft*

---

### Post by Soybean on 2007-09-24
I don't actually know the answer, and I'm running Feisty so I can't check for you with certainty. But I'd suggest opening Synaptic and starting with libqt3-mt, then maybe libqt3-mt-dev. If those don't work, I'd just search for "qt3" and look through the results for something promising. Good luck! :)

---

### Post by blackhole54 on 2007-09-24
Thanks for the response, Soybean.


> **Soybean said:**
> then maybe libqt3-mt-dev

Bingo!  From *apt-cache show libqt3-mt-dev*:

> 
This package contains the libqt-mt.so symlink, necessary  for building threaded Qt applications as well as the libqui.so symlink  and the necessary header files for libqui.so.


Unfortunately, *libqt3-mt-dev* has a boatload of dependencies  -- 20+ MB of disk space to get that one symlink.  :(  But I guess that's the right way to do it; probably save myself some grief down the road.

To help anybody else who tries to do this, *libxv-dev* and *libxxf86vm-dev* were also required  to get similar symlinks.  I'll also point out that as I incrimentally added packages and reran **make**, I eventually hit a baffling error.  But starting from a clean slate by  deleting the entire directory and re-exctracting from the tarball produced an error free compile.

---

### Post by severedspirit on 2007-09-24
im having a similar problem, unfortunately I'm not sure how to handle it. I'm currently trying to compile the most recent build of MythTV  however it gets half way down the screen and reports '/usr/bin/ld: cannot find -lqt-mt', I try and fix this by installing libqt3-mt-dev but it says that its not available.

Any Ideas?

---

### Post by blackhole54 on 2007-09-24
> **severedspirit said:**
> I try and fix this by installing libqt3-mt-dev but it says that its not available.

What application are you using to try to install it and what version of Ubuntu are you running?  Did you update your package list first?  I'll admit I am just fishing here, but it is all I can think of to ask.

EDIT:  I guess I should have also asked what architecture.  I've also wondered if maybe that message happens when they are updating a package and that it will be OK later.  If you're feeling adventurous, [this page]("https://launchpad.net/ubuntu/edgy/+package/libqt3-mt-dev") provides some links down the left side of the page which you can (supposedly) follow to directly download the *.deb*.  Note that I only got those links displayed when I loaded the page _w/o_ Java Script enabled.  And of course, I take no responsibility for what happens when you feel adventurous.  ;)

---

### Post by Soybean on 2007-09-25
Yeah, it's usually the -dev packages you need for compiling things. Usually when you're missing a -dev, though, it shows up as a missing header rather than a missing library, which is why I suggested the other one first.

> **severedspirit said:**
> I try and fix this by installing libqt3-mt-dev but it says that its not available.

Er... it looks to me like it's part of the main repository. So, it really *ought* to be available... maybe try ```
sudo aptitude install libqt3-mt-dev
``` and post the output here if it gives an error.

Oh, it might have just been a server or network problem. So just trying again might fix it.

---

