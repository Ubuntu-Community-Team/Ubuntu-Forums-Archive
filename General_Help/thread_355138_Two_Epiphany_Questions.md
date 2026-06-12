---
title: "Two Epiphany Questions"
date: 2007-02-06
forum: General Help
---

### Post by crimesaucer on 2007-02-06
Hello, I'm trying Epiphany right now, and I can't find info on an easy way of setting my "tabs bar" to always show. Should I make a new string in about:config or add something to /.gconf/apps/epiphany/general 

I saw a post on google with the similar question and it said there was a "key" (string of code?) in there that would say, "always_show_tabs_bar."

When I read through the %gconf.xml, I did not see a line of code with "always_show_tabs_bar.
" in it.

My second question is about the Epiphany (Gnome footprint) spinner. I would like to remove it completely from the toolbars, is that possible? It doesn't really serve a purpose except to show a window is loading.

Or is there a way to change the image or the background image? 

The problem is that I use a gradient box fill to create a gradient image in my toolbars. I have it written in my gtkrc, and want to keep it for my theme, but the background of the "spinner" uses this gradient box fill sideways (like my drop down menus), while my toolbars use the gradient box fills regularly( top to bottom and bottom to top). This makes it very ugly. So to be able to remove the spinner, or change the background would be cool.

---

### Post by 23meg on 2007-02-06
> Hello, I'm trying Epiphany right now, and I can't find info on an easy way of setting my "tabs bar" to always show. Should I make a new string in about:config or add something to /.gconf/apps/epiphany/general

I saw a post on google with the similar question and it said there was a "key" (string of code?) in there that would say, "always_show_tabs_bar."

When I read through the %gconf.xml, I did not see a line of code with "always_show_tabs_bar.
" in it.Type "gconf-editor" to launch the configuration editor. The key you should check is /apps/epiphany/general/always_show_tabs_bar.

---

### Post by crimesaucer on 2007-02-06
I'm sorry, I'm not sure where you mean for me to type it. I'm still very new to xubuntu.

---

### Post by 23meg on 2007-02-06
Click the XFCE menu, choose "Terminal" and type it in there.

[IMG]http://psychocats.net/ubuntu/images/terminalxfce.png[/IMG]

---

### Post by crimesaucer on 2007-02-06
I had tried it in Terminal and in the address bar, this is what my terminal said:

```
blah@blah-blah:~$ gconf-editor
bash: gconf-editor: command not found
blah@blah-blah:~$ sudo gconf-editor
Password:
sudo: gconf-editor: command not found
blah@blah-blah:~$ 

```

---

### Post by crimesaucer on 2007-02-06
edited to help anyone confused like me*

I'm sorry, I didn't know that you needed an additional package called "gconf-editor" from synaptic, I thought I would be able to just write a string in a file somewhere. I guess the package gconf-editor makes it real easy like a registry key in Windows.

Anyway thanks.

So does anybody know how to remove the spinner from the righthand side of the tool bar?

---

### Post by raul_ on 2007-02-06
Actually he didn't. What is your desktop environment?

---

### Post by crimesaucer on 2007-02-06
I use xubuntu edgy with Beryl AiGLX. I re-edited the top post to explain it better to a beginner like me.

---

### Post by raul_ on 2007-02-06
Oh. Then i really don't know because gconf means "Gnome configuration" and Gnome isn't Xfce (sorry, i don't use it so i don't know). But 23meg should know it better than me. About the spinner, I don't know how to remove it but there is an extension that moves it to the menubar, so it gets really tiny and clean. You can download the extension here 

[http://www.sstuhr.dk/epiphany-extensions/]("http://www.sstuhr.dk/epiphany-extensions/")

---

### Post by crimesaucer on 2007-02-06
Thanks, and I guess I should of looked up what the gconf-editor was before whining about it. I just thought that it was something I already had installed from my xubuntu-desktop, not something different. It seems like a really cool way to customize apps though, and it fixed my tab bar problem.

xubuntu and ubuntu are still new to me so sometimes I need a little more explaining on some things that seem simple.

---

### Post by crimesaucer on 2007-02-06
Hey raul_, how do you go about installing that script?

edit- oops, I think I found the instructions.

---

### Post by raul_ on 2007-02-06
> Installation Guide

Download the .py and .ephy-extension files for the extension you want to install, and move them to ~/.gnome2/epiphany/extensions/

;)

EDIT: i posted a little late

---

### Post by crimesaucer on 2007-02-06
this is what I was trying to fix:

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-59b-1.png[/IMG]

---

### Post by crimesaucer on 2007-02-06
Totally fixed it perfectly thank you!

---

