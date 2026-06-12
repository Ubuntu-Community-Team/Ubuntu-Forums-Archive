---
title: "lastest flash delayed?"
date: 2018-01-20
forum: General Help
---

### Post by yazdzik-k on 2018-01-20
Dear Friends,

For some reason,  the latest flash 28.0.0.137 has been available in Debian for over a week,  and I cannot seem to get it in Ubuntu.  Is there some problem with my sources?

```


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu artful partner
# deb-src http://archive.canonical.com/ubuntu zesty partner


# deb http://archive.ubuntu.com/ubuntu artful-security main restricted multiverse
# deb http://archive.ubuntu.com/ubuntu artful-security universe
deb http://archive.ubuntu.com/ubuntu artful main universe restricted multiverse
deb http://security.ubuntu.com/ubuntu/ artful-security multiverse main restricted universe
deb http://archive.ubuntu.com/ubuntu artful-updates multiverse main restricted universe


```

Normally it updates relatively soon after Debian,  and,  whatever the political opinions,  we still live in a world where flash is used by many sites.

Obviously,  once can run flash installer,  that updates firefox perfectly,  but leaves an error in Chromium,  Opera.  Not sure where the problem is,  I can,  of course,  manually copy paste the files from the debian box,  but believe there is either an updater issue on my machine,  or I am missing something else.

All good wishes,
Martin

---

### Post by deadflowr on 2018-01-20
It's in proposed.
[https://launchpad.net/ubuntu/+source/adobe-flashplugin]("https://launchpad.net/ubuntu/+source/adobe-flashplugin")

---

### Post by yazdzik-k on 2018-01-20
Dear Dead,

Thank you very much indeed for the prompt relief.

Very best,

Martin

---

### Post by deadflowr on 2018-01-20
You can grab it from proposed:
[https://wiki.ubuntu.com/Testing/EnableProposed]("https://wiki.ubuntu.com/Testing/EnableProposed")

---

### Post by yazdzik-k on 2018-01-20
Dear Deadflowr,

Thank you again for all the information.

For those who want to cheat fast,  one can download from the graciously provided source for one's version, [https://launchpad.net/ubuntu/+source/adobe-flashplugin](https://launchpad.net/ubuntu/+source/adobe-flashplugin),  then in less than a minute :

```

tar xvzt path/to/adobe-flashplugin_20171212.1.orig.tar.gz
sudo su
mkdir /usr/lib/adobe-flashplugin/old
mv /usr/lib/adobe-flashplugin/*.*  /usr/lib/adobe-flashplugin/old
mv path/to/adobe-flashplugin_20171212.1/yourarchitecture/libflashplayer.so /usr/lib/adobe-flashplugin/
mv path/to/adobe-flashplugin_20171212.1/yourarchitecture/libpepflashplayer.so /usr/lib/adobe-flashplugin/
mv path/to/adobe-flashplugin_20171212.1/yourarchitecture/manifest.json /usr/lib/adobe-flashplugin/


```

Obviously,  making the "old" backup directory is added paranoia,  but one always does that.  Just in case.  

Now,  thanks to Deadflowr,  one can simply install flash latest version in less time that it would take to use the updater.

Much gratitude,

M

---

### Post by Yellow Pasque on 2018-01-20
^I would advise against that. Just download the .deb file(s) and install it if you don't want to modify your sources.

---

### Post by yazdzik-k on 2018-01-20
Dear T,

Therein lies the difficulty,  there are no deb files in the ubuntu proposed sources,  just the tars.  
Thus,  either take the files from debian,  which are easy to get,  and place them where ubuntu places them,  or wait for ubuntu to provide appropriate .deb,  or just do as we did for many many years,  use the tar to make debs,  or,  in this case, since there are only three files,  and the /etc files point to them for all the browsers,  it is as I said,  quick,  and dirty,  but certainly better than waiting another week,  as many sites control the version number of flash,  and will not load,  not to mention that unless chromium is flagged run outdated plugins,  flash will not run at all.  
Plus,  for old people,  the nature of linux was everything was the son of a file,  and that made it easy to grasp.  Sadly,  extensible markup has made simple text files obsolete for the most part, and I am not too sure anyone who spent more than ten minutes on the issue would not have done what I used to do by grabbing the files from my debian machines.  I merely tried to make it really fast by combining the two methods Dead's repo,  and the thirty second command line.   And no one should really be dependent on debs,  no pun intended.  Apt is a great convenience,  and I have used it for twenty years,  but in the end,  knowing where everything is and what it does is still better,  albeit less and less possible,  as anyone who tries to connect in a hurry in a hotel room with modern wifi security will tell you.  Editing /etc files in that case,  with the current complexities,  is not possible. 
Adding three files to a known place is simply faster that waiting,  using the deb from the adobe site,  which is bizarre since the browser checks OS version,  and artful is not supported,  this,  one way or another,  until ubuntu provides the debs,  we must copy files.  Or risk learning why even in supported files,  the varying debs which provide flash deposit the actual .so in different places.  This,  flash-installer only works for firefox,  and,  even then,  places the file in a different place.  One must,  one way or the other,  take account of the fact that people need to run about three browsers today,  given the varying compatibility with varying sites,  particularly internationally.  This is why,  of course,  the ubuntu deb, which  provides plugins compatible with both chromium and Mozilla based web browsers, is ideal,  although one would really like to say that debian and ubuntu would always place everything in the same place,  to insure total cross compatibility for all debs in all repos.  I personally do not know why ubuntu does not use exactly the same structure as debian, but used the ubuntu installer for the first time last year because of hardware issues,  and am deeply impressed with the automation.   And I would guess, since anyone needing up to date software tends to run a testing/sid mix,  ubuntu is a lot safer,  and debian stable is just too far behind in a world where most people have moved to incredibly fast multimedia,  and even good old youtube-dl  changes everytime google burps.  Thus,  to someone running artful,  going to the adobe site will not allow the download on an artful machine, the ubuntu deb is not ready,  and using the deb from deb multimedia will create chaos,  on a machine running three or four browsers,  and some sites have already required the latest flash,  we are stuck with a good old put the file where it belongs solution.

Had I read my post a year ago,  it would not have taken me twenty minutes to figure out how to do it.  Twenty minutes,  which is  three times the time it took to write this,  is an eternity in NYC in 2018.   Thus my post,  as a courtesy to the time stressed.   The placement of every file in Ubuntu should be common knowledge,  not something once should take twenty minutes of research and a bit of trial and error to find.  I was merely trying to prevent someone else from having to look. 
  
Very best,

M

---

