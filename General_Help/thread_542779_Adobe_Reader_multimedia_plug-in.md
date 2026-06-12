---
title: "Adobe Reader multimedia plug-in ?"
date: 2007-09-04
forum: General Help
---

### Post by wgw on 2007-09-04
I have a pdf file that has audio. When I open it in Adobe Reader I get the pages but no audio; only an error message: 'the plug-in required by this  "Rendition" action is not available'.

Are there linux multimedia plug-ins for the Reader? I found nothing on the Adobe site.

Thanks for any suggestions.

---

### Post by frank95com on 2007-09-04
What about opening with another program (like evince kpdf or something other)?
Maybe you can find a working one.:)

---

### Post by wgw on 2007-09-04
As far as I can tell, evince does not support sound. Xpdf and kpdf might, but can't confirm that yet.

Will do a bit of experimenting later. 

Thanks!

---

### Post by wgw on 2007-09-22
So, my conclusion is: audio+pdf reader+ linux = zilch. It does not work. You could put a link in a pdf file to a sound file, and then click on that, but otherwise, as far as I can tell, you can't 1) take a windows Pdf file with sound and play it on linux or 2) create a pdf file with sound on linux and play it on windows. I'm probably wrong about 2, but my conclusion is that cross platform sound + pdf doesn't work. 

:(

---

### Post by SanGimignano on 2007-09-25
You can try Adobe Reader 8.1.1 which is available for download. The multimedia plugin is available in this version : 
[ftp://ftp.adobe.com/pub/adobe/reader/unix/8.x/8.1.1/enu/AdobeReader_enu-8.1.1-1.i386.deb](ftp://ftp.adobe.com/pub/adobe/reader/unix/8.x/8.1.1/enu/AdobeReader_enu-8.1.1-1.i386.deb)

---

### Post by wrathkeg on 2007-09-25
> **wgw said:**
>  2) create a pdf file with sound on linux and play it on windows.
You can if you create the pdf with LaTeX.  If you are a LaTeX user, let me know and I can tell you how to do it.  I can't get the sounds to play with any reader under Linux, though.

WK

---

### Post by wgw on 2007-09-25
A new Adobe reader: great! I'll give it a try.

---

### Post by wgw on 2007-09-25
well, Adobe 8 reader does have multimedia support, but not directly. My embedded mp3 files would not play, and when Adobe took me to their website for a plugin, I got this message:

> We're sorry, but the third-party media player required to play the selected media file in your Adobe PDF document isn't available for your system. No media player will be downloaded at this time.

Adobe Acrobat 6.0 Professional, Adobe Acrobat 6.0 Standard, and Adobe Reader 6.0 for Windows currently support the following media players for playback: Flash, QuickTime, RealPlayer, and Windows Media Player. Acrobat 6.0 and Adobe Reader 6.0 for Mac OS currently support QuickTime. For information about system requirements and media types supported by these third-party media players, please visit the following Web sites:

For Flash, visit [www.macromedia.com](www.macromedia.com) (U.S.)

For QuickTime, visit [www.apple.com](www.apple.com) (U.S.)

For RealPlayer, visit [www.realnetworks.com](www.realnetworks.com) (U.S.)

For Windows Media Player, visit [www.microsoft.com](www.microsoft.com) (U.S.) 

So, now it is the player for 8 that is needed under ubuntu.

---

### Post by wgw on 2007-09-25
For Latex: yes, that is a possibility. And one might hope that openoffice will soon give audio support for creating pdf files. I will take a look at Lyx to see if there are any facilities for managing multimedia, though it is probably simple enough to go directly through latex.

---

