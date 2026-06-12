---
title: "[SOLVED]Rythmbox not working / Subtitles wrong, help!"
date: 2013-11-06
forum: General Help
---

### Post by gordan-vrbanec-vepar on 2013-11-06
Hello!

So, Rythmbox stopped working all of a sudden.
I used it maybe twice, and now, whenever i click on the icon, it starts loading, then either nothing happens, or i get a crash report.
I have no idea why. I did nothing except install an Equalizer plugin from it's repos, but it worked fine after the install once, then this happened...
I kinda like it so i don't want to use other players. Can this be fixed?

Also...

How do i get ubuntu to reckognize croatian letters? For subtitles for example.
Everytime i get some subtitles, they're usualy ANSI encoded and VLC reads them wrong (&#269; as AE,ae and &#263; as é and simmilar...) , but Notepad++ reads them correctly.
That's why (in Windows) i opened them up, converted them to UTF-8 and it worked great. VLC displays them correctly after that.

This is a screenshot of random subtitles in Notepad++ in Windows:
[IMG]http://i42.tinypic.com/11azuav.png[/IMG]

And this is the screenshot of the same subtitles using Notepad++ (installed with wine) in Ubuntu:
[IMG]http://i41.tinypic.com/21jy7w6.png[/IMG]

Croatian characters are displayed wrong, so even if i convert to UTF they're not right to begin with and doesn't make any difference.

This is the same subtitles in the text editor that came with ubuntu (i don't know what it's called):
[IMG]http://i39.tinypic.com/f445rm.png[/IMG]

This one doesn't reckognize any of the characters... :/

Can anyone help me? I don't want to hop to windows everytime i watch a movie, just to convert subtitles... :(

I'm using Ubuntu 13.10.

---

### Post by gordan-vrbanec-vepar on 2013-11-07
Please. Anyone?

---

### Post by jamesisin on 2013-11-07
These should be two separate tickets.  You'll do better that way.  The two issues are not related.  For the Rhythmbox issue, it would be useful to include the crash data if you are able.

---

### Post by Impavidus on 2013-11-07
To get a bit technical, the so-called ANSI encoding isn't really an ANSI encoding. It's the Windows-1250 encoding for Central European languages, which is loosely based on a proposed ANSI standard and the ISO-8859-2 encoding for Central European languages. Microsoft once mislabled them, acknowledged their fault, but the misnomer stuck. For example, the character š is encoded in your file at 0x9a, in the standard at 0xb9 and in Unicode at 0x0161. Right now, the Linux applications recognise the subtitle files use a legacy 8-bit encoding, but they assume it's the ISO-8859-1 encoding for Western/Northern European languages, not the Windows-1250 encoding. Notepad++ in wine thinks it's the Windows-1252 encoding, almost identical to ISO-8859-1.

I don't know Rhythmbox or VLC very well, but there must be a menu somewhere to tell the program what the encoding of the subtitle file is. Else, you can convert the file to UTF-8 encoding (which is pretty much the standard, not only in Linux but on the web too). The command```
iconv -f WINDOWS-1250 -t UTF-8 -o <output file name> <input file name>
``` should do the trick. A text editor can do it too. In gedit you can specify the encoding when opening a file using the menu (not when double-clicking the file in the file manager). Then, without editing, save the file, selecting UTF-8 encoding.

I don't know about the crashes of your Rhythmbox. Someone else may help you with that.

One kind request: when posting large screenshots it's better to include them as attachments instead of in-line. Not everyone has a fast internet connection.

---

### Post by gordan-vrbanec-vepar on 2013-11-08
Hi!

Sorry for the screenshots and not putting this in separate threads. Won't happen again.

The Rhytmbox issue is "solved". I tried to reinstall it but after i uninstall it and try to install again it gives me an error.
I don't know how to post that error here because i didn't find any option to save a text version or something...
But i installed Banshee, and it's pretty simmilar to Rhytmbox so it's ok. I can use that instead. It's working ok for now.

About the subtitles...

The command line did it. I opened the newly created file with gedit and all characters were properly shown. Thank you!
I can't seem to save with gedit directly though. The "Save" and "Save As" options are grayed out. I can only save on the save button, but that does nothing except save the changes in the same file and same encoding.
I don't know if that's a bug or what, but it doesn't let me save the file.

But the terminal command does the job so it's ok. :)

---

### Post by jamesisin on 2013-11-08
I prefer Clementine:

[http://jamesisin.com/a_high-tech_blech/index.php/2013/04/oh-my-darling-musica/](http://jamesisin.com/a_high-tech_blech/index.php/2013/04/oh-my-darling-musica/)

---

### Post by gordan-vrbanec-vepar on 2013-11-08
I'll try that one too, thank you! :)

---

