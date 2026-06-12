---
title: "No &quot;Open with....&quot; button when downloading .zip file with Firefox 2.0"
date: 2006-11-02
forum: General Help
---

### Post by pricorp on 2006-11-02
When downloading a .zip file with Firefox 2.0 on Edgy, a dialog box with the button "Cancel" or "Save file" appears. However, the button "Open with..." doesn't appear. What shall I do to have the "Open with..." button ?

[IMG]http://www.snapdrive.net/public/14675/Screenshot-Opening.zip.png[/IMG]

Note that the "Open with..." appears when downloading a .tar.gz file. I use "Archive manager" to open both .tar.gz and .zip files.

Thanks,

---

### Post by Polygon on 2006-11-02
i would suggest that you would go to edit > prefs > download > click the button that says view/ edit actions, but when i do that with ff 1.5.0.7 it doesnt list zip files.... but if you can somehow add .zip to the list, you can then specifiy what program opens it.

---

### Post by pricorp on 2006-11-02
Thanks for your answer, however there isn't any view/edit action button on ff 2.0. Moreover, the "open with..." button appeared on Dapper with ff 1.5. It just disappeared after I upgraded to Edgy.

---

### Post by pricorp on 2006-11-02
It isn't an issue with Edgy but with Firefox 2.0.
I found a workaround here:
[http://forums.mozillazine.org/viewtopic.php?t=458336&postdays=0&postorder=asc&postsperpage=15&start=30]("http://forums.mozillazine.org/viewtopic.php?t=458336&postdays=0&postorder=asc&postsperpage=15&start=30")
In Edgy, the file that need to be edited is:
/usr/lib/firefox/components/nsHelperAppDlg.js
HTH

---

