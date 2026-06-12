---
title: "Is it just me or the clipboard on Ubuntu has some issues?"
date: 2006-08-14
forum: General Help
---

### Post by zugu on 2006-08-14
Let's say I copy some text from a Wikipedia article in Firefox and want to paste it then into Gedit. It works as intended, EXCEPT for when I close Firefox before pasting the clipboard content.

Do I need to say this is true for any other applications?

As everything on Linux was carefully thought before being implemented, I'm sure there's a rationale for this design abomination to exist.

Anyone care to tell me what this rationale is?

---

### Post by Ziox on 2006-08-14
> **zugu said:**
> Let's say I copy some text from a Wikipedia article in Firefox and want to paste it then into Gedit. It works as intended, EXCEPT for when I close Firefox before pasting the clipboard content.

Do I need to say this is true for any other applications?

As everything on Linux was carefully thought before being implemented, I'm sure there's a rationale for this design abomination to exist.

Anyone care to tell me what this rationale is?

are you using hight-middle click or ctrl-c + ctrl-v? I know that for the middle click to work, you have to keep the text highlighted in order for you to paste it somewhere.  But i'm not sure about ctrl-c/v.

---

### Post by zugu on 2006-08-14
I tried everythink: Ctrl+C/Ctrl+V, Copy/Paste from the context menu, middle click... nothing works as long as the application the clipboard content was copied from has been closed.

---

### Post by Gustav on 2006-08-14
This is how it works in gnome. I think that it works as you want it to in KDE though.

---

### Post by vijirajan on 2006-08-14
> **zugu said:**
> Let's say I copy some text from a Wikipedia article in Firefox and want to paste it then into Gedit. It works as intended, EXCEPT for when I close Firefox before pasting the clipboard content.

Do I need to say this is true for any other applications?

As everything on Linux was carefully thought before being implemented, I'm sure there's a rationale for this design abomination to exist.

Anyone care to tell me what this rationale is?

I've seen this happening only with FireFox so far.

---

### Post by yopnono on 2006-08-14
> **zugu said:**
> Let's say I copy some text from a Wikipedia article in Firefox and want to paste it then into Gedit. It works as intended, EXCEPT for when I close Firefox before pasting the clipboard content.

Do I need to say this is true for any other applications?

As everything on Linux was carefully thought before being implemented, I'm sure there's a rationale for this design abomination to exist.

Anyone care to tell me what this rationale is?

Yep. The clipboard manager in gnome is really bad, when it comes to this.
Here is windows much better. The clipboard manager should catch everything, and keep it in the mem even if the application is closed.

---

### Post by kaamos on 2006-08-14
> Yep. The clipboard manager in gnome is really bad, when it comes to this.

Have you actually **installed** the clipboard manager? By default an applications data from the clipboard is removed when the app is closed. This is a security feature in X and ubuntu ships with it. See [http://ubuntuguide.org/wiki/Dapper#How_to_install_Clipboard_Daemon_for_GNOME](http://ubuntuguide.org/wiki/Dapper#How_to_install_Clipboard_Daemon_for_GNOME) if you want windows-like behaviour.

---

### Post by yopnono on 2006-08-14
> **kaamos said:**
> Have you actually **installed** the clipboard manager? By default an applications data from the clipboard is removed when the app is closed. This is a security feature in X and ubuntu ships with it. See [http://ubuntuguide.org/wiki/Dapper#How_to_install_Clipboard_Daemon_for_GNOME](http://ubuntuguide.org/wiki/Dapper#How_to_install_Clipboard_Daemon_for_GNOME) if you want windows-like behaviour.

No I did know that is was an extra clipboard manager. I just used the one in dapper. And this builtin one paste & copy from (all that I have tried) applications except FX, TB.

And now I have tried this one you provided and... it's the same. It don't save the data from FX or TB.
( copy text in firefox - close FX - open gedit try to paste = nothing to paste )
Thanks anyway, for pointing this out to me. (about the clipboard)

---

### Post by zugu on 2006-08-15
I also installed the clipboard manager and it's not working either.
So I guess there's nothing one can do to to get this basic functionality working in Ubuntu.
@Gustav: no, this is how it should work everywhere. I really don't care if the GNOME developers want to make somehing to work different from KDE. Some things are better just the way they are. Basic functionality should not be sacrificed just because someone's ambitions.

---

### Post by yopnono on 2006-08-15
> **zugu said:**
> I also installed the clipboard manager and it's not working either.
So I guess there's nothing one can do to to get this basic functionality working in Ubuntu.
@Gustav: no, this is how it should work everywhere. I really don't care if the GNOME developers want to make somehing to work different from KDE. Some things are better just the way they are. Basic functionality should not be sacrificed just because someone's ambitions.

Well we do have this klipper/clipper application for gnome/kde, but...
that's not how it should work. It should be transparent, like in MS.

Then it could be nice to also have an option like klipper/clipper, where you can open the clipboard and select older entrys. And not only the last one used.

---

