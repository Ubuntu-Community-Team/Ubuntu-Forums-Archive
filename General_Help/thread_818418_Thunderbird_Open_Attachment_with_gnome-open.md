---
title: "Thunderbird Open Attachment with gnome-open"
date: 2008-06-04
forum: General Help
---

### Post by nelfer on 2008-06-04
Is there a way to tell Thunderbird to open all attachments with gnome-open?

I receive a lot of emails from people who's Mime Type for the attachments is wrong. This either leaves Thunderbird unable to open the attachment at all or suggesting to open it with a different application.

However, if I download that attachment and then use gnome-open, nautilus will use whatever application I have setup for it.

I did something similar when I was using kmail and other email clients (by actually going to the source and modifying it), but I was wondering if there was an extension to just tell it: Open everything with [ enter path of program here]

I seen some extensions, that while useful to some degree, will be a pain to setup and every time a new type of file is sent, I have to do it again (like the openbyextension). To me it is redundant to setup that in Thunderbird, when nautilus already has those settings. Have one program to handle all file attachments.

Remember, adding an action not always work, for example if the mime type is something 'generic' and the 'do this automatically' checkbox will not be enabled.

So I want to take the responsibility from Thunderbird and pass it go gnome-open. Also, I would like to skip the whole "Do you want to open or save" question when I double click on an attachment.

I tried with the advanced options, setting the browser.helper.neverAsk.openFile to the full path of gnome-open, but still, I get asked the question and it picks a program out of nowhere (For example I received a file with extension CSV and offered me to open it with 'less')

If you know of any hack or extension that will allow me to tell Thunderbird "Open all attachments with gnome-open" I'll really appreciate it. Or if you know how to program extensions, it'll be great to make one like that. It will help also in kubuntu, as they can select konqueror to open all attachments.

Thank you very much in advance.
Nelson

---

### Post by Webstyler on 2009-06-26
Hi,

recently I developed an addon for thunderbird doing exactly this job.
[https://addons.mozilla.org/en-US/thunderbird/addon/12523]("https://addons.mozilla.org/en-US/thunderbird/addon/12523")

Have fun with it.

---

### Post by fishears on 2009-10-06
Please can you make this work with 3.0pre? I'm having to save all my attachments before opening them - its driving me nuts.
Thank you

---

### Post by nelfer on 2009-10-28
Thank you very much! It works great!

---

### Post by Aearenda on 2010-05-07
It's working with TB3 in Lucid for me too. Thanks!

---

### Post by locutus42 on 2010-06-12
> **Webstyler said:**
> Hi,

recently I developed an addon for thunderbird doing exactly this job.
[https://addons.mozilla.org/en-US/thunderbird/addon/12523]("https://addons.mozilla.org/en-US/thunderbird/addon/12523")

Have fun with it.

could you PLEASE port this to KDE?  I can not believe the update from Thunderbird 2 to version 3 resulted in no mime type associations and the open dialog doesn't give a choice of associating an application.

I found an addon openattachmentbyextension but I can't ask users to type /usr/lib/openoffice/program/xxxxxx or "go find the acroread program". And I've spent over 2 hours researching this with two computers showing different dialogs after upgrades to 10.04 running KDE. Help me Obi-Wan Kenobi, you're my only hope.

---

### Post by LewisTM on 2010-07-02
You can also use the ViewSourceWith extension for Thunderbird. Then add a new event calling /usr/bin/kde-open (or xdg-open, or gnome-open) to open attachments with the right mouse button.

Cheers!

---

