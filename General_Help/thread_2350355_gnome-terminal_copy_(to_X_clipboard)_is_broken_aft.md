---
title: "gnome-terminal copy (to X clipboard) is broken after updating to Ubuntu 16"
date: 2017-01-23
forum: General Help
---

### Post by uigrad on 2017-01-23
I used to be able to copy text to the X clipboard by simply selecting it with my mouse.    This still works for most of my applications (Firefox for example), but it no longer works with gnome-terminal!  I looked through all the preferences for gnome-terminal, and didn't see anything that would turn on or off copying to the X clipboard.  What am I missing?

---

### Post by Habitual on 2017-01-24
"updating to Ubuntu 16"? Similar thread at the LM forums recently...

---

### Post by uigrad on 2017-01-25
I haven't gotten any useful answers yet, so I did some looking into how to view your settings for gnome-terminal.  Here's what I found:  

```


$ dconf dump /org/gnome/terminal/legacy/profiles:/:b1dcc9dd-5262-4d8d-a863-c897e6d979b9/
[/]
foreground-color='#000000000000'
visible-name='Default'
palette=['#2E2E34343636', '#CCCC00000000', '#4E4E9A9A0606', '#C4C4A0A00000', '#34346565A4A4', '#757550507B7B', '#060698209A9A', '#D3D3D7D7CFCF', '#555557575353', '#EFEF29292929', '#8A8AE2E23434', '#FCFCE9E94F4F', '#72729F9FCFCF', '#ADAD7F7FA8A8', '#3434E2E2E2E2', '#EEEEEEEEECEC']
use-transparent-background=true
use-theme-transparency=false
scrollback-unlimited=true
bold-color='#000000000000'
background-color='#FFFFFFFFDDDD'
background-transparency-percent=-95
scrollback-lines=8192
xxxx@xxxxxxxxx:~/dev/temp


```

It looks like everything I have there is pretty standard.  Why isn't the clipboard being updated when I select text from the terminal?

---

