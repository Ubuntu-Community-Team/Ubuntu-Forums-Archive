---
title: "FIrefox linked to Thunderbird &amp; Thunderbird linked to Firefox"
date: 2007-09-12
forum: General Help
---

### Post by sqlpython on 2007-09-12
I noted that Rui Pais
[http://ubuntuforums.org/showthread.php?t=502651&highlight=thunderbird](http://ubuntuforums.org/showthread.php?t=502651&highlight=thunderbird)
gave an explanation of editing the Thunderbird about:config to make mail links open in Firefox rather then Konqueror
 I thought I would post the complete circle so the two apps completely interact.

1. In Firefox's Location (URL) Bar, enter "about:config" and then press <enter> or click "Go".
2. With the cursor in the body of the resulting page, <right> the mouse.
3. From the pop-up menu, select "New".
4. From the next pop-up menu, select "String".
5. In the pop-up dialog box "Enter preference name", enter "network.protocol-handler.app.mailto" (without quotes), and click "OK" (You might wish to cut-and-paste that phrase to ensure correct spelling).
6. In the pop-up dialog box "? network.protocol-handler.app.mailto", enter "/usr/bin/mozilla-thunderbird" without quotes 
In my case the line entered looked like this.........
network.protocol-handler.app.mailto /usr/bin/mozilla-thunderbird
Without restarting Firefox, you can test by opening or switching to another tab. from the Firefox top menu select, "File -> Send Link". Your desired email client should open. 

To config thunderdird to use firefox for it's links:
In Thunderbird
Edit->Preferences
then go:
Advanced->General

Click on 'Config Editor' and on editor check for a key:
network.protocol-handler.app.http
(you can make it if it doesn't exist) RIghtClick on the Config Editor Background and
As with Firefox
1. From the pop-up menu, select "New".
2. From the next pop-up menu, select "String".
3. In the pop-up dialog box "Enter preference name", enter "network.protocol-handler.app.http" No Quotes
4. In the pop-up dialog box ?"network.protocol-handler.app.http" enter /usr/bin/mozilla-thunderbird
and OK finish

Now Firefox Opens Email links to a Thunderbird email composer and Thunderbird opens URL links w/ Firefox..
Bye Konqueror..FileManagers are for managing files..

---

### Post by ppedrok on 2007-11-06
Thanks, that helped me! But step 4 in Thunderbird should enter: /usr/bin/firefox.
Cfr. thread 502651

---

### Post by checho4 on 2007-11-14
Perfect!  Thanks so much!!!

---

### Post by mastergunner on 2007-12-17
...

---

