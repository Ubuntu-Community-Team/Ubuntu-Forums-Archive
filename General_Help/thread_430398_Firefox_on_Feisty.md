---
title: "Firefox on Feisty"
date: 2007-05-02
forum: General Help
---

### Post by Arathorn on 2007-05-02
Is it me or doesn't Firefox work as it should on Feisty? I set it up to open links in new tabs, but Firefox keeps opening a new window. Also, backspace doesn't bring me back to the last page, but works the same as page-up. Page-up and backspace aren't that far off, so why would I need two keys for the same action? I know I could use mouse gestures to go back, but sometimes I just want to use backspace. Is there an about:config setting I should change to achieve this?

---

### Post by Arathorn on 2007-05-02
Found it:
Open in new tab not in a new window:
about:config
name: browser.link.open_newwindow
type: integer
value: 3
should do the trick, but it's stupid that Firefox doesn't do this from the preferences.

Backspace goes back a page:
about:config
name: browser.backspace_action
type: integer
value: 0
Appears to be intentional on Linux. Who made that retarded decision and why?

Source: [http://fosswire.com/2007/02/28/5-useful-firefox-tweaks/](http://fosswire.com/2007/02/28/5-useful-firefox-tweaks/)

---

### Post by grogger13 on 2007-05-02
my firefox doesn't clear search history, its freakin annoying

---

### Post by strabes on 2007-05-02
Get the "second search" extension

---

### Post by blehman419 on 2007-05-08
very nice fix to the tabbing problem.  worked like a charm.

---

### Post by rich.bradshaw on 2007-05-08
Thanks for fixing tab problem for me!

---

### Post by Jongi on 2007-05-08
Something strange about the tab issue. I use my profile across my XP, FC6, Debian and Kubuntu. I also have Tabmix Plus installed. However whenever I go into Kubuntu or Debian, it switches the option of opening a link in a new tab to a new window. Every time without fail.

---

### Post by adaniels on 2007-05-09
never mind

---

### Post by ivancamilov on 2008-05-06
Been meaning to do that for a while now... Thanks a lot, now Firefox works like I'm used to :).

---

