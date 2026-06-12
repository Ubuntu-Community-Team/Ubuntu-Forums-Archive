---
title: "Firefox vs Python and other languages"
date: 2017-05-29
forum: General Help
---

### Post by Skaperen on 2017-05-29
when i access a URL with "Content-Type: text/plain" using firefox, it displays the text just fine.  however, when the URL has "Content-Type: text/x-python" then firefox refuses to display it, giving an option to edit it with gedit or save it.  how can i get it displayed like text/plain, or at least have the option to do so?

---

### Post by ajgreeny on 2017-05-29
Have a look in the FF preferences ->Applications tab to see if there is a way to add FF to the options available for opening those filetypes.  

In my FF, python-script is one available filetype, set at present to "Always ask" but it could be set to whatever is wanted from the drop-down option box.

---

### Post by Skaperen on 2017-06-04
there was no way that i could see to add having FF do the display itself like it does for text/plain.  i am also now curious why Python is the only language listed here.

---

### Post by dragonfly41 on 2017-06-05
I'm currently adding custom mime types for my own purposes and they are found in /etc/mime.types.

Do you have .. text/x-python	py
in that file?

I can view py source in Chromium Browser using protocol .. file://<path_to_python_script>/test.py

---

### Post by Skaperen on 2017-06-09
yes, in [FONT=courier new]/etc/mime.types[/FONT] i do have "[FONT=courier new]text/x-python    py[/FONT]" and many other languages such as "[FONT=courier new]text/x-csrc c[/FONT]" but none for pike.  source does display for me using the file: protocol, but that does me no good to avoid the download step for remote servers.  i need to make it work for http: servers where i cannot change the type to [FONT=courier new]text/plain[/FONT].

---

### Post by dragonfly41 on 2017-06-10
I use Chromium Browser although on occasions I use Firefox.

Perhaps this add-on will help?

[https://addons.mozilla.org/en-us/firefox/addon/open-in-browser/](https://addons.mozilla.org/en-us/firefox/addon/open-in-browser/)

---

### Post by Skaperen on 2017-06-10
so vanilla (no plug-ins) FF can't do this.  that justifies changing them to "text/plain" at my servers.

---

