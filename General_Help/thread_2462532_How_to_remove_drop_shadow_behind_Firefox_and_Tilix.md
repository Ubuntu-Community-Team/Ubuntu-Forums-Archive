---
title: "How to remove drop shadow behind Firefox and Tilix application windows?"
date: 2021-05-22
forum: General Help
---

### Post by riverhawk on 2021-05-22
Hello everyone. I am getting a drop shadow behind the application windows of both Firefox and Tilix. This doesn't happen on other applications like Zim, Chrome, Thunar, etc. I'm fairly sure this is because some applications use Qt while others use Gtk, but don't know the details on changing settings for widget toolkits.

Any pointers in the right direction would be appreciated. Thanks!

---

### Post by riverhawk on 2021-05-23
OK...solved this myself. Following this thread: [https://askubuntu.com/questions/1150373/how-do-i-control-all-window-shadows](https://askubuntu.com/questions/1150373/how-do-i-control-all-window-shadows)

Created: "~/.config/gtk-3.0/gtk.css"

Added:

```
decoration
{
    border-radius: 6px 6px 0 0;
    border-width: 0px;
    /*box-shadow: 1px 12px 12px 12px rgba(0, 0, 0, 0.4), 0 0 0 1px rgba(0, 0, 0, 0.18);*/
    box-shadow: none;
    margin: 4px;
}


decoration:backdrop
{
    border-radius: 6px 6px 0 0;
    border-width: 0px;
    /*box-shadow: 1px 12px 12px 12px rgba(0, 0, 0, 0.4), 0 0 0 1px rgba(0, 0, 0, 0.18);*/
    box-shadow: none;
    margin: 4px;
}
```

---

