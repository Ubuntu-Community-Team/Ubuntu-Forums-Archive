---
title: "Problem with Chromium browsesr"
date: 2013-12-03
forum: General Help
---

### Post by tarkawebfoot on 2013-12-03
Earned a Tumbleweed badge on AskUbuntu for this one.

[COLOR=#333333][FONT=UbuntuRegular]I'm running Xubuntu 12.04. It originally was Lubuntu 12.04, then I installed xubuntu-desktop. I'm still using Chromium as my browser because it's running on a Netbook.
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Everything works really well except for one small annoyance. I have other users who use the system now and then. When I run Chromium, it works as you would expect. When any other user runs it, Chromium starts a terminal window to show output. This is confusing for some of them.
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I've checked their /home directories and they seem identical to mine wrt Chromium (i.e. they have a.cache and all its subdirectories are the same as mine). The shortcuts all launch Chromium with the same command:[/FONT][/COLOR]
/usr/bin/X11/chromium-browser

[COLOR=#333333][FONT=UbuntuRegular]At first I thought it was just because they didn't have access to /var/log. But now I'm not so sure. It doesn't look like Chromium logs to that directory; it must log to the user's home directory, though I haven't found the output from my session yet.
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]How do I get Chromium to work the same for my other users as it does for me?[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]
Specifically, no terminal window at launch and logging to their home directories.[/FONT][/COLOR]

---

### Post by deadflowr on 2013-12-04
cache is just cache but do the users have chromium profiles.
I'm not sure where chromium keeps its users profiles, but I think it would be in ~/.config.
(per user)
I've not seen this type of behavior. well at least not isolated to specific users.
Usually something like this happens across the full board or when a user over-tweaks the settings.
I don't run Xfce/Xubuntu, so that too might have an affect. 
Nothing against xfce/xubuntu though, just something to also look at.

---

### Post by tarkawebfoot on 2013-12-04
I'd have to double check, but I don't believe this happens on regular Ubuntu which I'm running on my desktop.

I may have mistyped when posted the original message. I thought I was looking at the .config directory. I'll double check tonight.

---

### Post by tarkawebfoot on 2013-12-04
Problem solved.

The issue was the 'Run in Terminal' box was checked when I created the launcher. I don't remember checking it, but must have done so by accident, because that's not the default in Xfce.

Thanx anyway,

Brian

---

### Post by deadflowr on 2013-12-04
Good to see. Sometimes it's the little things that make you go mad.

You can mark the thread as solved by going to thread tools.

---

