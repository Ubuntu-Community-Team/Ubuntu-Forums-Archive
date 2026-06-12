---
title: "firefox differences between OS [Resolved]"
date: 2007-03-10
forum: General Help
---

### Post by xyrer on 2007-03-10
Hi, i have noticed that firefox for windows obeys when you tell it to open all links on tabs, but in linux it doesn't, i wonder if the problem is related to firefox being aimed different or is it ubuntu?
clicking on the adress is also better on windows because it selects all, here i have to double click.

I would apreciate if anyone knows how to solve the opening of links on tabs, I don't like having a nice browser with tabs but can't use them cause it opens a lot of windows instead.

---

### Post by aysiu on 2007-03-10
about:config and [the Tab Mix Plus extension](https://addons.mozilla.org/firefox/1122/) are your friends. See the attached screenshots for more details.

Of course, I just use Control-L to select the address bar, but it sounds as if you want to change the mouse functionality.

By the way, I use Firefox in Windows at work, and I don't remember it opening all links in tabs unless I have the Tab Mix Plus extension installed...

---

### Post by xyrer on 2007-03-11
Well i was always reluctant to install tab mix i don't really know why, but now i guess i have to, thank you very much.
I wonder why the clickselect option is selected true by default in windows and it isn't in linux, anyway i will change it, I'm used to it.
Your help has been lifesaving, another thing i will not miss from Windows.

---

### Post by aysiu on 2007-03-11
The other thing I learned recently: if you click on the symbol to the left of the address, that highlights the entire address.

---

### Post by kerry_s on 2007-03-11
You can just do a google search for about:config entries and manualy set the settings. The page won't link.

---

### Post by SuSUntu on 2007-03-12
I'm with Aysiu.

Tab Mix Plus is not an accessory. It is a must have. :)

One thing that is different in Ubuntu's FireFox for sure is this security-related issue posted by Security Focus:

[http://www.securityfocus.com/bid/22899/info](http://www.securityfocus.com/bid/22899/info)

There is a proof-of-concept at the link below:

```

h t t p://people.zoy.org/~sam/firefox-crash-save-session-before-clicking.gif

```

**Do not access the above URL unless you understand that it serves as an exercise to prove the information posted by Security Focus and it may [will] crash your FireFox browser.**

I could not get it to crash FireFox 2.0.0.2 in Windows XP SP2, but it does crash version 2.0.0.2 in Edgy. 

Though this vulnerability is not particularly nasty as far as I can tell, these types of security discrepancies between the Windows versions of FireFox and the Linux versions are much more important.

---

### Post by xyrer on 2007-03-12
Well, i kind of dislike that kind of things that make firefox more usable on winbugs, I just got an e-mail announcing a response on this forum and as i have both computers with both OSes, i tried it on linux and it opened another window, in Windows it just opened on another tab, same options and same extensions on both, i think that should be fixed.
Another thing not as annoying as that one is that preferences menu, in windows is tools>options but in linux it goes edit>preferences, if this goes on the transition for users will be harder.

Thank you all for your help, I will definitely install tab mix plus although I don't seem to need it in windows, but I dont use Windows as often anyway, and have a look at all about:config options, they come handy.

---

### Post by Pikestaff on 2007-03-12
It might be Firefox version differences... correct me if I'm wrong, but before 2.0 I'm pretty sure Firefox defaulted to opening links in new windows, and now with Firefox 2.0 it defaults to opening things in new tabs.  If you are using the default Firefox that came with Ubuntu, and you're using Dapper, that might be your problem?

Either way there are extensions that will do the trick, as has been mentioned: I use Tabbrowser Preferences myself but Tab Mix Plus works too :)

---

### Post by xyrer on 2007-03-12
Hi, actually I solved it, I'm using edgy wich comes with firefox 2 but seems to have 1.5 defaults, i looked into the about:config documentation as Kerry_s sugested and found the key browser.link.open_newwindow and had 2 by default wich opens new windows, changed it to 3 and it's done, I checked and it comes in 3 by default in the windows version.

Thank you everyone, learned a lot!

---

### Post by Mark C on 2007-03-13
> **Pikestaff said:**
> It might be Firefox version differences... correct me if I'm wrong, but before 2.0 I'm pretty sure Firefox defaulted to opening links in new windows, and now with Firefox 2.0 it defaults to opening things in new tabs.  If you are using the default Firefox that came with Ubuntu, and you're using Dapper, that might be your problem?

Either way there are extensions that will do the trick, as has been mentioned: I use Tabbrowser Preferences myself but Tab Mix Plus works too :)

Hey, your Gir avatar is kind of familiar... oh wait, I remember, you have just posted on the livejournal my_desktop community... nice desktop btw.

---

