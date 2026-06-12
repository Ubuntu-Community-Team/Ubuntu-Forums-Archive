---
title: "Terminal in 14.04 not handling ctrl and shft character"
date: 2016-12-21
forum: General Help
---

### Post by Clopper Almon on 2016-12-21
I just updated the Ubuntu 14.04 system on a computer I had not used in several months. As a result, ctrl and shift keys no longer work correctly in the Terminal app. Specifically, shift+rightarrow yields a C on the screen and shift+leftarrow yields a D on the screen, while ctrl+C yields nothing but a repetition of it yields ^C and similarly ctrl+V repeated yields ^V. They do not copy and paste. 

These strokes work normally in other applications; only in Terminal do they not work. I have removed Terminal and reinstalled it from the repository without effect.

Any help would be appreciated.

---

### Post by kingneutron on 2016-12-21
--Quick check: I would recommend you try installing " xfce4-terminal " and see if it does the same thing there. If not, it's pretty much a direct replacement.

--If it's still happening after that, it may be a bug or a keyboard-mapping issue.

---

### Post by oldrocker99 on 2016-12-21
You might try SHIFT-CTRL-C; you need to use SHIFT-CTRL-V to paste in terminal.

---

### Post by Impavidus on 2016-12-22
ctrl-c is used to send a terminate signal to the running application. It will show ^C and give you a new prompt. ctrl-v is used to add the following character to the terminal input literally, allowing you to input control characters. Typing another ctrl-v will put this character, with the ascii value 0x16 "synchronous idle", on the terminal input. Terminals have always worked like that, even before people used ctrl-c and ctrl-v for copy and paste.

---

### Post by vasa1 on 2016-12-22
> **oldrocker99 said:**
> You might try SHIFT-CTRL-C; you need to use SHIFT-CTRL-V to paste in terminal.

> **Impavidus said:**
> ctrl-c is used to send a terminate signal to the running application. It will show ^C and give you a new prompt. ctrl-v is used to add the following character to the terminal input literally, allowing you to input control characters. Typing another ctrl-v will put this character, with the ascii value 0x16 "synchronous idle", on the terminal input. Terminals have always worked like that, even before people used ctrl-c and ctrl-v for copy and paste.

+1

To summarize, there's nothing wrong with your terminal!

Combinations of keys may work differently in terminals than in other applications.

Terminals, by default, work like this:
If you want to copy selected text, it's Shift+Control+C (all pressed together).
If you want to paste text from elsewhere, it's Shift+Control+V (all pressed together).

---

