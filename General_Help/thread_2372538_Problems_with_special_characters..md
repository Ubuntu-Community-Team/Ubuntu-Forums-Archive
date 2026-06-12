---
title: "Problems with special characters."
date: 2017-09-26
forum: General Help
---

### Post by Coto_Paxi on 2017-09-26
[INDENT]Hi,

The OS is kubuntu 17.04. The LibreOffice is Version 5.3.1.2.

When I type here the German special characters "ß", "ä", "ö", "ü", they are displayed correctly in this browser.

Also the Spanish special characters "ñ", "á", "í", "ó", "ú" are displayed correctly by this browser.

Since I ran an update I have two problems:

1)
Speical characters within a file name or within a folder name:
File names or folder names that contain any of the above characters are displayed with a "&#65533;" subsituting the special character. So the word "Búsqueda" in a file name or in a folder name is displayed as "B&#65533;squeda".

When I want open the folder: /desktop/B&#65533;squeda de Suelo JLL , I get the message: 

[FONT=Ubuntubeta][I]Unable to run the command specified. The file or folder /home/skippy/Desktop//B&#65533;squeda de Suelo JLL does not exist.
[/I][/FONT]

This means I can't open, copy move or delete any file or folder that contains any special character. 

In Properties>Permissions, I find:

[FONT=Ubuntubeta][I]Owner: Can view & modify content
Group: Forbidden
Others: Forbidden
[/I][/FONT]

From the pull-down menu I can select "can view & modify content" for Group & Others but, when I cklick "ok" I get the same error message as above.

2)
LibreOffice can't open files with a special character and within a blank application (e.g. writer) the special characters are displayed as:

"ñ" is displayed as: "[FONT=Ubuntu]Ã±"

[/FONT]"ó" is displayed as: "[FONT=Ubuntu]Ã³"

[/FONT]"é" is displayed as: "[FONT=Ubuntu]Ã©"

[/FONT]"á" is displayed as: "[FONT=Ubuntu]Ã¡" , 

[/FONT]and so on. Also the same for the German characters, always this "[FONT=Ubuntu]Ã" with an additional sign.

[/FONT]I thought it was a bug and I waited for a week before posting, because I thought an upgrade would fix it. But a couple of update did not fix it, so I am posting this problem now.

Can anyone help me to track the problem down?

Thanks very much![/INDENT]

---

### Post by TheFu on 2017-09-26
Looks like a character set issue to me.

In the meantime, use tab completion to access the files. [https://www.howtogeek.com/195207/use-tab-completion-to-type-commands-faster-on-any-operating-system/](https://www.howtogeek.com/195207/use-tab-completion-to-type-commands-faster-on-any-operating-system/) explains.

---

### Post by Coto_Paxi on 2017-09-26
Hi Fu,

Thanks for your reply!

The tab completion works in terminal, but I still get the result:

> No such file or directory

Thanks again for your help!

---

### Post by TheFu on 2017-09-26
Sorry - if tab completion works, then the filename will be filled in even if it isn't displayed correctly.  Alternatively, you can use regex matching as well.

As for correcting the UTF8 characters, you'll need to check that a correct characterset is enabled for both the console and X11. Additionally, not all file systems default to UTF8 support, fat32 for example.

---

### Post by Coto_Paxi on 2017-09-27
Hi Fu,

Thanks very much indeed again for your help. I am actually giving up and will make a re-installation of Kubuntu. I have a separate home partition and I will just re-install.

Again, thanks very much!

---

