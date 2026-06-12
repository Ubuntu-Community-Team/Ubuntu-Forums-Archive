---
title: "using parity files to check and repair rar files"
date: 2007-12-01
forum: General Help
---

### Post by alfreddo on 2007-12-01
I know how to combine .rar archives using Ark, but I'd like to run a parity check to make sure all parts are complete and undamaged before I do that.
Using Adept Manager I've downloaded and installed par2, also parchive for checking and repair of files.

If I click on the first par2 file using Windows, the whole rar set will be checked through and repairs using the par volumes will be carried out.

If I click on the first par2 file in Kubuntu, a box open up telling me the file type is unknown and inviting me to select a program to open it with. Of course par2 and parchive are not listed as options.

What do I have to do to associate the par2 files with the appropriate program?

---

### Post by xodus1 on 2007-12-01
quickpar run under wine

---

### Post by disturbed1 on 2007-12-02
This doesn't have anything to do with multimedia production ;)

par2 is a command line program. You can use it in the terminal (par2repair par2create par2verify) or get a GUI for it (pypar2 gpar2)

secondly, par2 is not the same as pararchive. Pararchive only supports V1.0 of par files, whereas par2 supports V1.x-V2.x. You don't need both installed.

---

