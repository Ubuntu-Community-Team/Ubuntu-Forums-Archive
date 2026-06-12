---
title: "How do I add a font to Thunderbird in Lubuntu?"
date: 2015-05-10
forum: General Help
---

### Post by MarthaMyDear on 2015-05-10
I am using Lubuntu LX Panel 0.7.2 and Thunderbird 31.6.0 for email.

I would like to add a font that is not included in the Thunderbird package for when
I compose the emails I send. I have downloaded the font (gutenberg.ttf) but my computer
will not allow me to drag and drop it into the usr/share/fonts/truetype folder that one of
the tutorials suggests that I have seen on the Intgernet. My computer keeps refusing and
tells me I do not have permissions. The downloaded font is stored in my home directory
documents file folder.

Can anyone walk me through how to do this from the terminal mode? I am assuming I will
need to break through the administrative wall with "SUDO" or something like that. I am
not sure.

Help! Thanks!!

---

### Post by Frogs Hair on 2015-05-10
You could try moving the font to the desktop, run the command below and then try to drag and drop. 
```
gksudo pcmanfm
```

---

### Post by Holger_Gehrke on 2015-05-10
No need to go with full administrative privileges if you just want to install a font and don't need it to be available to all users of the system (in the latter case you would need 'sudo' ...). 
Just create a directory named '.fonts' in your home directory (the dot at the beginning of the name makes it a hidden directory, so you might need to hit ctrl-h in the file manager to see it after you've created it) and put the font in there. A few seconds later the font will be available for use.

---

### Post by MarthaMyDear on 2015-05-10
Thanks so much Frogs Hair and Holger. With
some fat-fingering I was able to get the file added
to my usr/share/fonts.truetype folder and now the font
appears in my email composition as well as Librewriter. I am
very pleaseed!

Thanks to you both for the help!!!

---

