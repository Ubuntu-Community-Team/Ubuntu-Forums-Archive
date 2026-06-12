---
title: "firefox 3 print font size"
date: 2008-07-06
forum: General Help
---

### Post by Vivaldi Gloria on 2008-07-06
Firefox 3 uses a huge font to print. How can I decrease the printing font size?

---

### Post by Vivaldi Gloria on 2008-07-06
Or does anyone know a browser which let chainging of the print size font?

---

### Post by Vivaldi Gloria on 2008-07-07
No one?

---

### Post by the_maplebar on 2008-07-10
I was looking for a fix to this too.  I found some help on the [mozilla forums]("http://support.mozilla.com/tiki-view_forum_thread.php?locale=sk&comments_parentId=90300&forumId=1")

> 1) in the URL box (i.e. where you normally enter a web address like [http://support.mozilla.com](http://support.mozilla.com)) enter about:config and hit enter

1b) on some systems you may be prompted by a bogus warning from mozilla joking that this might affect your firefox 3 warrantee (FF is free so the warrantee is a moot point); ignore the warning and proceed.

2)a special configuration settings screen will appear in you browser window; enter the following parameter name in the 'Filter:' box: print.whileInPrintPreview

3)FF 3 will quickly search for this parameter (i.e. print.whileInPrintPreview ) and display it and it current settings in the browser window (just below the filter box).

4) Double click on this parameter to change it from FALSE to TRUE

5) now when you print preview, you should see new buttons that let you scale the print out as well as portrait and landscape buttons (just like in windows) - enjoy. 

---

### Post by Vivaldi Gloria on 2008-07-10
Thanks, it worked great.

---

### Post by BobvanderPoel on 2008-11-05
Great ... I'll never figure out why so much of this stuff is so well hidden from mere mortals :)

BTW, I tired it in thunderbird (which was also printing things for the nearly-blind) and this option works there as well. Access the config from edit>-preferences->general->config-editor.

Only problem is that in thunderbird the display in the preview doesn't update. So, select a shrink-size, cancel and then select preview again. Bit of a pain, but better than the giant printouts I was getting.

---

