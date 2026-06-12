---
title: "Need to quit using Windows for business"
date: 2016-06-07
forum: General Help
---

### Post by NotWindows on 2016-06-07
What version of Ubuntu will Filemaker 11 and above work on? I absolutely hate Windows and everytime I use it there is security problems. I am stuck only using it for Filemaker and Windows. I have used Ubuntu for years without any problems at all  just need to use it also for business.

Someone Please Help! LOL

Thanks,
Kevin

---

### Post by Frogs Hair on 2016-06-07
Filemaker has a Bronze rating from wine HQ , but the test results are dated. [https://appdb.winehq.org/objectManager.php?sClass=version&iId=19727](https://appdb.winehq.org/objectManager.php?sClass=version&iId=19727)

---

### Post by QDR06VV9 on 2016-06-07
FileMaker will run under Wine. See the Wine App Database for complete detail.
[https://appdb.winehq.org/objectManager.php?sClass=version&iId=19727](https://appdb.winehq.org/objectManager.php?sClass=version&iId=19727)


There are other options that you can use in place of FileMaker. Some of your options are: LibreOffice, Kexi, Glom, and camelot. This was a couple of years back for these though.



> What works

Installs, runs and opens remote databases, if we manually add server.


What does not

After installation, we have to press "Enter" to get the prompt back again.

Application icon doesn't work. Clicking on it gives a "File not found" error. Crashes if we click where there's no field, menu or any clickable item. Clicking at some checkboxes also makes it crash. Also crashes if we click a tab which is already opened. Embedded (raster) images shown upside down. When a field is being edited, its fonts are shown upside down and are never erased. Replacing text makes old and new show at the same time. Centered text impossible to read when edited... After hitting 'Enter', field is shown correctly. Hitting 'Enter' not always exit from fields. We have to move to another field and try 'Enter' 'till it works. Sometimes the spacebar stops working and some keyboard keys become control keys, forcing us to restart the app. Refreshing views is too slow. Everytime we click on something, enter data, change tab or bring app to the foreground, it takes several seconds to redraw. List view is shown as Form view and Table view is shown as List view.


What was not tested
Creating databases and accessing local databases


Additional Comments

Recommended packages must be installed before installing Wine: [http://winezeug.googlecode.com/svn/trunk/install-wine-deps.sh](http://winezeug.googlecode.com/svn/trunk/install-wine-deps.sh) or sudo apt-get build-dep wine wine-dev
I used tools/make_requests and autoconf before compiling Wine just in case. Don't know if app would fail otherwise.
It can find remote servers automatically and crashes less often if patched and installed according to [http://www.compholio.com/wine-kane/](http://www.compholio.com/wine-kane/). It seems outdated - patches belonging in wine 1.4.0, but it's good to track in case they release patches to the latest version.


Ninja'd by Frogs hair:)

---

### Post by NotWindows on 2016-06-07
Kind of a let down! Was hoping for better results. I used to run filemaker on a earlier version of Ubuntu and seemed to work fine. I also ran old Lotus Approach.

I really don't want to go to a Linux Database because of the time I have in Filemaker setting it up for my business.

Any suggestions on this is greatly appreciated, also where is older versions stored at for Ubuntu?

---

