---
title: "Cannot open atachments in Thunderbird 1.0.2"
date: 2005-05-09
forum: General Help
---

### Post by oscarossa on 2005-05-09
Hi,
In Mandrake 10.0 + Mozilla Suite 1.6 i can to open atachment files in reiceved emails directly from Mozilla mail client. (i.e, files with .doc, .ppt extension).

In Ubuntu Hoary + Mozilla Thunderbird 1.0.2 i cannot do this.
When i tried open a word document atached to email, nothing happens.
I can see the "Open"option in atachment window, but it dont work and I must save to disk and open later.

Where can i setup Thunderbir to make this files open directly from Thunderbird to OpenOffice?

Thanks

Oscar

---

### Post by brickbat on 2005-05-09
Hi, I have exactly the same setup and mine works perfectly so this is just an idea.  In Thunderbird, go to Edit/Preferences and select Attachments.  Make sure that the "Ask me where to save" option is selected.

Now when you double click an attachment and it says "open with" you should make sure that openoffice is there.  If it isn't there or it is there and you select it but nothing happens when you click ok then you can do the following.

double click the attachment, select "open with" but instead of clicking ok, click the arrow to the right of it and select "Other".  It will bring up a file browser dialog.  Browse to /usr/bin and find openoffice.  Double click it and if this doesn't work, then I think you can be pretty sure it is a problem with your openoffice program and not Thunderbird.

In that case, a simple solution would be to installed the openoffice2 beta and go through the same procedure above but in usr/bin select ooffice2 or oowriter2.

If it works with openoffice2, then you are sure that the problem is with your openoffice setup.  If it doesn't then it would be very strange indeed. I would then suggest it would be a problem with your Gnome setup.

ciao
bb

---

### Post by oscarossa on 2005-05-11
Thank for answer but it didnt work.

When i click over a saved word file, OpenOffice opens perfectly.
The problem is that i can't open this documents when reading emails in Thunderbird.
I can do this easily in Outlook (windows 98 and XP) and in Mozilla Suite (with Mandrake 10.0)

In Thunderbird 1.0.2 + Ubuntu Hoary, i have problems.
In atachment window (below preview email window) i can see the files received, pictures, word-documents, etc.  

But nothing happen when i select one of them and push "Open".

The menu list for atachments in my Ubuntu machine only show this options:

Open
Save as..
Save all...

In Nautilus browser all files open whith their respective programs at click (jpg files with Gimp, word files with OpenOffice, etc).

My problem is thunderbird relative only.

---

### Post by derrick1985 on 2005-05-11
Check thunderbirds security settings. I know in Outlook Express, you have to say for it to download attachments, or else it just shadows them over.

Try sending the email back to yourself.

---

### Post by rosslaird on 2005-05-11
Yup, I'm having the same problem. No options for "Open with..." and no way to dynamically open attachments (I have to save them first).

The other thing is that the Attachments dialog box (in Preferences) for associating files with applications does not allow adding file extensions.

As I recall, this function worked in TB until recently.

Ross

---

