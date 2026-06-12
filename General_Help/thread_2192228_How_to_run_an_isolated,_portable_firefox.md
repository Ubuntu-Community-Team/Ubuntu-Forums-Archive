---
title: "How to run an isolated, portable firefox?"
date: 2013-12-06
forum: General Help
---

### Post by blazzer12 on 2013-12-06
Isolated, because it shouldn't interfere with the installed one. Portable so its should work from distro to distro (all ubuntu based).

I tried extracting the source and running firefox and firefox-bin to no avail.

So how to do it?

**Solution : **

1) Download the Firefox Binary you want from here : [http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/](http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/)

2) Extract.

3) In Terminal set the current directory to where you extracted and type > firefox -ProfileManager

4) A dialog opens, click "create profile" and set the path for the 'profile' directory (prefarably in the extracted directory itself). Enter name for the profile.

5) Click 'finish' to start Firefox!

6) From next time, click on the file 'firefox'.

In step 4, if you did not change the 'profile' directory from its default (home directory) it interferes with the 'installed' version of Firefox, so kind of beats the purpose.

---

### Post by mikewhatever on 2013-12-06
If there is firefox-bin, it's binaries and not the source, also, you don't tell us what command you use to run it.
Try running it with './firefox', which means from the current directory. If it works, add the -P option for the desired profile. Profiles are stored in .mozilla/firefox/ in the home folder default, so you may consider moving the portable one out to ...whereever the portable firefox is. Then run it like this: ./firefox -P path _to_profile. For more options, check out 'firefox --help'.

---

### Post by ajgreeny on 2013-12-06
Just download the Firefox tar.gz direct from mozilla, extract it to its firefox folder on a USB and run the executable from there.

You will need the USB formatted to a linux filesystem in order to run an executable from it directly, or you could copy the whole folder from USB to hard disk and then make the binary executable.

---

### Post by C.S.Cameron on 2013-12-08
A while back I loaded Chrome OS, (from chromeos.hexxeh.net), to USB then replaced Chrome with FireFox.
Had to boot from USB rather than open from a running distro though.

---

### Post by blazzer12 on 2013-12-12
Thank you! I have been trying to run it on a NTFS drive all along!

---

### Post by blazzer12 on 2013-12-12
I am using > ./firefox but as pointed out by[COLOR=#000000] C.S.Cameron it [/COLOR][COLOR=#000000]should [/COLOR][COLOR=#000000]be[/COLOR] [COLOR=#000000]run on  Linux file system. I am doing it on NTFS.
[/COLOR][COLOR=#000000]
>  ./firefox -P path _to_profile  is exactly what I asked. Thank you.

It has 'firefox-bin', so binaries, got it.[/COLOR]

---

