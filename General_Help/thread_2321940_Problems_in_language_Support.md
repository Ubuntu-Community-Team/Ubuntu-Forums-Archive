---
title: "Problems in language Support"
date: 2016-04-25
forum: General Help
---

### Post by sahashinjan on 2016-04-25
I have been using Ubuntu 12.04 so far. A few days back I fresh installed Ubuntu 16.04 and started to face some issues regarding language support in web pages.
In Google page I can see boxes for two languages while in 12.04 it worked absolutely fine. Please have a look at the below screenshot.
[ATTACH=CONFIG]268620[/ATTACH]

Can you please help me solve this issue? Do I need to install anything additional? If yes, how was it running smoothly in 12.04 without having to install anything additional?

Any help will be much appreciated.

---

### Post by sahashinjan on 2016-04-26
Any help for this issue?
Why can't I see the text properly?

---

### Post by peter228 on 2016-04-27
looks like you need to install support for more languages.

Go to System Settings / Language Support then Install / Remove languages.

You need to select some more languages that are related to India so perhaps you need to select Hindi and Gujarati and any of the other local languages that you recognise.  

Once they are installed the google home page will display correctly.

---

### Post by vasa1 on 2016-04-27
By hovering over the language links, the languages seem to be 
Telegu (te): [https://www.google.co.in/setprefs?sig=0_dAgX0igK8YRJhUJyu0YxMGA4BPI%3D&hl=](https://www.google.co.in/setprefs?sig=0_dAgX0igK8YRJhUJyu0YxMGA4BPI%3D&hl=)_te_&source=homepage 
and 
Kannada (kn): [https://www.google.co.in/setprefs?sig=0_dAgX0igK8YRJhUJyu0YxMGA4BPI%3D&hl=](https://www.google.co.in/setprefs?sig=0_dAgX0igK8YRJhUJyu0YxMGA4BPI%3D&hl=)_kn_&source=homepage 

If you don't need them, you needn't worry. If you do, try what's suggested by peter228.

---

### Post by sahashinjan on 2016-04-29
Thanks I am a bit surprised because I have only "English" installed in System Settings / Language Support but still I can see the other Indian regional languages in the Google page.

Why only these two languages are not displaying?

I searched more and came to understand that some font package has to be installed to display these languages. I tried ttf-ancient-fonts but it did not help.

Can you suggest any other font package for these languages?

---

### Post by sahashinjan on 2016-04-29
Found the solution:-

In Ubuntu 12.04, ttf-indic-fonts was installed by default but in 16.04 it is not.

installed two packages fonts-knda and fonts-telu and now everything is fine...

---

