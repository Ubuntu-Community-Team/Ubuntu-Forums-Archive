---
title: "Clearing history in gnome-search-tool"
date: 2007-06-24
forum: General Help
---

### Post by sra136 on 2007-06-24
How do you clear the search history in gnome-search-tool?

---

### Post by sra136 on 2007-06-25
Does anybody have an answer to my question?

---

### Post by Shazaam on 2007-06-25
panel-Places-Recent Documents?
A good guide for Ubuntu cleanup--  [http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

---

### Post by sra136 on 2007-06-25
When I go to search for files.  The pull down menu lists all the searches I have made.  How do I clear that?

---

### Post by rtimai on 2007-12-01
I had a number of misspelled file searches that were driving me crazy too. Took a lot of detective work, but the following worked in Ubuntu 7.10 Gutsy.

Clear the gnome-search-tool drop-down history

Open the Terminal and copy-paste the code string below.

Code:
gedit ~/.gconf/apps/gnome-settings/gnome-search-tool/%gconf.xml

Remove unwanted search strings between <li type="string">
and their matching </li>

Press Ctrl+S to save the changes. Quit Gedit. Restart the Gnome session. 

The history list was retained if I opened the Search for Files window immediately after editing the %gconf.xml file. The change took place only after restarting the session. Logging out and back on may also re-initialize the gnome-settings, but I haven't tested that. 

Also please be mindful that there appear to be several "%gconf.xml" files in different locations with different contents. Editing the wrong file may break the gnome-search tool. Also, I'm a relatively new user and not familiar with files that start with "%" (the percent symbol.) The "%" metacharacter is supposed to have a special significance to BASH (the shell.) If you prefer to navigate to the file in Nautilus, be sure to turn on Show Hidden Files in the View options, or enter Ctrl+H. 

Intermediate users might create a shortcut (oops, symlink) to this file with the above command. Hopefully, someone will create a tool to automate clearing this drop-down history.

Please post feedback here. I'd be interested to know other user results.

---

