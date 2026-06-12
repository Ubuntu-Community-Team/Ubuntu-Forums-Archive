---
title: "midnight commander"
date: 2018-09-15
forum: General Help
---

### Post by jgw on 2018-09-15
I used to be able to move files around with midnight commander.  Now, however, it seems to be a terminal emulator and nothing else.  Perhaps my memory is deluding me on this one.  When I goto help all I get is help on the terminal.

Thoughts?

---

### Post by Holger_Gehrke on 2018-09-15
How are you starting the program ? From a menu or desktop item or with 'mc' in a shell ? If the last one doesn't work, then Midnight Commander is either not installed or very badly broken. 'sudo apt install mc' (perhaps with the option '--reinstall') should fix that. If it does work from a shell but not with a graphical starter, then either the .desktop-file (/usr/share/applications/mc.desktop) is broken or you have a second desktop file in &#8217;~/.local/share/applications/' that also gives it's name as 'Midnight Commander'.

Holger

---

### Post by jgw on 2018-09-21
Thank you for the reply.

I just went to applications and entered "mc'  and two programs came up, icons were exactly the same.  One was for the mc terminal and the other was for the file manager.  I now know how to get to the file manager but I am not sure that this is right.

---

### Post by rbmorse on 2018-09-21
You're not imagining things...there are two related utilities and they both have the same icon in the program menu: mc, the midnight commander file manager, and the midnight commander editor (not sure what command evokes that from terminal).

---

### Post by Qew on 2018-09-21
> **rbmorse said:**
> You're not imagining things...there are two related utilities and they both have the same icon in the program menu: mc, the midnight commander file manager, and the midnight commander editor (not sure what command evokes that from terminal).

mcedit is the command. It's what's called when hitting F4 or Shift-F4 when on a file in Midnight Commander.

As you say, one of the mentioned icons opens mc and the other mcedit. If you're running on Gnome, then if you install the extension Application Overview Tooltip, that'll show a tooltip with additional information when using Show Applications. At leas then you'd quickly notice such differences at a glance.

---

### Post by jgw on 2018-09-22
thank you for the reply..........

I installed the extension application overview tooltip and it now tells me which is which - thanks for the tip!  I am still not sure why one is called the midnight commander editor as it behaves and looks pretty much like a terminal with options and I am not sure where the 'editor' thing comes in.  No problem, however.  I will just have to study on it.  Thanks again!!!!!!!!

Its interesting.  When I have both open at the same time they are displayed, in the dock, with a single terminal icon instead of the icons displayed in the applications.  When one goes to the 'editor' the title bar displays 'terminal'.  When one clicks on the editor icon, in applications, it takes you to ubuntu software which also says its a text editor.  When one clicks on 'files' it get you a normal black terminal screen.  When it the editor, and click on /help/about it says (all centered on display):
GNOME Terminal
3.28.2
A terminal emulator for the GNOME desktop
Using VTE version 0.52.2 +GNUTLS -PCRE2

A bit confusing but with the help I got I can deal with it.   I will mark this one as solved.

---

### Post by PaulW2U on 2018-09-22
> **jgw said:**
> I am not sure where the 'editor' thing comes in.
It sounds as if something is not right with your installation.

Screenshot of what I get when pressing F1 after invoking the editor shortcut of Midnight Commander:

---

### Post by Qew on 2018-09-22
I'll just add what happens when I click on the Midnight Commander Editor icon. As its name suggests, it's a text editor (I use it a lot).

When in mc, if you highlight a file, then press F4, it'll open up mcedit for that file, allowing you to edit it. Try with a text file to see. You can also open it up blank (as done when clicking on the icon), then if you press F9, it'll bring up the top menu bar. You can then select File from that menu bar and then Open File to choose a file to open.

Note: I use a different "skin" for mc, which is why it's not blue. Maybe you have done something similar to make it appear like a terminal window.

---

### Post by jgw on 2018-09-23
Thank you for the replies, I am almost there now.

Basically this is a new deal for me.  When I came over to ubuntu, from windows a few years ago.  I used to use an editor called vedit (for years) as a normal editor and a programming editor.  With ubuntu I have been using gedit (and, sometimes, vim).  I suspect I will have to spend some time for this one as I can see advantages.  I have also saved the icon problem with the dock - kinda.  I dragged the mc icon for the editor to the dock and it stuck.  The problem is when I open mcedit the terminal icon also shows open (kinda odd)

I think my basic problem is that my mc editor does not open with a prompt (actually I NEVER get a prompt (something like:greg@greg-down:~$)).  I must click the end of the [-M--] line to get to the editor.  After that I can just chug along.  I also found a ini file in -config/mc as 'ini' (no extension).  I do have an 'mc' file in /.local/share/  That has one folder that has something called 'filepos' which has "/home/greg/.cedit.menu 117;22;3271" in it.  There is no /home/greg/.cedit.menu    there is also a history file there.  

Below are some observations:
When in the mc editor I cannot take a picture of the screen if any drop downs are active.  The problem, here, is that there is another 'File' when the [-M] line morphs into an editor command line.
The screen of the editor/terminal has 'terminal' centered at the top, 
then the x, underline, and size box
then file, edit, view, search terminal, help
then a line with [-M--] 24 L:[  1+ 4   5/ 5] *(261 / 262b) <EOF>     (this line, when pressed, morphs into an editor command line!)

Then, when I click on the original 'File' I get:
new tab
new window
close tab
close window

If, however, I click on the [ -M-O] line and THEN click on file I get a normal file menu:
open
close
save
etc


So, when the terminal  is open I cannot take a picture of the screen (neither print screen nor screenshot)
when I am in the editor screen I can do a screenprint
I was unable to do a copy (with either a ^c or get a right click menu to copy but I could save it

---

