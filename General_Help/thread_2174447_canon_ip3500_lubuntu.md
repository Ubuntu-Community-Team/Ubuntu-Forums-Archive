---
title: "canon ip3500 lubuntu"
date: 2013-09-14
forum: General Help
---

### Post by oakhollow on 2013-09-14
My newly installed lubuntu does not recognize my canon ip3500 computer. Does anyone know how to get this work? Or do I need to buy another kind of printer?

---

### Post by royph on 2013-09-14
Go to the website "iheartubuntu canon printers" (without quotes). There you will find the list of Canon drivers including Canon ip3500 that work with Ubuntu and I have also used these drivers with Lubuntu and they work on my computer at least.

When you copy and paste the first line ie: sudo add-apt-repository ppa:michael-gruz/canon you may need to add "-trunk" (again without quotes) to the end. Then copy and paste: sudo apt-get upate. When this is finished scroll down to: sudo apt-get install cnijfilter-ip3500series again copy and paste to terminal.

When this is finished connect and turn on your printer, open System Settings, click on Printers and after a few seconds your ip3500 should appear as installed.

This worked for me with an ip3600 and lubuntu so I hope it works for you as well.

Roy

---

### Post by oakhollow on 2013-09-16
What does it mean when I get this line after doing those entries?

E:Unable to locate package [COLOR=#000000]cnijfilter-ip3500series[/COLOR]

---

### Post by royph on 2013-09-16
That means it did not download the driver. Did you add -trunk after you pasted the first line in Terminal? If not, delete the download in Update Manager, Settings, Othet Software. Then try a reinstall with the -trunk command added. If you still get the error, delete the download again. Download the first two commands only, then go to Update Manager, Settings, Other Software. Look for the two lines you have downloaded, Highlight the first one add click on Edit, change the PPA from Precise to Oneiric. Now do the same thing with the second line. Go back to the website and copy and paste the package cnijfilter-ip3500series again.

One of these two solutions should make your printer work. Canon printers are not always easy to setup on Linux since Canon does not offer much help. It took me a long time to find out how to setup my ip3600 so it works and my next printer will be an Epson or HP.

---

### Post by oakhollow on 2013-09-16
Wondered if the E: had any bearing since it seemed to looking for a thumbdrive. Thanks again.

---

