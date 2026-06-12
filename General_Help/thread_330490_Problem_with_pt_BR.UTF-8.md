---
title: "Problem with pt_BR.UTF-8"
date: 2007-01-03
forum: General Help
---

### Post by gramarga on 2007-01-03
Hello, everyone.

I have just installed 6.10 Edgy and everything seemed to work just fine.
Then I installed a statistical software (R) and had a big problem with encodings.

My locale is pt_BR.UTF-8. This software R recognizes characters such as ç, á, é and others, but when I try to create a plot using an X11 console, I get an error message saying it was impossible to find any X11 fonts.
A google search showed that changing my environment variable LANG to C should correct the prolem. Doing this actually allowed me to make plots, but I lost my desirable portuguese characters.

I don't know if this is the problem, but I don't have the '/usr/X11R6/lib/X11/locale' directory.
It is possible that I have a problem with my XLC_LOCALE, but I tried just about everything I found without success.

Thank you for your attention.
Glad if anyone can help.

Best,
Gabriel.

---

### Post by gramarga on 2007-01-03
Well, it's kinda odd replying to myself, but this might help someone.

I figured out what was wrong after I posted the first time.

It appears that the file /etc/X11/xorg.conf has wrong paths for the fonts directories. The default is /usr/share/X11/fonts, but (at least in my case) it should be /usr/share/fonts/X11.
I changed the following part of xorg.conf:

[FONT="Courier New"]Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection[/FONT]

to this:

[FONT="Courier New"]Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection[/FONT]

REBOOTED the PC and it worked just fine. Now I can make the plots with every character.
Hope this can help.
Gabriel.

---

### Post by gramarga on 2007-01-03
Oops! I forgot to mention something:
when you change your xorg.conf file this way, there is no need to change the LANG environment variable.
Cheers!

---

