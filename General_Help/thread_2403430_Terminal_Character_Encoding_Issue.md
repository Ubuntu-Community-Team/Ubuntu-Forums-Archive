---
title: "Terminal Character Encoding Issue"
date: 2018-10-11
forum: General Help
---

### Post by asiebenwirth on 2018-10-11
Hi,

On Ubuntu 16.04 in a terminal I stream a Kazahk radio station with mplayer.

I like that mplayer shows the artist and song of the currently streaming title.
But for cyrillic letters or even Kazahk letters the characters are not displayed.

Where would have to start checking to solve this in a way that I can see the titles correctly?
Is it the encoding of the streamed data, the terminal?

Here's how it looks:

[ATTACH=CONFIG]281305[/ATTACH]

Thanks for any ideas!

---

### Post by Holger_Gehrke on 2018-10-11
It's both the stream and the terminal. Since you don't have any control of the stream, you'll have to set your terminal to match the encoding of the metadata in the stream. Set your terminal to expect 'windows 1251' encoding and it should display readable title information. In my xfce4-terminal I choose 'Terminal->Encoding->Cyrillic->WINDOWS-1251' from the menu, don't know where those settings are in your terminal.

Holger

---

