---
title: "Help with &quot;#ffff7fff0000&quot;, please!"
date: 2013-11-27
forum: General Help
---

### Post by vasa1 on 2013-11-27
I'm fiddling with [s]*~/.config/geany/geany.gtkrc*[/s] */usr/share/geany/geany.gtkrc* to get the tab text colors to my liking. But I don't understand what **#ffff7fff0000** and **#00007fff0000** are all about. Other color codes in *geany.gtkrc* are simpler:
```
#ffff66666666 = #ff6666
#ffffffffffff = #ffffff
#0000ffff0000 = #00ff00
```and I can enter the smaller ones into, for example, *gcolor2*.

---

### Post by vasa1 on 2013-11-27
I forgot I had asked about it before: [http://superuser.com/questions/463897/how-do-twelve-character-color-codes-work](http://superuser.com/questions/463897/how-do-twelve-character-color-codes-work)

---

### Post by vasa1 on 2013-11-28
Just to add that one can modify */usr/share/geany/geany.gtkrc* **or** *~/.gtkrc-2.0.mine* depending on whether changes are to be made for all users or just one.

I prefer making user-level changes. The following code makes 
the active tab's text green when any change is made and the file is not yet saved
and an inactive tab's text red when any change is made and the file is not yet saved:
```
# Custom styles

# document status colors
style "geany-document-status-changed-style" {
	fg[NORMAL] = "#00FF00"
	fg[ACTIVE] = "#FF0000"
}
widget "*.geany-document-status-changed" style "geany-document-status-changed-style"

```
Also, the 16-bit color code isn't necessary.

---

