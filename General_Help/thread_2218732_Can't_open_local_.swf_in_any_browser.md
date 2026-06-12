---
title: "Can't open local .swf in any browser"
date: 2014-04-21
forum: General Help
---

### Post by lucasnye on 2014-04-21
Hello,

Today I upgraded to 14.04 and have met a problem that I've not yet been able to solve. I cannot play local .swf (flash games that I downloaded). Said games worked fine in 13.10 with Chromium and on Windows 7 with Google Chrome.

Now, whenever I try to play a local .swf, it makes me download it again (for Firefox, it prompts me with the "open with..." window), which I don't understand why because it's a local file. I want to play my .swf in my browser (tried gnash standalone but it runs my swfs slowly, making for example The Binding Of Isaac unplayable and bugged, while it ran really smoothly and perfectly in Chromium). However, any .swf files I see on a webpage runs perfectly. It just _doesn't work for local files_.

I would really prefer to open my swfs in Chromium instead of some standalone software _if possible_.
Anyone got a fix?

Thanks by advance.

---

### Post by monkeybrain20122 on 2014-04-21
Probably because flash 11.2 doesn't work. You may need pepper-flash. Either install Chrome or install pepperflashplugin-nonfree from the repository (Chromium only)
Don't even bother with gnash, it just clutters up your system.

---

### Post by lucasnye on 2014-04-23
> **monkeybrain20122 said:**
> Probably because flash 11.2 doesn't work. You may need pepper-flash. Either install Chrome or install pepperflashplugin-nonfree from the repository (Chromium only)
Don't even bother with gnash, it just clutters up your system.

I tried both of the solutions, but it still tries to download my .swf instead of playing it with Flash. I manually set Firefox to play the swf using the flash plugin, it still gave me the "open with" window.

What shall I try now?

---

### Post by fraser3 on 2014-04-23
This is driving me crazy too -- I am so addicted to Binding Of Isaac.  I have the same exact symptoms.

I have worked around it by creating an HTML file in the same directory as my Isaac.swf file, which simply loads the swf file.  I'll provide the full text below.

This works and is playable.  However it does not have my game progress (unlocked items, mom kills, etc.)
This should be solveable ( [http://bindingofisaac.wikia.com/wiki/Save_Data](http://bindingofisaac.wikia.com/wiki/Save_Data) ) but so far I have not found an so.sol file that works.  I think  I know which source so.sol file to use, but I'm not sure where to put it for pepperflash.

There is one other problem:  no progress is being saved in my games anymore.  I am starting from a pristine state (no mom kills, no items unlocked) every time.

Still this is the best I've got.  For me, this is working the same in both firefox and chromium.

Here's the full text of the HTML file I created.   Make sure you updated the filename ("Isaac.swf" below) to match whatever you've got.

[PHP]
<html>
<head>
<title>The Binding Of Isaac - v1.48 Wrath of the Lamb</title>
</head>
<body>
<OBJECT classid="clsid:D27CDB6E-AE6D-11cf-96B8-444553540000" codebase="http://download.macromedia.com/pub/shockwave/cabs/flash/swflash.cab#version=6,0,0,0" WIDTH="100%" HEIGHT="100%" id="The Binding Of Isaac" ALIGN="">
<PARAM NAME=movie VALUE="Isaac.swf">
<PARAM NAME=quality VALUE=high>
<PARAM NAME=bgcolor VALUE=#000000>
<EMBED src="Isaac.swf" quality=high bgcolor=#333399 WIDTH="100%" HEIGHT="100%" NAME="Isaac.swf" ALIGN="" TYPE="application/x-shockwave-flash" PLUGINSPAGE="http://www.macromedia.com/go/getflashplayer"></EMBED></OBJECT> 
</body>
</html>[/PHP]

EDIT: 
Forgot to explain this -- after creating the html file with correct path/filename, open the html file in your browser instead of opening the swf file directly.

---

### Post by lucasnye on 2014-04-24
Thank you, but that's not the solution I'm looking for, I'm afraid. I have 200+ .swf and I don't feel like creating 200+ .html pages to open them.

---

### Post by dragonfly41 on 2014-04-24
See this related thread ... [http://ubuntuforums.org/showthread.php?t=2218710](http://ubuntuforums.org/showthread.php?t=2218710)

---

### Post by lucasnye on 2014-04-24
I can't use the projector since I use a 64bits version of Ubuntu and the projector is only 32bits.

---

### Post by lucasnye on 2014-04-27
A small bump. Please guys, I need to fix it, I also have work in .swf.

---

### Post by sebastian-valnar on 2014-04-27
Got the same problems, found some potential hints in the Arch forums:
[https://bbs.archlinux.org/viewtopic.php?pid=1374454#p1374454](https://bbs.archlinux.org/viewtopic.php?pid=1374454#p1374454) and following.
I already tried changing /usr/share/mime/packages/freedesktop.org.xml accordingly and doing
```
sudo update-mime-database /usr/share/mime
```
but I'm getting several "unknown media type" messages and the program doesn't complete but just stops at some point. Doesn't fix the problem either. Maybe this will help somebody else figure it out...

---

### Post by dragonfly41 on 2014-04-27
I only run flash on my 32bit ubuntu 12.04 .. but this thread might help you

[http://flexceptional.blogspot.co.uk/2011/04/install-stand-alone-flash-player-on-64.html](http://flexceptional.blogspot.co.uk/2011/04/install-stand-alone-flash-player-on-64.html)

---

### Post by jmb-tux on 2014-05-01
I have the same problem after a fresh Xubuntu 14.04 installation (separate partition).
Neither Firefox (28 like 29) nor Chrome are able to play local SWF files - but playing them from Internet sources is no problem.
I used thunar to make the appropriate browser the standard application for SWFs but than both react in recursion of opening new tabs/`downloading' (i.e. copying local find in the Download directory ... no comment for that functionality of Chrome).
I also had a hint with a mime type problem:
(from another thread I just tried: "sudo rm /usr/share/mime/packages/kde.xml", but without result, but the 2nd command yield the following errors):
```

sudo update-mime-database /usr/share/mime
Unknown media type in type 'chemical/x-alchemy'
Unknown media type in type 'chemical/x-cache'
Unknown media type in type 'chemical/x-cactvs-ascii'
Unknown media type in type 'chemical/x-cactvs-binary'
Unknown media type in type 'chemical/x-cactvs-table'
Unknown media type in type 'chemical/x-cdx'
Unknown media type in type 'chemical/x-cdxml'
Unknown media type in type 'chemical/x-chem3d'
Unknown media type in type 'chemical/x-cif'
Unknown media type in type 'chemical/x-cml'
Unknown media type in type 'chemical/x-daylight-smiles'
Unknown media type in type 'chemical/x-dmol'
Unknown media type in type 'chemical/x-gamess-input'
Unknown media type in type 'chemical/x-gamess-output'
Unknown media type in type 'chemical/x-gaussian-input'
Unknown media type in type 'chemical/x-gaussian-log'
Unknown media type in type 'chemical/x-genbank'
Unknown media type in type 'chemical/x-gulp'
Unknown media type in type 'chemical/x-hin'
Unknown media type in type 'chemical/x-inchi'
Unknown media type in type 'chemical/x-inchi-xml'
Unknown media type in type 'chemical/x-jcamp-dx'
Unknown media type in type 'chemical/x-macromodel-input'
Unknown media type in type 'chemical/x-mdl-molfile'
Unknown media type in type 'chemical/x-mdl-rdfile'
Unknown media type in type 'chemical/x-mdl-rxnfile'
Unknown media type in type 'chemical/x-mdl-sdfile'
Unknown media type in type 'chemical/x-mdl-tgf'
Unknown media type in type 'chemical/x-mmcif'
Unknown media type in type 'chemical/x-mol2'
Unknown media type in type 'chemical/x-mopac-graph'
Unknown media type in type 'chemical/x-mopac-input'
Unknown media type in type 'chemical/x-mopac-out'
Unknown media type in type 'chemical/x-msi-car'
Unknown media type in type 'chemical/x-msi-hessian'
Unknown media type in type 'chemical/x-msi-mdf'
Unknown media type in type 'chemical/x-msi-msi'
Unknown media type in type 'chemical/x-ncbi-asn1'
Unknown media type in type 'chemical/x-ncbi-asn1-binary'
Unknown media type in type 'chemical/x-ncbi-asn1-xml'
Unknown media type in type 'chemical/x-pdb'
Unknown media type in type 'chemical/x-shelx'
Unknown media type in type 'chemical/x-vmd'
Unknown media type in type 'chemical/x-xyz'

```
But after removing
 /usr/share/mime/packages/chemtool.xml 
/usr/share/mime/packages/chemical-mime-data.xml
No error message is shown but still no local file got be used inside a browser.

I never saw that problem before and I don't have any clue ...

I would appreciate any hint how to solve this problem or
at least how to clearly identify the reason for the problem.
What may be the relevant package to open a bug report?

Small update: clean installation of browsers/plugins and removing personal settings does not change anything.
Xubuntu 13.10 has no problem running local files, 14.04 LTS denies it ...

---

### Post by lucasnye on 2014-05-04
Still no solution to me. I guess it's fine to report the problem to Canonical. I found a temporary solution to the problem: Crutziplayer. It works and requires Adobe's plugin to work, but out of 10 .swf, 3 didn't work/worked poorly. It performs really bad on heavy files, such as 50Mb .swf. That will work for now, but I hope to get this problem fixed to get back to performance and total fonctionnality in browsers.

---

### Post by someonestoleallmyhandles on 2014-05-08
This was driving me nuts.

Now I'm not a fantastic person at understanding Ubuntu, but I do have some good google-fu.
And this is what I found at:
[https://bbs.archlinux.org/viewtopic.php?id=173295&p=2](https://bbs.archlinux.org/viewtopic.php?id=173295&p=2)
> 
[COLOR=#333333][FONT=sans-serif]So the workaround for this is to edit /usr/share/mime/packages/freedesktop.org.xml and change[/FONT][/COLOR]
[FONT=sans-serif]<mime-type type="application/vnd.adobe.flash.movie">[/FONT]
[COLOR=#333333][FONT=sans-serif]to[/FONT][/COLOR]
[FONT=sans-serif]<mime-type type="application/x-shockwave-flash">[/FONT]
[COLOR=#333333][FONT=sans-serif]and then run[/FONT][/COLOR]
[FONT=sans-serif]update-mime-database /usr/share/mime[/FONT]
[COLOR=#333333][FONT=sans-serif]
I did this, reinstalled flash player a couple of times and hey-presto it started working.

<3[/FONT][/COLOR]

---

### Post by Drowz0r on 2014-05-11
Hello there

I did the same thing:

> **someonestoleallmyhandles said:**
> 

[COLOR=#333333][FONT=sans-serif]So the workaround for this is to edit /usr/share/mime/packages/freedesktop.org.xml and change[/FONT][/COLOR]
[FONT=sans-serif]<mime-type type="application/vnd.adobe.flash.movie">[/FONT]
[COLOR=#333333][FONT=sans-serif]to[/FONT][/COLOR]
[FONT=sans-serif]<mime-type type="application/x-shockwave-flash">[/FONT]
[COLOR=#333333][FONT=sans-serif]and then run[/FONT][/COLOR]
[FONT=sans-serif]update-mime-database /usr/share/mime[/FONT]



And reinstalled flash player.

Worked perfectly :D

---

### Post by lucasnye on 2014-05-12
That mime modification actually worked! Thank you very much!

---

### Post by professordenis on 2014-06-03
I just made the changes in [COLOR=#333333][FONT=sans-serif]freedesktop.org.xml file.

Since I need change that in many PCs, I made a *patch.sh* script:

```
#!/bin/bash
clear
echo "Update file freedesktop.org.xml...";
sed  -e "s/<mime-type  type=\"application\/vnd.adobe.flash.movie\">/<mime-type  type=\"application\/x-shockwave-flash\">/g"  /usr/share/mime/packages/freedesktop.org.xml >  /usr/share/mime/packages/freedesktop.org.xml.new
mv /usr/share/mime/packages/freedesktop.org.xml /usr/share/mime/packages/freedesktop.org.xml.original
mv /usr/share/mime/packages/freedesktop.org.xml.new /usr/share/mime/packages/freedesktop.org.xml
echo "File updated successfully!";
echo "Update mime database...";
update-mime-database /usr/share/mime
echo "Mime database updated successfully! ALL DONE!";
```[/FONT][/COLOR]

Run it as root!

---

### Post by upcroft on 2014-12-02
This worked for me on Ubuntu 14.04 and chrome. Thanks for the info.

---

