---
title: "Creating URL specific shortcuts/launchers on Lubuntu Desktop with their own icons"
date: 2019-03-13
forum: General Help
---

### Post by bdutta on 2019-03-13
Hi,

Would like to add some icons that correspond to Office 360 Outlook, Word, Powerpoint etc. on my Lubuntu Desktop for faster access, s.t. those URLs open with browser of my preference (Firefox).
Right clicking on Desktop doesn't show any "Create URL" type of entry, but just an Empty File. What I did try was to name the file as Outlook.sh with the following text:
```
#!/bin/sh
firefox https://outlook.office.com/mail/inbox
```
Then I changed the permission to execute. Right-clicking on it, I don't see any way to change the associated ICON (it stays same of Text file), and double-clicking on it I am prompted that this is shell-script and if I'd like to Execute it or Execute it in a terminal. I don't want to see that prompt and for it to be directly opened in Firefox (without executing it in a terminal) and for the icon to be an icon of my choice (ideally the Office360 icons). Can this be achieved ?

regards,
BD

---

### Post by Holger_Gehrke on 2019-03-13
Don't use a script, use a [.desktop-file]("https://specifications.freedesktop.org/desktop-entry-spec/latest/"). Put this
```

[Desktop Entry]
Type=Link
Name=Outlook
URL=https://outlook.office.com/mail/inbox
Icon=[COLOR=#ff0000]put-the-path-and-filename-for-your-Icon-here[/COLOR]

```
in a text file named 'outlook.desktop' on your desktop (replacing the red part with a valid path and filename) and mark the file as executable.

Holger

---

