---
title: "Text and launcher icons vanishing"
date: 2017-01-19
forum: General Help
---

### Post by antiquarian on 2017-01-19
Hello,      Hours to days after a reboot, text vanishes in some windows and parts of the desktop environment (the launcher, the top bar with the clock, and text fields like the Files tool and the Save tool).  Libreoffice and Thunderbird seem especially prone.  The window with the contents of a file or email will appear empty (except for squiggles under words which the spellchecker in Libreoffice does not like) while the search box and the text in various windows of the surrounding application appear normally.  Logging out sometimes helps, and restarting always does, but that is not exactly a *nix solution!      I have attached a screenshot of a mild case.  The sample file in Libreoffice has two lines of text, a mix of English (blank) and gibberish (the red squiggles).  The terminal has the same problem, except that it I can see text when I highlight it ... I think that the default colour of text is being set to the same one as the background.  I played around with the Profile Preferences -> Colours interface of the terminal without being able to solve the problem.      Where do I go from here to figure out what is going in?  There are these forums, Ask Ubuntu, the bug report system ... hard to know where to start.  The closest thing I can find by googling is [https://askubuntu.com/questions/759150/launcher-menubar-and-window-borders-disappeared-in-ubuntu-16-04](https://askubuntu.com/questions/759150/launcher-menubar-and-window-borders-disappeared-in-ubuntu-16-04) but that is not the same bug.      I am running Ubuntu 16.04 LTS on a Thinkpad T410.  I installed and enabled the proprietary drivers for the graphics card.  I have experienced the same bug in Gnome and Unity.  I can provide more details if needed.

---

### Post by antiquarian on 2017-01-25
I have found some possibly relevant bug reports:        
[list]    
[*]Bug #1573959 **On-screen text disappears after suspend** (April 2016) [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1573959](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1573959) "After resuming from a suspend, almost all text on screen is not visible. This includes menu items, text in all three boxes (list of folders, list of e-mails, e-mail body) in Thunderbird (with the curious exception of "ffl" in the File menu), top menu in Chromium (but not the menu obtained by pressing the hamburger button), and the menus produced by clicking items in the system tray. Also, the apport dialog had no text except for a few capital letters."    
[*]Bug #1434351 **X fonts and widgets disappear after suspend/resume cycle** (March 2015) "After a suspend/resume cycle, the screen comes up normally, but every time I move my mouse over a piece of text, button, widget, etc, the text vanishes and it's replaced by a plain rectangle." [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1434351](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1434351)    
[/list]
    What is the procedure here?  Should I register for launchpad and confirm the bug?  I am happy to contribute if someone would explain how things work in this community.  Also, this forum does not seem to accept line breaks.  It turned all the paragraphs in my first post, separated by "enter enter," into a wall of text.  Do we need to use special bbcode to mark paragraphs and line breaks on this forum?

---

### Post by antiquarian on 2017-12-14
I still have this problem.  I found a fix in an Ask Ubuntu thread which describes a different bug:  [https://askubuntu.com/questions/455301/how-to-restart-gnome-shell-after-it-became-unresponsive-freeze/963644#963644](https://askubuntu.com/questions/455301/how-to-restart-gnome-shell-after-it-became-unresponsive-freeze/963644#963644)    
[list] 
[*]Terminal: w // If you see tty7, that means F7 brings you back, if tty3 then F3 etc.  
[*]Ctrl-Alt-F1, wait as the screen turns black, Ctrl-Alt-F7 
[/list]
     The method described in that thread works for me in Gnome shell on Ubuntu 16.04 LTS.    Did I ask this question in the wrong place?

---

