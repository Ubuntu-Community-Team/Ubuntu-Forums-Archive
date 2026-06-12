---
title: "How can I hide the file extensions on Nautilus? (Trusty)"
date: 2014-04-21
forum: General Help
---

### Post by silex89 on 2014-04-21
Hi there, dear forumers! :D

As the thread title says, I'd like to hide the extensions of the files that I manage with Nautilus in Trusty, I personally prefer to see the icon instead of the extension, having both is sort of redundant to me. Is there a way to hide them?

Best regards and thanks in advance.

---

### Post by pfeiffep on 2014-04-21
In the upper right hand corner of a Nautilus screen there's a gear - click on the gear and choose preferences. You can choose the default view to icons.

---

### Post by silex89 on 2014-04-21
Hmmm, it seems we're confused here. I'm using Trusty Tahr with Nautilus 3.10, the gear is shown only in the 3.8 version were there was not a full menu implemented yet. Herewith the image that shows the header bar of the new nautilus.

[IMG]https://dl.dropboxusercontent.com/u/31580859/nautilus.png[/IMG]

The other thing is that I don't want to switch from the list mode to icon mode (I'm already in the icon view). What I want is to hide the file extensions from within my default icon view. I believe this can be done with GSettings, but I'm not sure.

---

### Post by pfeiffep on 2014-04-21
Interesting my Nuatilus version is 3.10.1

[COLOR=#800080][SIZE=2]*[FONT=UbuntuRegular]"Other than in Windows file extensions are not needed for files in Ubuntu. However they are used for convenience when it comes to sort out files according to their content. Therefore extensions are more like a fixed part of the filename and thus will always be displayed."[/FONT]*[/SIZE][/COLOR]
 
I'm not certain that file extensions can be effectively hidden in Linux ... read about it at the link below
[B][URL="http://askubuntu.com/questions/17561/how-to-hide-file-extensions"]
File extensions are fake[/URL][/B]

[COLOR=#333333][FONT=UbuntuRegular][By which I mean, in Linux, they are simply part of the file name and have no special meaning like in Windows.]("http://askubuntu.com/questions/17561/how-to-hide-file-extensions")[/FONT][/COLOR]

---

### Post by coldcritter64 on 2014-04-21
> **silex89 said:**
> .... I believe this can be done with GSettings, but I'm not sure.

I'm not so sure there is one either, it is possible, but don't recall ever seeing that option in Ubuntu or Debian since I started in 2007 in Gutsy. There is that option on Windows boxes "Hide extensions for known filetypes", but I've never seen it used in Linux/Ubuntu (still it is possible there is a setting tucked away in gsettings somewhere though).

Linux uses the mimetype of the file, more importantly than requiring the extension, to open or recognize file contents for display/playing. Although some programs require you to save with a known file extension, once saved you can delete the extension and the file remains usable and the icon/thumbnail etc all stay working. The system seems to recognize files by their mimetype not by their extension in my experience with Ubuntu/Linux.

I currently have 4 files, 1 .jpg, 1 .txt, 1 .mp3 and 1 .mkv file on the desktop with all extensions _*deleted*_. All retain their icons/thumbnails and all open / play with the correct application when double clicked, extensions are not entirely necessary to use in Linux. See attached screenshot for icons without any extension used, they still work fine.

---

### Post by HermanAB on 2014-04-21
Yup.  Files are identified by MIME type and a program called 'file'.  The extension is optional and a filename can have as many dots and things in it as you want.  So in general, the whole filename is significant and therefore, hiding part of it is not a good idea.

---

### Post by silex89 on 2014-04-21
Ok, I see. Thank you so much for all of that input guys! :). I'll stick with the default view instead. I guess it won't hurt to see the extension instead of the icon when I open up files.

Thank you once again!

Kind Regards

---

