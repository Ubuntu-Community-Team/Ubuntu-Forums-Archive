---
title: "automating firefox navigation"
date: 2019-11-13
forum: General Help
---

### Post by Skaperen on 2019-11-13
there is a website i have legal access to (paid account using https and password) that i want to navigate through and print some full (whole page, not just what is currently seen) pages from.  so i am interested in tools that can drive GUI applications and/or specifically firefox.

i am quite accustomed to automating around command line programs, including difficult programs that directly open /dev/tty to read passwords (probably to prevent users from piping them in).  but, i am totally lost in the GUI world, which is very obviously, even more focused human interaction.  but when i have a list of 400+ pages i want to make a pdf from, GUI gets to be quite tiresome and even painful.  does anyone working with Ubuntu know about ways to do this, even if it involves something like running X under VNC?

i know many GUI apps can take keyboard input and act on that.  but i don't even know how to automatically feed keyboard input to an X application.  i have seen apps that take certain input only by keyboard (text entry form elements) as well as apps that take certain input only by mouse (draw a path on a map).  i have no clue how to do either, although it seems like a highly modified VNC client might be able to do that.

who can build a programmed psychiatric counsellor that operate through a video chat site and understand the other person's speech?  i've heard that someone once pitted two of these programs against each other.  i don't want to go that far, but knowing the tools involved would be interesting to me.

---

### Post by vanadium on 2019-11-13
xdotool can simulate keypresses and mouse clicks, and could therefore be used for scripts that mimicks interactions of a user with a GUI.

---

### Post by vetmawd on 2019-11-13
Check out iMacros. If that's not enough you probably want to go straight for Selenium. Both of those tools can make screenshots so that should suit your requirement.

---

### Post by dragonfly41 on 2019-11-13
I use [Actiona]("https://wiki.actiona.tools/doku.php?id=:en:start") on a regular basis to automate GUI actions.
There are other tools such as selenium driver and Sikuli but I find Actiona suits my needs.
Create and test your automation in the GUI and then run the script using the command

actexec myscript.ascr

In fact there is some overlap with xdotools (which like other apps can also be invoked through an Actiona command widget).


[Further thoughts]
Reading your specific requirement to navigate through 400+ pages you could install Zotero standalone and Zotero connector for Firefox browser.

Next create a new Collection for the corpus of pages you wish to crawl and print.
With your Collection highlighted for each page that you view you can click on the Zotero connector button to add to your Collection.  Your Collection viewed in Zotero standalone will increase.
You can keep the Collection private or share with others.
Zotero has a number of plugins to explore to add functionality.  It is designed for librarians.
You can then apply scripting to your Collection to dump reports and create custom outputs such as aggregated content.

You could also apply Actiona script to automate Zotero.

[zotero]("https://www.zotero.org/")

---

