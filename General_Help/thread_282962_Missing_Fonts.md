---
title: "Missing Fonts"
date: 2006-10-23
forum: General Help
---

### Post by jimmyk on 2006-10-23
Hi All,

Been having problems with fonts in emacs after changing my graphics driver. I found this thread which partially helps:

[http://ubuntuforums.org/showthread.php?t=163674&highlight=emacs]("http://ubuntuforums.org/showthread.php?t=163674&highlight=emacs")

But for a permanent solution it says I need to change the paths of some files in my xorg.conf from

```
/usr/share/X11/fonts/
```

to

```
/usr/share/fonts/X11/
```

But none of the files exist in that directory either?? :confused: 

This is the section in my xorg.conf that I have changed, which specifies the missing files:

```
Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection
```

Does anybody know where can I get the missing files?

Thanks

James

---

### Post by danielph on 2006-10-26
I believe xfonts-base contains the fonts you need. Maybe installing or reinstalling the package will help you

---

### Post by jimmyk on 2006-10-29
Please help - this is driving me nuts ](*,)

I upgraded to edgy, just in case it improved the situation, but it made it worse.  Previously I could start emacs using:

```
emacs -fn 10x20

```
But now that doesn't work, I just get the messages:

```
Warning: Cannot convert string "-*-courier-medium-r-*-*-*-120-*-*-*-*-iso8859-*" to type FontStruct
Warning: Cannot convert string "-*-helvetica-medium-r-*--*-120-*-*-*-*-iso8859-1" to type FontStruct
```

I read on another forum that I may need to change my ~/.Xdefaults, but that didn't exist and creating it didn't help either. :cry:

Please help if you can, or even if you can't - any suggestion welcome

James

---

