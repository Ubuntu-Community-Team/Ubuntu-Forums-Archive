---
title: "Keyboard shortcut to insert text"
date: 2017-12-22
forum: General Help
---

### Post by raleigh3 on 2017-12-22
[https://askubuntu.com/questions/543968/tool-to-insert-text-snippets-into-applications](https://askubuntu.com/questions/543968/tool-to-insert-text-snippets-into-applications)

Trying to make a keyboard shortcut to paste text.

I installed xdotool and xclip.

I created the text file containing the text I want inserted in the /home/andy/.config/snippet_paste/ directory.

What key do I use to insert the text?

---

### Post by DuckHook on 2017-12-22
If you are on Artful (like way too many users are) then your default GUI environment is no longer X11 but Wayland, in which case, xdotool and xclip are unlikely to work. The solution in your link is probably obsolete for Artful.

If still using Xenial, the solution in your link should work. Read the procedure carefully. You are supposed to assign a shortcut key of your own choosing to the script.

BTW, why not use autokey? It shows up at the bottom of the thread in your link. Much easier to use because you don't have to wrestle with scripts, custom shortcuts, etc.

---

### Post by raleigh3 on 2017-12-22
I got it to work. Ctrl V inserted my text.

I tried AutoKey.

It's actually more work.

Too bad text can't be inserted into a terminal. :-)

---

### Post by DuckHook on 2017-12-22
Good to hear. If satisfied, please mark thread "solved" using thread tools at the top of this thread, so that others can benefit from your solution.

---

### Post by vasa1 on 2017-12-22
I tried Autokey on 16.04. I got the impression that it used CPU continuously. Something like the route OP went will not run continuously in the background but just when invoked.

The snippets route should work in the terminal but some characters may cause problems with Bash. If it doesn't work at all for OP, there maybe need to modify the code to accommodate his/her terminal instead of gnome-terminal.

I'm using an older version of [texpander]("https://github.com/leehblue/texpander") which is somewhat similar to the AU code. There's been a recent update to it and I'll check that out as well.

Edit: the newer version doesn't need to detect if the pasting is being done in a terminal.

---

