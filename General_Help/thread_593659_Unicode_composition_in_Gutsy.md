---
title: "Unicode composition in Gutsy"
date: 2007-10-27
forum: General Help
---

### Post by mhenriday on 2007-10-27
The available [[COLOR="Blue"]documentation[/COLOR]]("https://help.ubuntu.com/community/ComposeKey") on Unicode composition states the following :
> Unicode composition

Another means to enter non-keycap characters is to enter them as Unicode character number.

key Shift+Ctrl+U then enter the hexadecimal (0123456789abcde) Unicode character code point. Shift+Ctrl+U will display an underlined u, release the keys, then type the unicode value (four hex digits), then space bar.

This worked for me in **Feisty** (with the exception that «Ctrl+Shift+u» did not display an underlined «u», but rather no text at all), but after upgrading to **Gutsy**, the hexadecimal code itself is displayed on my system. Thus, «Ctrl+Shift+u»/016f/space in **Gutsy**'s text editor or in **OpenOffice** leads not to a Czech «&#367;», but instead to «016f». Has anyone else experienced the same phenomenon ? I'm running 64-bits **Gutsy** on a **HP Pavilion AMD 64 X2 5000+** box....

Henri

---

