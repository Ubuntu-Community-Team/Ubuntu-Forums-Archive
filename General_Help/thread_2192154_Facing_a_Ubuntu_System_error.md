---
title: "Facing a Ubuntu System error"
date: 2013-12-06
forum: General Help
---

### Post by sydney2 on 2013-12-06
Hello There, I have a Ubuntu 12.04 installed system.Everything was working well all this while until I have been facing serious errors.Firstly the System sets up quiet slowly after I log in. Secondly the default themes wont set up. After I execute palimpsest under root privileges I cannot access any folders, clicking at root / does nothing. However at the terminal a error appears:
 


    ```
(nautilus:6243): GLib-GIO-ERROR **: Settings schema 'org.gnome.nautilus.preferences' is not installed

``` 
I have gone through many of the posts online but none have helped.


Well any help provided would be greatly appreciated 


User

---

### Post by ibjsb4 on 2013-12-07
Hello sydney2

I been googling around for about a half hour (Im sure you spent way more time than this).  Got my best hits here:

[https://www.google.com/search?client=ubuntu&channel=fs&q=ubuntu+Settings+schema+%27org.gnome.nautilus.preferences%27+is+not+installed&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=ubuntu+Settings+schema+%27org.gnome.nautilus.preferences%27+is+not+installed&ie=utf-8&oe=utf-8)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Settings+schema+%27org.gnome.nautilus.preferences%27+is+not+installed&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Settings+schema+%27org.gnome.nautilus.preferences%27+is+not+installed&sa=Search&cof=FORID:9)

If I had this problem I think I would try this fix (post#9):

[https://bbs.archlinux.org/viewtopic.php?pid=926746](https://bbs.archlinux.org/viewtopic.php?pid=926746)

Since I do not have this problem and have not tried this; I really have no idea of the outcome.  So use it at your own risk.  

Something else to try.  Open a terminal and enter:

```
nautilus --check
```

Maybe that will give you some clues.

Also, I wonder if purging Nautilus would do any good (this may remove custom settings).

```
sudo apt-get remove --purge nautilus && sudo apt-get install nautilus
```

But again, this is just some more guess work on my part.

Maybe someone with a better understanding of "gschema" will come along.

Good luck

---

