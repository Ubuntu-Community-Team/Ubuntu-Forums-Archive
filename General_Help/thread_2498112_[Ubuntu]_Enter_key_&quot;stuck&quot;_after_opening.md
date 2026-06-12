---
title: "[Ubuntu] Enter key &quot;stuck&quot; after opening application after 24.04"
date: 2024-05-31
forum: General Help
---

### Post by hinough on 2024-05-31
After upgrading to 24.04 LTS I'm experiencing what can best be described as the enter key being held down when opening applications from the app launcher.
This is experienced as the enter key being held down in whatever application was active before opening the new application (In terminal that would be a spam of blank commands being fired, or a bunch of new lines in a text editor).
Checking with evtest reveals the enter key not being held down at all (It fires value 1 and 0 as it should for key down and up, but not value 2 for key held down).

I'm verifying that my keyboard is working as it should on other PCs, and it was also working on the same PC I'm now experiencing this issue with prior to installing 24.04 LTS (Was then running 23.10).
I have since tried with and without solaar installed (Used it to pair keyboard and mouse on the same bolt receiver), and clean installed 24.04 on the PC (Did this since I was on a install upgraded from 23.10)

evtest shows that the keydown and keyup event on enter is fired as it should when the bug occurs, but the terminal just spams blank lines. As compared to actually holding a key down (In this case left control) where value 2 will be spammed.
(See attached screendumps)

As mentioned this was an issue that occured after upgrading to 24.04 LTS from 23.10
Any suggestions? Where do I look to see what actually happens? It does not seem to be any specific application or action that triggers it, but it seems to happen more frequently on applications that does not immediately open and respond

---

### Post by thenglong on 2024-06-03
Face the same issue.

---

### Post by dragonfly41 on 2024-06-03
I am still on 22.04 letting you pathfinders blaze the trail.
 
Wild hunch: Install Input Remapper and inspect keys (launch through evtest). which shows input-remapper keyboard)

---

