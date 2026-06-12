---
title: "firefox acts weird with links launched from external app in new tab"
date: 2005-04-15
forum: General Help
---

### Post by lespedeza on 2005-04-15
This is a strange problem I´ve been trying to figure out and I´d appreciate any help.  Maybe it´s something simple that I´m overlooking and I apologize if it is.

Alright, I prefer links to be opened in a new tab in the most recent window.  The problem is that when I choose this option, Firefox acts weird.  For example, if I click a URL from Kontact the link opens fine in a new tab, but a new Firefox instance shows up in the Taskbar and the firefox icon shows up underneath my mouse cursor.  This continues even after the new page has loaded.  

This behavior does not occur if I have the option checked for URLs to open in a new window instead of a new tab.

I´ve searched these forums and the mozilla forums and really didn´t come up with anything.  The only thing that might be related is writing a script for other applications to call to force firefox to launch that URL in a new tab.  Is that what I need to do?  Or does anyone else have any other suggestions?  I´m going to try that, but I was wondering if anyone had any hints.

Thanks.

Jimmy

lespedeza at yahoo dot com

btw, I´m running kubuntu 5.04 with firefox 1.0.2

---

### Post by kassetra on 2005-04-16
[QUOTE=lespedeza]
Alright, I prefer links to be opened in a new tab in the most recent window. The problem is that when I choose this option, Firefox acts weird. For example, if I click a URL from Kontact the link opens fine in a new tab, but a new Firefox instance shows up in the Taskbar and the firefox icon shows up underneath my mouse cursor. This continues even after the new page has loaded. 

This behavior does not occur if I have the option checked for URLs to open in a new window instead of a new tab.
[/QUOTE]

Sounds like you need an extension installed.  Firefox is opening things in the new tab, but it isn't understanding that you want it in "single-window" mode...

The extension is "[Quick Tab Pref Toggle Settings]("https://addons.update.mozilla.org/extensions/moreinfo.php?application=firefox&category=Tabbed%20Browsing&numpg=10&id=353")"

---

### Post by lespedeza on 2005-04-17
Kassetra

Thanks for the reply and the suggestion.  I tried out that extension and others with all the different options and I'm still getting the same response.  When I click a link from an external app, the link will open up in a new tab in the most recent window, but at the same time it seems that another instance (a whole new firefox window) tries to open as well, but never opens (i.e., it shows up in the taskbar and the firefox icon shows up underneath the mouse cursor).  The icon and the entry in the task bar remain for at least ten seconds well after the page is loaded in the new tab and then just go away.  I'm not sure what's causing this or what might fix this.  It's kind of annoying though.  Any other ideas?

Thanks.

Jimmy

---

