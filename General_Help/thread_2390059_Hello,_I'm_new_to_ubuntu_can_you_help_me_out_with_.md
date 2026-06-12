---
title: "Hello, I'm new to ubuntu can you help me out with this?"
date: 2018-04-25
forum: General Help
---

### Post by shinjitanimura on 2018-04-25
I tried to install node.js in latest version, bash, curl and npm in the terminal after my computer was automatically locked, i cannot log in anymore and i tried to restart and this happens..
[ATTACH=CONFIG]279434[/ATTACH]

then i restarted it again and it says.

/dev/sda5: clean, 229928/7798784 files, 290213/31178496 blocks

can you help me out? Thanks

---

### Post by ajgreeny on 2018-04-25
Hello shinjitanimura, and welcome to the forums.

Your first screenshot suggests that the system crashed, perhaps  when installing that node.js, and that you carried out a hard reboot without shutting down properly.
Is that correct?

The second screenshot is simply a message that appears after boot but just before the GUI desktop system starts, telling you that the filesystem is clean; I see that every time I boot into my 16.04 and 18.04 systems but the OS continues to boot to the desktop without a problem.
Does yours eventually get to the desktop, does it move to a command line login screen, or does it go no further than the message you see?

Tell us in as much detail as you can what exactly you did when installing node.js and someone may be able to help you more.

---

### Post by VMC on 2018-04-25
shinjitanimura, do what aj suggests.
Also, I get the first message every time I do a power cycle. The reason I need to do that is system freeze. No amount of key manipulation will work. Modern FS's are very robust.

Acouple of years ago, when that second message started to appear, I too wondered what was going on.  Its with the new system messaging and control, as in journalctl and systemctl.
In fact familarize yourself with both of those commands. Here is a good cheat-sheet for the ***journalctl*** to check log results.
[https://www.cheatography.com/airlove/cheat-sheets/journalctl/](https://www.cheatography.com/airlove/cheat-sheets/journalctl/)
***systemd*** cheat-sheet
[https://xtronics.com/wiki/Systemd_Cheatsheet.html](https://xtronics.com/wiki/Systemd_Cheatsheet.html)

---

### Post by kc1di on 2018-04-25
Hello shinjitanimura  and Welcome to Ubuntu Forums, 

Could you give us as much info about your machine as possible.  Make, Model, Ram video card, Etc. 
if you can install Inxi from the command terminal ```
sudo apt install inxi
```
Then you could run this command ```
inxi -Fxz
```and post the output it would be helpful.

---

