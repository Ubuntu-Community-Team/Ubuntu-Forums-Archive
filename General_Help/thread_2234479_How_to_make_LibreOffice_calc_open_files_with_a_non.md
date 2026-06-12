---
title: "How to make LibreOffice calc open files with a non-default theme"
date: 2014-07-15
forum: General Help
---

### Post by vasa1 on 2014-07-15
I'm using LibreOffice Calc Version: 4.2.4.2, Build ID: 420m0(Build:2) from the Software Center. I didn't install the full suite, just some of the components (and their dependencies). I'm mentioning this just in case it is relevant.

```
libreoffice-base-core
libreoffice-calc
libreoffice-common
libreoffice-core
libreoffice-gtk	
libreoffice-help-en-us
libreoffice-style-galaxy
libreoffice-style-human
libreoffice-writer
```

The space at the bottom of a spreadsheet is occupied by tabs containing the names of sheets in the workbook. The font size within each tab seems to be determined by the width of the scrollbar set in the current theme's /gtk-2.0/gtkrc.

My problem is this. I prefer very narrow scrollbars for all gtk2 applications. (The overlay scrollbars are not relevant for gtk2, AFAIK). Having narrow scrollbars mean the font size in the sheet-name tabs is too small to be legible.

A workaround is to specify a separate theme for LibreOffice Calc in which I set a broader scrollbar width as described in [How can one make firefox ignore my GTK theme entirely?]("http://askubuntu.com/a/8346").

So I've got this script which I call **scalc**:
```
#!/usr/bin/env bash

# used by Openbox right-click menu

env GTK2_RC_FILES=/usr/share/themes/Greybird/gtk-2.0/gtkrc libreoffice --calc
```

And I can run it from the terminal or by assigning a shortcut in Openbox's menu.xml.

However, this script, as it stands, only opens a blank spreadsheet. I then have to go into Recent Documents or use Ctrl+O to open a specific spreadsheet. I don't know how to make a .desktop file that would let me double-click a spreadsheet file's icon to open it with the theme specified above.

Is what I want possible and, if so, how?

**Edit**: Looks like modifying the .desktop file to have this line as described [here]("http://askubuntu.com/a/358493"), instead of the default (**Exec=libreoffice --calc %U**) works:
```
Exec=bash -c 'GTK2_RC_FILES=/usr/share/themes/Greybird/gtk-2.0/gtkrc libreoffice --calc %u'
```

---

