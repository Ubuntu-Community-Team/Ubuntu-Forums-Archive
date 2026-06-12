---
title: "thunderbird &amp; firefox statically linked"
date: 2008-01-28
forum: General Help
---

### Post by mättu on 2008-01-28
Does anyone know how to build / where to find statically linked ("standalone") versions of thunderbird / firefox?
It would be great to have portable linux versions of these applications to take with you on a usb-stick.

As for firefox it works at the moment (2.0.0.9) to have it installed on usb if firefox is installed on the host machine as well. It then uses the hosts libraries. In my case it works even if the installed "host-firefox" is not the same version as the "portable". Anyway, this is not a desired way to make things work, as it depends on compatibilty between the two versions..

Thunderbird (2.0.0.9) works, but often crashes (core dumped) - due to different versions I guess.

At the moment I use a windows version of thunderbird from portableapps.com under wine. This works, but seems quite weird to me, as i almost never use it on windows machines.. And it doesn't allow to open links in firefox. (wine-error: usage winebrowser URL)

tanks for your attention.

cheers
:m)

---

### Post by jrusso2 on 2008-01-28
I have never seen a static linked Firefox wish they had it.  Esp the Firefox 3 beta.

I have seen Static linked Opera in both .deb and rpm on their website.

---

### Post by mättu on 2008-01-29
well I succeded in building thunderbird, but it segfaults as well as the original build from mozilla..

---

### Post by mättu on 2008-01-31
.. update..

core-dumps seemed to be due to errors in prefs.js. Mine, about 5 years old and migrated many times between different versions of windows and linux, was 13 pages in A4-printout, whereas a "fresh" file only needs 2 pages. 


So there is how I managed to compile a "standalone thunderbird". At least I think so..

****
I downloaded and compiled TB with help from this wiki-page: (read changes below first!)
[https://wiki.ubuntu.com/CompileThunderbirdNewVersion?highlight=%28thunderbird%29](https://wiki.ubuntu.com/CompileThunderbirdNewVersion?highlight=%28thunderbird%29)

changes:
Of course, don't wget version 1.5.2 but 2.x.x.x instead! (Or browse & download manually)
Add one line to .mozconfig: 
ac_add_options --enable-static --disable-shared
(from: 
[http://developer.mozilla.org/en/docs/Configuring_Build_Options](http://developer.mozilla.org/en/docs/Configuring_Build_Options)
)

This took +- 2h compile time on a 1.6GHZ-Xubuntu-Box.
***

And here, how to migrate mail using a fresh prefs.js. I don't know if this is generally advised, so perhaps only try in a desperate situation like mine when TB core dumps every time you download mail.. Possibliy one could repair tho old file, but according to be modern I thouht "ending is better than mending".

***
general backup of *everything*, just to be shure.

I started out with a fresh copy by thunderbird 2.0.0.9:
(in "portable-thunderbird"-folder)
./thunderbird -profile "my_new_profile"
generated all my mailaccounts to force thunderbird to write a clean prefs.js

shut down thunderbird

backed up old prefs.js

replaced with fresh one from "my_new_profile/"

found out that TB had named my account folders in Mail/ differently than 5 years ago, due to a rename of my mail-provider, so copied over my old mail to the according folders. 
A little guessing was neccessary, but as long as you don't overwrite the original folders, nothing bad should happen. I had my mail in the wrong accounts, so I shut down TB again, swapped the folders and found myself happy again.

opened thunderbird with my standard-profile.

And voilà! Everything back in place. I only had to retype my passwords.
No more core dums so far.

Would be interested to hear from you, fellow compilers. ;-)
I know, this is not a gentoo-forum, but it was fun anyway, so have a try if you like.

cheers
:m)

---

### Post by mättu on 2008-02-01
update 2

core dump (every time TB fetches Mail) happens with theme "Cyclene" but not with standard theme.

by the way: firefox compiles as easy as thunderbird. just use the firefox compile wiki page and the compiler-flag line meant in the previous post.

So I'm travelling the world with an usb-stick in my pocket containing all my mail, bookmarks & open tabs. (besides all my documents, abyss-webserver to start from a console and so on)
not to forget portable-cygwin for the saddest of all cases.
quite cool. :-)

---

