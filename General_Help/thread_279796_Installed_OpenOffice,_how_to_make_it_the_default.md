---
title: "Installed OpenOffice, how to make it the default?"
date: 2006-10-18
forum: General Help
---

### Post by towsonu2003 on 2006-10-18
Using Dapper 6.06 up-to-date, I installed the latest OOo (2.0.4) from openoffice.org following [these steps]("http://www.oooforum.org/forum/viewtopic.phtml?t=26173&highlight="), which make you install any version of OOo separately under /opt as an independant package (so you can have numerous versions of OOo installed in your system). 

I changed all my launcher paths so that whenever I click on the OOo icon in the menu, it will launch OOo from /opt/openoffice/programs/soffice

I also changed how gnome handles OOo files by right clicking on OOo files and asking gnome to open them with /opt/blabla by default

Here is the problem: both thunderbird and firefox open office documents that I download using the old Ubuntu version of OOo. How do I tell them to use the new openoffice?

thanks :)

---

### Post by aysiu on 2006-10-18
In Firefox, go to Edit > Preferences > Downloads > View and Edit Actions and delete the old action. Then open a document and choose to open it with your /opt OpenOffice.

Do the same for Thunderbird.

---

### Post by towsonu2003 on 2006-10-18
> **aysiu said:**
> delete the old action

The thunderbird dialogue is empty, and firefox doesn't have openoffice entries (I'll attach the screenshot, just in case, and bc I like doing that ;) ). that's why I though there was a system wide option (a shortcut, something like update-alternatives for openoffice) I thought I could change. 

I'll go ahead with the > open a document and choose to open it with your /opt OpenOffice way then :) thanks

---

