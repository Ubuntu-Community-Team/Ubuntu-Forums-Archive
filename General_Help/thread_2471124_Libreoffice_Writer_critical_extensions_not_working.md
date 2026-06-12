---
title: "Libreoffice Writer critical extensions not working"
date: 2022-01-21
forum: General Help
---

### Post by cigtoxdoc on 2022-01-21
Ask LibreOffice won't help on this, and I see few related posts on this forum. Basically, LANGUAGE TOOL will not load, neither will LIGHTPROOF nor ALT FIND & REPLACE.  Yes, I get error messages, but Ubuntu (currently 21.10, but same for earlier versions) won't let me copy them so I can paste them in this forum.  I find this very annoying since the leaders of this  forum need copies of the error messages to help solve problems, but apparently will not allow pasting of pictures of the error messages into the text.

If I doing something wront, please tell me.  LibreOffice will not load Lightproof on installation as it says it should.  I do scientiifc writing as part of my consulting business.  I mujch prefer working in Linux than using the alternatives.

Current text from LibreOffice help is:
Version: 7.2.5.2 / LibreOffice Community
Build ID: 20(Build:2)
CPU threads: 4; OS: Linux 5.13; UI render: default; VCL: gtk3
Locale: en-US (en_US.UTF-8); UI: en-US
Ubuntu package version: 1:7.2.5-0ubuntu0.21.10.1
Calc: threaded

John

---

### Post by norobro on 2022-01-22
I don't know about your other extensions but there is a newer version (1.6) of Lightproof that works here: [https://github.com/freedesktop/libreoffice-lightproof](https://github.com/freedesktop/libreoffice-lightproof)

I get the error in the image from the version in the LO repository.

---

### Post by cigtoxdoc on 2022-01-22
Thank you for your reply.  Unfortunately, those running Ubuntu and those running LibreOffice do not appear to communicate on things not working, even though a "union" of the two technologies is essential at least for technical success.

Several releases ago of the Ubuntu versions of LibreOffice, the extensions on LibreOffice writer such as Language Tool and Alt Find & Replace stopped working.  Even this past week's release (7.2.5.2) failed to fix the problem.  Everytime I would attemp to load the extensions I wouild get some unintelligibl error message that Libre Office prevents you for coopying so you can get help on it.  Out of disperation. I tried running LibreOffice Writer in the Safe Mode and the extensions loaded without error and things worked after a required restart of LibreOffice Writer.

John

---

### Post by KBar on 2022-01-22
> **cigtoxdoc said:**
> Yes, I get error messages, but Ubuntu (currently 21.10, but same for earlier versions) won't let me copy them so I can paste them in this forum. I find this very annoying since the leaders of this  forum need  copies  of the error messages to help solve problems, but apparently  will not  allow pasting of pictures of the error messages into the text.
Are these the error messages you're getting?

---

### Post by cigtoxdoc on 2022-01-22
Thank you, KBar.  The error messages you posted were similar to the ones I received until I put LibreOffice Writer in the Safe Mode before installing the extensions.  However, two questions still remain:

1.  Why does Ubuntu forbid users to simply copy any error message from any program so that the user receiving the error can post it in this forum?
2.  Why are there not a table of error messages and solutions for LibreOffice products?  These prouducts come as part of Ubuntu installations.

John

---

### Post by KBar on 2022-01-23
> **cigtoxdoc said:**
> However, two questions still remain:

1.  Why does Ubuntu forbid users to simply copy any error message from any program so that the user receiving the error can post it in this forum?
2.  Why are there not a table of error messages and solutions for LibreOffice products?  These prouducts come as part of Ubuntu installations.
[LIST=1]
[*]Ubuntu doesn't forbid anything. It's not a person, entity or the ultimate villain. It's a collaboration of thousands of volunteers working together to make open-source software just a tad bit better. That error dialog is designed by the team behind LibreOffice. It was probably an oversight from their part. Still, you can just screenshot individual error dialogs and share it here, just like I did. 
[*]There [is]("https://help.libreoffice.org/latest/en-US/text/scalc/05/02140000.html") but it's for LibreOffice Calc. We do things differently in the Linux community. Usually, applications do not print out cryptic and unrecognizable codes in case of a failure. Instead, diagnostic messages are streamed to standard error—which is connected to display by default—in full, including the offending line in the code. For example, in the error messages above it's explained to us that the syntax in line 116 of Lightproof.py (the extension itself) is invalid. In such cases, you can either try to contact the developer or find an analogous extension. 
[/LIST]
 
> Thank you, KBar.  The error messages you posted were similar to the ones  I received until I put LibreOffice Writer in the Safe Mode before  installing the extensions.
So do these extensions work now?

---

### Post by Impavidus on 2022-01-23
> **cigtoxdoc said:**
> 
1.  Why does Ubuntu forbid users to simply copy any error message from any program so that the user receiving the error can post it in this forum?

Ubuntu isn't in charge of copying text from error messages. The application giving the error message is. The only thing Ubuntu does is display a window with some pixels in it – not letters, pixels. The application could be so kind to allow copying the text to a system clipboard or could write the text directly to some log (in fact, it may have done so), but it's the responsibility of the program generating the error message.

---

### Post by cigtoxdoc on 2022-01-30
Thank you Kbar and Impavidus.

Users of LibreOffice and LibreOffice Writer and LibreOffice Impress, in particular, should not be expected to be computer gurus nor necessarily have ready access to IT support personnel who can deciper error codes that require special expertise or training to interpret.  In the situation, I encountered, the error message should have read, "Please restart LibreOffice Writer in the Safe Mode and install extensions after LibreOffice Writer has restarted in the Safe Mode."

John

---

