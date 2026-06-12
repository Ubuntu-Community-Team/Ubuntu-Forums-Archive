---
title: "Thunderbird 102.2.2 shows unreadable folders and message pane"
date: 2022-10-11
forum: General Help
---

### Post by Robbyx on 2022-10-11
Does anyone know the solution to this display problem as shown in picture?

Disabling all addons does not help.

---

### Post by col48 on 2022-10-12
I think this may be the answer?

Have you tried View > Density > Touch  (choice is Compact, Normal, Touch in increasing spacing)
or
View > Font Size > Increase font size

I can't reproduce your thumbnail with the overlapping text (and icons in the panel on the left) so I can't be sure.  I've got Tbird 102.2.2 in Ubuntu 22.04.

---

### Post by Robbyx on 2022-10-12
Thank you for your suggestion. Unfortunately, changing the font size only seems to effect the text in the email not the the listing on the desk top page, also density made no difference.  In case my picture is not clear, the patches which should be clear listings of folders or messages look like moth eaten carpets. Most of the text is not readable.

---

### Post by ajgreeny on 2022-10-13
Not Font size! That certainly won't help.

You need the View - Density options but if that's not the solution I begin to wonder about your overall graphics.
Do you have integrated graphics or a separate graphic card?

---

### Post by Robbyx on 2022-10-13
My integrated graphics card may not be the cause because it is showing very small text in other areas such as in Firefox when I reduce the resolution by 50%, even in TB it is showing small text outside of the two problem display locations.

I have reistalled TB but that did not correct the problem. It is very anoying because the fault  is making TB useless.

---

### Post by Robbyx on 2022-10-13
BTW in case it makes any difference to your suggested solution, the picture is not showing thumbnails. They are squashed and over written lists of emails in folders  and their detail eg date. Likewise for the folder names.

---

### Post by col48 on 2022-10-13
View>Density making no difference is puzzling.  It should space out (1) the icons on the Toolbar at the left (2) the list of folders & subfolders (3) the list of emails - all with the same vertical spacing, with Touch giving the greatest clear space between the items.  Your picture suggests Density is a fraction of Compact so that items get partially overwritten.

On your Toolbar only the 'Chat' icon is showing - mine has this as the lowest of five, the 'Mail' icon being the at the top.  Have the others been hidden by the Chat icon?  Can you open an email, and if so does it appear readably?

@ajgreeny.  A crazy question (to which the answer ought to be 'no').  If reinstalling TB made no difference, and other apps are not affected, does this suggest there is a setting hidden away from the main TB system folders which is corrupt?  Or perhaps something not being refreshed on reinstallation because of a permissions issue?  I'm just a user having opened the bonnet (US: hood!) and wondering how it all works...

---

### Post by ajgreeny on 2022-10-13
It therefore sounds as if this problem is more related to the general font settings in your Ubuntu DE but I don't have a clue how you change that if you're using the default gnome desktop.

Have a good look through system settings, wherever that is, and see if changing the font size or scaling might help.

---

### Post by col48 on 2022-10-13
This is speculative and beyond my comfort zone, but....

Settings > General
shows a screen with (in the RH panel) the first bold heading 'Thunderbird Start Page'
scrolling down to the bottom there is a button labelled 'Config Editor'

Clicking that (and then 'Show all') displays a long list of preferences and their values.  There is a search function.

The preference mail.uidensity should have a value of 0, 1 or 2 (corresponding exactly to Compact, Normal, Touch). I find that anything but 1 or 2 is gives a Compact display.
The option to delete the Preference altogether is not on offer, but perhaps yours has been, somehow.

But reinstallation should have dealt with that.

I think this may be one for Mozilla support - I can't find any clue in an internet search that anyone else has had this exact problem.

---

### Post by ajgreeny on 2022-10-13
Good catch **col48**; I didn't realise that this setting was one of the **Advanced Preferences** items, though now I think about it, of course it is; just like everything else.

I use Normal in those density settings and in the Advanced Preferences it is showing as 1 just as it should, so it will be very interesting to see what the setting is showing in **Robbyx**'s Advanced Preferences, or if it has been deleted in some manner.

@ Robbyx.
It may be worth closing T'Bird, renaming your hidden .thunderbird in your home as a backup, then starting thunderbird again. You will have to reset your email account again in order to open the application if I remember correctly, or perhaps ypu can delay doing that for now, but it may give us some clues about why your current T'Bird display is not doing what we expect.

---

