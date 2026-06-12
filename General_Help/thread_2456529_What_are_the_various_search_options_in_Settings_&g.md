---
title: "What are the various search options in Settings &gt; Search (Ubuntu 20.04)?"
date: 2021-01-13
forum: General Help
---

### Post by Paddy Landau on 2021-01-13
I'm using Ubuntu 20.04, which currently has Gnome 3.36.8.

In Settings > Search, there are several options as shown in the screenshot, which apply to the search that comes up when accessing Activities or Show Applications.

[ATTACH=CONFIG]287737[/ATTACH]

I've worked out most of the options, but I can't figure out two of them.

[LIST]
[*]Files: Search for files whose names contain the search string
[*]Calculator: Display the results of a calculation, e.g. 7 * sqrt 5
[*]Calendar: Search your linked calendar
[*]Characters: Display the character and its unicode for the search string, e.g. numero
[*]Passwords and Keys: ?
[*]Software: Search for software whose name or description contains the search string
[*]Terminal: ?
[/LIST]
As you can see, the two that I don't understand are "Passwords and Keys" and "Terminal". What do they mean when searching?

---

### Post by TheFu on 2021-01-13
[https://itsfoss.com/ubuntu-keyring/](https://itsfoss.com/ubuntu-keyring/) is a guess.
Maybe the window title for every terminal? IDK.

---

### Post by Paddy Landau on 2021-01-13
> **TheFu said:**
> [https://itsfoss.com/ubuntu-keyring/](https://itsfoss.com/ubuntu-keyring/) is a guess.
So, Seahorse? That seems like a good guess, because the icon matches.

So, I tried searching for the various keys that are in Seahorse, and it found nothing.
> **TheFu said:**
> Maybe the window title for every terminal? IDK.
My terminal windows are all just called "Terminal". I know that gnome-terminal used to allow you to tailor the title, but not with the current version.

Anyway, I tried searching for "Terminal", and naturally it showed me the open terminal window — no surprise there, as this happens with any app.

I had tried searching for terminal commands, e.g. rsync and ls, but they drew a blank as well.

It's quite puzzling!

---

### Post by dragonfly41 on 2021-01-13
I don't use that search feature [but does this explain]("https://help.ubuntu.com/stable/ubuntu-help/gs-use-system-search.html.en#:~:text=Open%20the%20Activities%20overview%20by,will%20appear%20as%20you%20type.")?

---

### Post by TheFu on 2021-01-13
Maybe use a better terminal program - like one that allows changing the window title?  I know xterm does.
but this is all just guesses.  My WM provides a list of all windows that I can search/pick or just use wmctl or xdotool to search.

If it isn't obvious, I don't use most of the built-in tools on any Ubuntu systems. I like that Ubuntu decided to allow "minimal" installs. That drastically reduces the bloat for stuff I'll never use.

---

