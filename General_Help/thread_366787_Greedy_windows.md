---
title: "Greedy windows"
date: 2007-02-21
forum: General Help
---

### Post by mrmonday on 2007-02-21
Hi everyone,

I use Ubuntu 6.10 and was wondering if there was a way to stop greedy windows. I'll explain. 

I use gaim for instant messaging, which I have set to ask me for my passwords when it loads. The problem is my friends chat straight away, so whilst I am typing the password for another account, the chat window is brought to the front. This makes me end up typing my password in the chat window, hitting enter and sending my friends my passwords. 

Is there a way to stop windows coming to the front?

Thanks.

---

### Post by dtruesdale on 2007-02-21
Yep go into your pref/settings for gaim and tell it not to auto chat windows I forget specifically since i use kopete.

---

### Post by mrmonday on 2007-02-21
Help... I have seen the auto chat feature somewhere before, but now I can't find it.

---

### Post by hotani on 2007-02-21
This is a system-wide problem, sometimes called "stealing focus", and is fixed in Feisty.

Some examples: you'll be typing a document in open office when someone IMs you. The IM window jumps to the front causing you to finish your thought in the text box instead of your document. Or, you'll be working in something and the update manager steals focus 2 or 3 times during its run. 

In Feisty, all is well. Instead of jumping to the top, windows will just flash in the panel. :)

---

### Post by mrmonday on 2007-02-23
Is there a fix currently though?

Can I edit a file - preferably so just GAIM can't steal focus?

Thanks.

---

### Post by hotani on 2007-02-23
On one of my Edgy machines I just changed the "Hide new conversations" option to "Never", next time I get an IM I'll find out if that does anything or not.

---

### Post by hotani on 2007-02-26
That works! 

It doesn't pop up in front of everything like before. Instead, the GAIM icon flashes indicating a new message. When you click on it, the IM window shows up.

---

### Post by hotani on 2007-03-02
Oh, this is not good. I seem to have spoken (typed?) too soon. The steeling focus problem is still present in Feisty afterall. If I run synaptic, or update manager then go to another window, it still steals focus away every time it updates the screen.

For example: open synaptic and install something. While it is downloading, go to another window. When the download completes and the install begins, it will steal focus away from what you are doing to push the "installing software" window to the front. 

:(

(but the GAIM fix posted above still works, so at least there's that.)

---

### Post by finferflu on 2007-03-02
If you use beryl, you can adjust the stealing focus prevention in the main section of the general menu. I guess you shold set it to Exteme if focus stealing annoys you...

---

### Post by hotani on 2007-03-02
Good to know, thanks!

EDIT: no go. :(

Extreme is too extreme, even windows spawned by the app you are working with go to the background
Normal still allows apps other than the one you are working in to steal focus, and High does the same.

---

