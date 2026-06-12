---
title: "Openoffice toolbar icons appear inverted when using a dark theme"
date: 2008-02-19
forum: General Help
---

### Post by dev.urandom on 2008-02-19
as can be seen from the attached screenshot, all toolbar icons except the first one appear inverted in color. This happened only when using a dark theme. OOo somehow detects that the theme is dark, and inverts the icons. The menu icons are not inverted. The toolbar icons are not influenced by the iconset that is chosen in the options->view dialog.

does anyone know how I can stop OOo from doing that?

---

### Post by GepettoBR on 2008-04-16
Same problem here. Help?

---

### Post by calc on 2008-04-16
I think going into Tools->Options->Accessibility and uncheck "Automatically detect high contrast mode of operating system" may fix this issue for you.

---

### Post by fbuchele on 2008-05-17
Unfortunately, i did that and it didn't work for me. I also installed other themes, and none of them work. No matter what I choose, the style of icons is always inverted.

This is a most definately a bug, and rather annoying.

---

### Post by vhozard on 2008-05-17
I happens to me too. When I set my theme a little bit lighter it doesn't happen. But with a darker theme I always get the inverted icons. And the "Automatically detect high contrast mode of operating system" option does nothing to me too. Please help here.

---

### Post by redoscar3 on 2008-05-26
At least you are getting some icons.  I installed the Neutronium theme and now all my toolbar icons in OpenOffice are gone completely.  I am only getting "text" buttons for all toolbar functions.  It's not a pretty sight.

---

### Post by tamias on 2008-05-28
This is a known issue (I also use Neutronium). It was first reported about 18 months ago at [http://www.openoffice.org/issues/show_bug.cgi?id=70501](http://www.openoffice.org/issues/show_bug.cgi?id=70501)

(Taken from my [website]("http://tamias.striatus.googlepages.com/linuxtips")): OpenOffice.org suffers from a long-standing bug where dark desktop themes cause it to drop into a high contrast "accessibility" mode, thus losing all colours. The following commands will give a work-around:

```
cd /usr/lib/openoffice/program
sudo mv soffice.bin soffice2.bin
sudo mv soffice soffice2
sudo gedit soffice
```

Enter the following text into the editor and save it:

```
#!/bin/sh
env GTK2_RC_FILES=/usr/share/themes/Clearlooks/gtk-2.0/gtkrc /usr/lib/openoffice/program/soffice2 "$@"
```

Then execute ```
sudo chmod +x soffice
```

Hope this helps.

---

### Post by redoscar3 on 2008-05-30
I will give your suggestion a try.  Right now, I just decided to forget using Neutronium on my Hardy install.  There were other issues and I just decided to take the easy route and do something more conventional.  However, on my Edgy install, Neutronium generally works pretty well and your tip might even improve things some more.  I'll let you know how it turns out.

Red

---

### Post by amirman on 2008-06-14
i just wanted to add i tried the fix listed on here and it did not work for me. i'm sure it has something specifically to do with using a dark theme. i turned off the accessibility feature that mentions autodetection to no avail. the sloppy layout of the text buttons is enough to make me use abiword instead of writer.

---

