---
title: "Hardy - terminal font/mime type problems"
date: 2008-05-03
forum: General Help
---

### Post by Senesence on 2008-05-03
I've just upgraded to Hardy, and there seem to be a few issues:

For one, the font rendering in the gnome-terminal seems to have a mind of it's own as to what fonts should look like. In other words, "Sans" looks fine everywhere else (desktop, gedit, openoffice, etc), but in the gnome-terminal, letters overlap and everything looks far too blurred.

Second, the icons for .blend files (a format used by the application blender) are no longer shown, even though the "MIME type" for these files is set to "application-x/blender". Now they just have that default blank file icon.

Same thing with regular text files. The mime type is clearly set to "text/plain", but unlike before, that little bit of text preview that you get when a file contains text is not showing.

How can I fix this?

---

### Post by noynac on 2008-05-03
> **Senesence said:**
> ...For one, the font rendering in the gnome-terminal seems to have a mind of it's own as to what fonts should look like. In other words, "Sans" looks fine everywhere else (desktop, gedit, openoffice, etc), but in the gnome-terminal, letters overlap and everything looks far too blurred....

I had the same problem with gnome-terminal and found a fix that involved copying the text between ~~~ and ~~~ below to a text file and saving it to my home directory with the name ".fonts.conf" (omit quotes). After restarting gnome-terminal, it used the system, fixed-width font the same as in Gutsy. 

Credit goes to John Buncher, who posted this fix in the following bug report. You can also download the font.conf file from that site. 

[https://bugs.launchpad.net/gnome-terminal/+bug/190848](https://bugs.launchpad.net/gnome-terminal/+bug/190848)

~~~
<?xml version="1.0"?><!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>rgb</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintfull</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>true</bool>
  </edit>
 </match>
</fontconfig>
~~~

---

### Post by Senesence on 2008-05-03
I wasn't quite sure which "home directory", so I placed your ".font.conf" (quotes omitted..of course) file in both "/home/" and "/home/user/" (aka "~").

...It changed nothing. The font in gnome-terminal is still messed up.

---

### Post by noynac on 2008-05-04
> **Senesence said:**
> I wasn't quite sure which "home directory", so I placed your ".font.conf" (quotes omitted..of course) file in both "/home/" and "/home/user/" (aka "~").

...It changed nothing. The font in gnome-terminal is still messed up.

Sorry--the correct file name is .fonts.conf. I placed the file in my user home directory (/home/noynac/.fonts.conf).

---

### Post by Senesence on 2008-05-04
Thanks, that worked.

Although, I must say, solutions like these (usually involving yet another script just chucked into the users home directory) feel awfully "hacky".

Heh, I guess that's the price of freedom though. Thanks again.

Now all I need to figure out is the mime icons issue, and my transition to 8.04 will be finalized.

---

### Post by Senesence on 2008-05-04
Still need help with the second issue.

---

### Post by begemot. on 2008-05-12
OMG!
Thank You, **noynac**, **Senesence**!
I thought this F-ing blurry font in terminal will crash my eyes!

---

### Post by durand on 2008-05-12
The mime type problem is just to do with the icon theme. Some themes don't have all the icons so they use a generic one.

---

### Post by grisou on 2008-06-08
Thanks for the solution. But the terminal font became very crisp only after I changed the value of antialias to false in the .fonts.conf file.

My font appearance preferences are monochrome rendering, no smoothing and full hinting. My monitor is an LCD.

---

### Post by vijaym on 2009-03-25
thanks that helped me

---

