---
title: "firefox not starting"
date: 2007-10-02
forum: General Help
---

### Post by maduranga on 2007-10-02
i removed and then installed firefox and ubufox n xubuntu and now when i clicked on firefox icon nothing happens. I check in package manager, both of them are installed. any idea to fix it?

---

### Post by Seisen on 2007-10-02
Try running firefox the terminal like this

```
firefox
```

---

### Post by maduranga on 2007-10-02
> **Seisen said:**
> Try running firefox the terminal like this

```
firefox
```


I tried that, when i gave the comand it gave the following output in terminal:

[B] (gecko:5182): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Calibri 12'
Segmentation fault (core dumped)[/B]

---

### Post by vinutux on 2007-10-02
delete the ff preferences from u r home directory

for this open home directory and navigate  --->/home/[COLOR="Red"]u r username[/COLOR]/.mozilla/firefox in nautilus 

delete everything on there[bakeup it if u have need u r bookmarks and history]

strart ff now....................may be help u    i think..........:guitar:

---

### Post by maduranga on 2007-10-02
I got it working by deleting that. I have my bookmarks synchronized with foxmarks so its ok. Thanks.... :)

---

### Post by Seisen on 2007-10-02
That is why I recommended running firefox in the terminal because it something was causing the problem the error will usually show up in the terminal.

---

### Post by maduranga on 2007-10-02
> **Seisen said:**
> That is why I recommended running firefox in the terminal because it something was causing the problem the error will usually show up in the terminal.

 :guitar: thaks alot, now it works perfectly expect a font problem. even the this forums pages are not being rendering perfectly. text in the quoted areas are blurred, not clear. fonts are too small, but when I press Ctrl and + together and increase the fonts size, I don't get enough text fitted on the screen (amount of text fit in the screen become decreased) anyone have an idea about that? :confused:

---

### Post by dwasifar on 2007-10-02
> **maduranga said:**
> :guitar: thaks alot, now it works perfectly expect a font problem. even the this forums pages are not being rendering perfectly. text in the quoted areas are blurred, not clear. fonts are too small, but when I press Ctrl and + together and increase the fonts size, I don't get enough text fitted on the screen (amount of text fit in the screen become decreased) anyone have an idea about that? :confused:

In Firefox: pull down Edit, choose Preferences, select Content, then in the Fonts & Colors area, click Advanced and increase the value for Minimum Font Size.

---

