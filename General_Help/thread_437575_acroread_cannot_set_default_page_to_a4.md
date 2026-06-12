---
title: "acroread cannot set default page to a4"
date: 2007-05-08
forum: General Help
---

### Post by tomlyn on 2007-05-08
Every time acroread is started, both on Edgy and Feisty, the page default is set to letter. I have to go through "Properties" button to change "Page Size" to A4.

My printer is set default to A4 paper, my other programs know the printer is set to A4, but not acroread.

[COLOR="Red"]Is there any way to set the default to A4?[/COLOR] I have browsed /usr/bin/acroread and $HOME/.adobe/Acrobat/7.0/Preferences/reader_prefs files, but don't think I have change there. 

I appreciate your help.

[FONT="Courier New"]acroread -version output 7.0.9
I have a standard Feisty Fawn installation.[/FONT]

---

### Post by dcstar on 2007-05-09
> **tomlyn said:**
> Every time acroread is started, both on Edgy and Feisty, the page default is set to letter. I have to go through "Properties" button to change "Page Size" to A4.

My printer is set default to A4 paper, my other programs know the printer is set to A4, but not acroread.

[COLOR="Red"]Is there any way to set the default to A4?[/COLOR] I have browsed /usr/bin/acroread and $HOME/.adobe/Acrobat/7.0/Preferences/reader_prefs files, but don't think I have change there. 

I appreciate your help.

[FONT="Courier New"]acroread -version output 7.0.9
I have a standard Feisty Fawn installation.[/FONT]

What is in /etc/papersize ?

---

### Post by tomlyn on 2007-05-09
> **dcstar said:**
> What is in /etc/papersize ?

it is a4

[FONT="Courier New"]$ > more /etc/papersize 
a4
[/FONT]

---

### Post by dcstar on 2007-05-09
> **tomlyn said:**
> it is a4

[FONT="Courier New"]$ > more /etc/papersize 
a4
[/FONT]

Try and see if there is an Acroread config file somewhere in the /etc tree - other than that I don't know.

---

### Post by tomlyn on 2007-05-09
Found a similar posting on adobe forums
[http://adobeforums.com/cgi-bin/webx/.3bc02da1]("http://adobeforums.com/cgi-bin/webx/.3bc02da1")

Seems one has to look into the source code to figure this out :-?

---

### Post by tomlyn on 2007-05-09
> **tomlyn said:**
> Found a similar posting on adobe forums
[http://adobeforums.com/cgi-bin/webx/.3bc02da1]("http://adobeforums.com/cgi-bin/webx/.3bc02da1")

Seems one has to look into the source code to figure this out :-?

Forgot that source code for acroread is not available :mad: 
maybe this is why Feisty stopped including it in the standard repository.

---

### Post by pompos on 2007-05-09
Have the same problem with acroread and Firefox.
I use Kubuntu... might there be some trouble because those two programs use GTK+?

---

### Post by tomlyn on 2007-05-09
> **pompos said:**
> Have the same problem with acroread and Firefox.
I use Kubuntu... might there be some trouble because those two programs use GTK+?

For me, Firefox is OK, picks up the system setting.
I am using Ubuntu 7.04.

---

### Post by tomlyn on 2007-05-09
A similar posting with similar conclusion can also be seen on this forum at
[http://ubuntuforums.org/showthread.php?t=402889]("http://ubuntuforums.org/showthread.php?t=402889")

---

