---
title: "Cannot enter accented characters in GNU Emacs"
date: 2020-10-01
forum: General Help
---

### Post by buisteric on 2020-10-01
Hi,
This issue persists for years without any resolution. If I start GNU Emacs from the start menu or by hitting ALT-F2 and typing emacs, the text editor cannot enter any accented character. Hitting ` followed by e just displays e, not è. Same thing for ç, ê, à, etc. The only workaround is to start Emacs with XMODIFIERS="" emacs from a terminal window. I was able to improve this workaround by putting the export XMODIFEIRS="" into my .bashrc, but that stopped working a week ago. Now the only way is to start emacs from a terminal; I cannot start it from the start menu or the ALT-F2 "Run program" box, which I'm used to do, do and redo, and have to restart Emacs from a terminal to get accented characters. I tried running sudo im-config and set the input method to none: no effect, even after restarting Ubuntu.

I am running Ubuntu 20.04 MATE with the latest updates.

There was a thread about this: [https://ubuntuforums.org/showthread.php?t=2183796](https://ubuntuforums.org/showthread.php?t=2183796). Instead of bringing a solution, somebody locked the thread so no replies can be posted anymore. This way, the problem looked to be solved but is still there. Is it because I need to get paid support for Ubuntu now, to get such issues solved? Yes, I could work around this by rebooting to Windows, but what's the point of having Linux in dual boot if I have to reboot to Windows pretty much for everything except Firefox? That kind of makes no sense.

Please don't lock the thread if it is inappropriate; remove it and tell me why. Google indexes all the threads on the forum so when people search, they find the locked threads and cannot get to a real solution, only loose time searching and reading "bump", "i have the same issue", etc.

---

### Post by tea for one on 2020-10-01
Just to satisfy my curiosity, can you try:

Press Alt Gr and Semi-colon simultaneously, release then press a

Do you get á?

Alternatively:

Scroll Lock and apostrophe (or single quote) also simultaneously, release and press a

Do you get á?

I don't know about EMACS but they work in in other applications such as Gedit, LibreOffice, Thunderbird and in this forum.

---

### Post by buisteric on 2020-12-06
Pressing Alt Gr and semicolon gives ~.
I can get a é using the / key, à using ` followed by a, ç using ] followed by c.
That works everywhere except in GNU Emacs where pressing ` followed by a gives just a instead of à, ` followed by e gives e instead of è.
Now the only workaround is to create a script named emacs, containing XMODIFIERS="" /usr/bin/emacs "$@", and put that on my PATH making sure this starts instead of the regular Emacs command.

---

### Post by Holger_Gehrke on 2020-12-06
There's [this page]("https://www.emacswiki.org/emacs/DeadKeys") in the Emacs Wiki that describes the problem and three separate workarounds. The 'XMODIFIERS=""' in ~/.bashrc not working when you start emacs from the menu or the Alt-F2 starter is to be expected, since in neither case is there a shell involved. You could either try to set XMODIFIERS in /etc/environment, but this might not work if whatever input-method you're running gets started after the setup of the environment. Or you could change the desktop file for emacs to have 'Exec=env -u XMODIFIERS /usr/bin/emacs %F' instead of 'Exec=/usr/bin/emacs %F', which will make emacs work from the menu. When starting it from ALT-F2 you'd need to enter that complete command (starting with 'env').

By the way, on my system (XUbuntu, German locale and keyboard) dead keys in emacs works just fine with 'run_im none' in '~/.xinputrc'.

Holger

---

### Post by Impavidus on 2020-12-07
I don't use emacs myself. I know that there are many ways to enter accented characters and we all have our favourite method. Mine is the compose key, as it keeps characters like ` ~ ' " ^ easily accessible by not turning them into dead keys and doesn't require me to memorise non-obvious key combination for rarely needed characters.

It may help if you told us about your keyboard layout.

---

