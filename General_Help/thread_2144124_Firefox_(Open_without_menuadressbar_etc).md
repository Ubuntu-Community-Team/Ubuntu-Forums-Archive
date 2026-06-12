---
title: "Firefox (Open without menu/adressbar etc????)"
date: 2013-05-11
forum: General Help
---

### Post by ztealmax on 2013-05-11
Hello im trying to make a shortcut on desktop for firefox so it opens firefox without menu/adressbar etc
why im trying this is becouse im linking it to my audio station (Music player webbased) 

so would be nice to be able to open firefox without menus, adressbar and other stuff and perhaps set size of window too

Is this possible, if so how would i go about doing this?


Sincerally
Martin aka "Ztealmax"

---

### Post by Archit88 on 2013-05-11
[http://support.mozilla.org/en-US/kb/create-desktop-shortcut-website](http://support.mozilla.org/en-US/kb/create-desktop-shortcut-website) 
this might help

---

### Post by ztealmax on 2013-05-11
thanx however didnt help ;) create shortcut on desktop i can, what i need is some commands for not showing adressbar
and menus when opening firefox

something like :\firefox notoolbar noadressbar nomenus

Thanx :)

---

### Post by 25tom on 2013-05-11
This may not be all that helpful, but you can do this with Chrome/Chromium. I think you just call the command for the browser, then an option, then your URL, for example, for Chromium:

```
chromium-browser --app=http://play.spotify.com
```

However, this doesn't really provide a solution for Firefox...

Have you tried ```
man firefox
``` and looked for options to do this in the man page?

Hope this is helpful to some extent :)

---

### Post by deadflowr on 2013-05-11
run
```
firefox --profilemanager
```

Then make new profile, save it or whatever.
Then start firefox with that profile, and customize the toolbar and stuff. 

Then make a launcher and set the exec command as
```
firefox -p profilename url
```

Having, for fun just tried this, the only thing I have is the tab, no toolbars, or addressbars.


Edit: Thinking it through, I think you should look at the application called fogger.
[https://apps.ubuntu.com/cat/applications/fogger/](https://apps.ubuntu.com/cat/applications/fogger/)
Unfortunately, it's only listed for precise.

---

