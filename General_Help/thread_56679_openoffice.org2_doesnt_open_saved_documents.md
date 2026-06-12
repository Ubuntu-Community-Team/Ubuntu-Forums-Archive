---
title: "openoffice.org2 doesnt open saved documents"
date: 2005-08-13
forum: General Help
---

### Post by shizow on 2005-08-13
i installed apt-get install openoffice.org2
i can save documents, but when i try to load a saved document OO crashes

any suggestions?

---

### Post by shizow on 2005-08-16
[QUOTE=shizow]i installed apt-get install openoffice.org2
i can save documents, but when i try to load a saved document OO crashes

any suggestions?[/QUOTE]
 

can anyone please help?

---

### Post by GTvulse on 2005-08-16
[QUOTE=shizow]can anyone please help?[/QUOTE]
 Which build? I have no such problems with 1.9.122...

---

### Post by kalahari875 on 2005-08-20
I have the same problem with the breezy release, OOo build 1.9.122. It won't open a saved document. For that matter, any OOo program crashes just upon running it. I had to install 1.1.4. :( 

Any ideas?

---

### Post by robins_web on 2005-08-20
[QUOTE=kalahari875]I have the same problem with the breezy release, OOo build 1.9.122. It won't open a saved document. For that matter, any OOo program crashes just upon running it. I had to install 1.1.4. :( 

Any ideas?[/QUOTE]
 And I can't get it to open saved documents with 1.1.4, even though they were created with 1.1.4. Keeps crashing.

---

### Post by GTvulse on 2005-08-24
[QUOTE=kalahari875]I have the same problem with the breezy release, OOo build 1.9.122. It won't open a saved document. For that matter, any OOo program crashes just upon running it. I had to install 1.1.4. :( 

Any ideas?[/QUOTE]
 That's a completely different ball of wax. As Breezy is moving on to using gcc 4 for all binaries (Debian testing is in the same process, fyi), the ABI (application binary interface) has changed and the runtime libraries are not the same as the ones in Hoary. In the latter, OOo2 1.9 build 122 is rock solid. You can try compiling OOo2 yourself under Breezy (a task for an seasoned hacker with a **fast** machine) or try whatever version that has been imported into Breezy's repositories lately.

---

### Post by shizow on 2005-08-25
[QUOTE=dradul]Which build? I have no such problems with 1.9.122...[/QUOTE]

the version is the one i installed with apt-get install openoffice2.org
when i do dpkg -l i see:
ii  openoffice.org 1.9.79.2-0ubun Office suite core, version 2.0

---

### Post by GTvulse on 2005-08-26
[QUOTE=shizow]the version is the one i installed with apt-get install openoffice2.org
when i do dpkg -l i see:
ii  openoffice.org 1.9.79.2-0ubun Office suite core, version 2.0[/QUOTE]
 Ones that are almost one year old. You should not be using them at all! (As stated at [http://development.openoffice.org/)](http://development.openoffice.org/)). Rather wait for Monday or Tuesday next week when build 1.9.125 will be released to the public, download and install that one. There is a (very complicated) set of instructions in the howtos section. My  version is simpler: [http://ubuntuforums.org/showthread.php?t=51889](http://ubuntuforums.org/showthread.php?t=51889)

---

### Post by gat on 2005-09-30
I'm having the same problem as shizow, but I can't figure out how to solve it (maybe I'm just too dense, too nooby, or both).

I don't know why, but my old OO 1.1 is now barely functioning (takes 10 minutes (seriously!) to open a file), so I downloaded the OO2 from synaptic.  It looks great, works great, and saves great -- but won't open it's own saved files.  Not a single one.

I've been using OO off and on for at least a year and I've never seen anything like that -- pretty scary.

I'm going to try dradul's link, even though I don't understand half of the code there.  I'll post my results -- wish me luck ;/

---

### Post by gat on 2005-10-01
Well, dradul was right -- seems to work fine :)

I downloaded from openoffice -- it wasn't exactly as they said it would be (they have a debian link that actually point to a music festival??) but, anyway...

I downloaded the 2.0 RC1 rpms from this page:
[http://download.openoffice.org/2.0.0rc/index.html](http://download.openoffice.org/2.0.0rc/index.html)
(I got a tarball named OOo_2-1.0.0rc1_050923_LinuxIntel_install.tar.gz)

Then cd to the download directory
Then unpack
$ tar -zxvf OOo*
Then cd to the directory that was unpacked
$ cd OOO*
(The actual directory I had was named OOO680_m1_native_packed-5_en-US.8958)
Then cd into the RPMS directory
$ cd RPMS

Then, the bit that really helped was dradul's code:
-$ fakeroot alien -d --fixperms *.rpm
-$ sudo alien -i *.deb desktop-integration/*.deb
-$ sudo chmod 755 /opt/openoffice*/program/soffice

This magically transformed the *386.rpm files into *.386.deb files and then ran them.  (BTW, I had Synaptic open at the time, which was a no-no -- but fortunately didn't hurt anything.  Close Synaptic, Kynaptic, or anything else that might be locking the apt files.)  

Then I could run soffice from the command line
$  /opt/openoffice*/program/soffice

Some issues I noticed:
I was only able to build the 386 debs, not the 586 -- maybe I don't have headers or something?
I'm using Kubuntu and so far can't find any of the entries in my menu, a session or two with the Kmenu editor will probably fix that (until then, I'm just using the command line).

Thanks for the help and good vibes -- let's hope a good, solid version lands in the apt repos soon

---

### Post by shizow on 2005-10-16
i updated to breezy and everything works

---

### Post by gat on 2005-10-16
I also updated to Breezy and OOo2 seems to be working very nicely.  Still, I ran into some unrelated problems
(
[http://www.ubuntuforums.org/showthread.php?p=417851#post417851](http://www.ubuntuforums.org/showthread.php?p=417851#post417851)
)
That would make me suggest that noobies think twice before jumping straight from Hoary into Breezy -- especially if the OOo2 problem is the only thing wrong with an otherwise perfect Hoary box.

---

