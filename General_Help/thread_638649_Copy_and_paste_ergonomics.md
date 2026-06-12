---
title: "Copy and paste ergonomics"
date: 2007-12-12
forum: General Help
---

### Post by barrkel on 2007-12-12
I observe that GNOME running on X on Linux has at least two separate clipboards:

[LIST]
[*] Mouse buffer: copy by selection, paste by middle mouse press
[*] Application clipboard: Ctrl+C or Ctrl+Ins to copy, Ctrl+X or Shift+Delete to cut, Ctrl+V or Shift+Ins to paste
[/LIST]

The mouse buffer is what I've always thought of as the clipboard on Linux, ever since the days of gpm on a Linux tty (no X installed much less running), and I always rejected it because it didn't support a very common operation: careful replacement of text with the buffer's contents. By this I mean selecting the text you want to replace and then invoking paste. This operation performed using the mouse buffer clobbers the buffer and duplicates the text to be replaced, rendering it pretty pointless.

The application clipboard works the way I desire, i.e. like Windows.

The problem comes when mixing the two operations, such as selecting from terminal consoles. So, here's the canonical example, and the actual question I'm looking for an answer to:

How does one browse to a location that one has just copied from a terminal window (via the mouse buffer) for rxvt as the terminal and Firefox as the browser?

Clicking in the location bar doesn't auto-select the text like it does in Windows, so one can't simply paste and thereby replace the old url. And selecting the text to delete it first, aside from being inefficient, clobbers the content of the mouse buffer.

So, what's the best way?

[I use rxvt because that's the terminal I use in Windows: bash on rxvt on Cygwin. It's kept me sane all these years.]

-- Barry

---

### Post by HermanAB on 2007-12-12
Click and Ctrl-z will usually erase the address box in an application, after which you can middle click.

---

### Post by barrkel on 2007-12-13
Pretty awkward to type Ctrl+Z in concert with using the mouse though, given that I use a Dvorak layout (Z is the key to the left of the right shift button).

I'll give it a go and see how things work out.

---

### Post by mcduck on 2007-12-13
For Firefox, you can just configure it to select the whole address whrn clicking on the address bar. Just like it behaves on Windows.

Type 'about:config' in the address bar, then use 'urlbar' as filter to find a key called 'browser.urlbar.clickSelectsAll', right-click it and select 'toggle' from the menu to change the key's value to 'true'.

---

