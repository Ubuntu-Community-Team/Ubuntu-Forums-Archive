---
title: "Support for Danish charaters - how can I get this?"
date: 2005-10-31
forum: General Help
---

### Post by Strid on 2005-10-31
Hello.

I've converted from Windows til Hoary a couple of months ago, and I really like it. Everything seems to work fine and thats great. :)

My problem is, that I write text in danish use danish letters. In Windows I'd use WinEdt/LaTeX. I installed Texmaker and all the required LaTeX packages.
The problem is really, that when I open a .tex document that I wrote running Windows, all danish characters, (æ, ø and å or Æ, Ø, and Å) are displayed as question marks and when I compile the text it compiles as wierd characters like "ï?½".
If I try to write the text in Texmaker, the text looks as is should with all the æ, ø  and å's there as they should be. When I compile the .tex file, They all turn into Ã in the .DVI file

I've noticed other programs having difficulties with æ, ø and å. XMMS has the same issues and OpenOffice Word Processor doesn't do a good job recognizing  danish characters either.

I tried to set my locale to Danish (ISO-8859-1) using "dpkg-reconfigure locales", as seen in [this]("http://www.ubuntuforums.org/showthread.php?t=50346&highlight=nordic+characters") thread, but that didn't help.

I'd be happy if I could get some help, as I'm sure I'm not the only one with this problem. Lots of people, nordic as well as danish, are running Ubuntu - I don't hope all of them just switch to using Windows, when they write LaTeX documents, as I would have to do if I can't get this solved.

Thanks,
Anders Christensen

---

### Post by fut21 on 2005-10-31
Maybe this forum could help you.
[http://www.linuxin.dk/](http://www.linuxin.dk/)

---

### Post by monotux on 2005-10-31
[QUOTE=Strid]Hello.

I've converted from Windows til Hoary a couple of months ago, and I really like it. Everything seems to work fine and thats great. :)

My problem is, that I write text in danish use danish letters. In Windows I'd use WinEdt/LaTeX. I installed Texmaker and all the required LaTeX packages.
The problem is really, that when I open a .tex document that I wrote running Windows, all danish characters, (æ, ø and å or Æ, Ø, and Å) are displayed as question marks and when I compile the text it compiles as wierd characters like "ï?½".
If I try to write the text in Texmaker, the text looks as is should with all the æ, ø  and å's there as they should be. When I compile the .tex file, They all turn into Ã in the .DVI file

I've noticed other programs having difficulties with æ, ø and å. XMMS has the same issues and OpenOffice Word Processor doesn't do a good job recognizing  danish characters either.

I tried to set my locale to Danish (ISO-8859-1) using "dpkg-reconfigure locales", as seen in [this]("http://www.ubuntuforums.org/showthread.php?t=50346&highlight=nordic+characters") thread, but that didn't help.

I'd be happy if I could get some help, as I'm sure I'm not the only one with this problem. Lots of people, nordic as well as danish, are running Ubuntu - I don't hope all of them just switch to using Windows, when they write LaTeX documents, as I would have to do if I can't get this solved.

Thanks,
Anders Christensen[/QUOTE]

Ubuntu uses UTF-8, and windows does not. I would recommend you to use UTF-8 instead of iso-8859-1, it's A Good Idea (tm).

You might have to convert the papers you've written in windows, and replace the failing characters with proper ones :)

---

### Post by Strid on 2005-10-31
It there an easy way to convert files from Windows format to UTF-8? Like a command or script that could do this for me. That way, I would atleast be able to .tex coded documents written under Windows

The easy way to write LaTeX properly could be to write the text with Æ, Ø and Å and the use find/replace to have all characters replaced with LaTeX code, ie å = \aa etc.

Does UTF-8 in Ubuntu not support not english character? This can't be enabled or am I wrong?
What do you do, monotux? being swedish, you'd have to write ö and ä occationally, right?

---

### Post by monotux on 2005-11-02
[QUOTE=Strid]It there an easy way to convert files from Windows format to UTF-8? Like a command or script that could do this for me. That way, I would atleast be able to .tex coded documents written under Windows

The easy way to write LaTeX properly could be to write the text with Æ, Ø and Å and the use find/replace to have all characters replaced with LaTeX code, ie å = \aa etc.

Does UTF-8 in Ubuntu not support not english character? This can't be enabled or am I wrong?
What do you do, monotux? being swedish, you'd have to write ö and ä occationally, right?[/QUOTE]

For converting between charsets, I've found iconv very handy.

The thing is - I haven't had any problems with anything in ubuntu - not even the dreaded Å. Ä and Ö - but on the other hand, I only use one platform (and that's ubuntu), that's probably why I haven't run into any major problems... :)

---

### Post by Strid on 2005-11-03
[QUOTE=monotux]The thing is - I haven't had any problems with anything in ubuntu - not even the dreaded Å. Ä and Ö - but on the other hand, I only use one platform (and that's ubuntu), that's probably why I haven't run into any major problems... :)[/QUOTE]

I can't honestly say, that I haven't had problems with that. However! I managed to get it fixed. I tried "[FONT="Fixedsys"]dpkg-reconfigure locales[/FONT]" once again and set my locale to en_DK ISO-8859-1 again. After a reboot everything worked as it was supposed to. I can compile old document with ÆØÅ appearing and danish characters displayed properly in XMMS playlist and so on. This was a major step on my way to total and complete independence from Windows - yay.

What would the danger be if I use ISO-8859-1 and not UTF-8 - you say its a good idea to use UTF-8? I mean, everything now seems to work as it should(tm). :-k

---

### Post by DeliMart on 2005-12-01
perhaps i'm dumb or something, but when I run the "dpkg-reconfigure locales" i find it impossible to make a selection (I've tried x and * and just about every other key)  

help appreciated
:confused:

---

### Post by Bachstelze on 2005-12-01
Spacebar ?

---

### Post by DeliMart on 2005-12-02
I reinstalled my default locales in synaptic (System ->Administration->Synaptic package manager .... find locales in the list - right click - choose reinstall)  Now I'm happy again :)  æøå

---

### Post by Urmas on 2005-12-02
[QUOTE=DeliMart]Now I'm happy again :)  æøå[/QUOTE]

[IMG]http://img206.imageshack.us/img206/9250/bobforside16yv.gif[/IMG]

Good! Scandiphobia aka äöphobia aka æøphobia is a terrible disorder! [-X

---

### Post by registerdown on 2008-05-30
Reinstall locales din't work for me, but I successfully opened an ISO-8859-1 .TEX file (from Windows) with æ ø å characters in TexMaker by simply following the instructions here: [http://www.xm1math.net/texmaker/doc.html]("http://www.xm1math.net/texmaker/doc.html")

Quite a simple fix, might be useful for somebody else as well.  

> 1.1 Configuring the editor

Before compiling your first document, you must set the encoding used by the editor ("Configure Texmaker" -> "Editor" -> "Editor Font Encoding"). Then, you should use the same encoding in the preamble of yours TeX documents (example : \usepackage[latin]{inputenc}, if you use the "ISO-8859-1" encoding for the editor) 

---

