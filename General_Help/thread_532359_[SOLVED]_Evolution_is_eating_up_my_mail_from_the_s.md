---
title: "[SOLVED] Evolution is eating up my mail from the server"
date: 2007-08-22
forum: General Help
---

### Post by Chymera on 2007-08-22
Is there any way to get evo to retrieve my mail fom the server without having it disappear at the same time (ie. log in via the browser and still see ma mail on the yahoo page)

---

### Post by jamvegan on 2007-08-23
It's been a long time since I used Evolution, so I can't give you detailed step-by-step instructions, but you want to find and check the option "Leave messages on server", somewhere in your server preferences.

Hope this helps.  If not, I'm sure that someone who actually uses Evolution will read this thread before too long and give you more detailed instructions. :)

---

### Post by PaulFr on 2007-08-23
In Evolution, Select **Edit -> Preferences** menu item. Then in the dialog that comes up, select **Mail Accounts** on the left hand side (if not already selected). Select the account for which you want to leave the mail on the server, then click the **Edit** button. Select the **Receiving Options** tab. The **Leave Messages on Server** option is on this tab, as is the option **Delete after 7 days**.

1. If you want to delete messages from your web browser only and not from Evolution, then just select the **Leave Messages on Server**.
2. If you want the messages to remain on the Yahoo mail server, but be deleted by Evolution after 7 days, select both the **Leave Messages on Server** and **Delete after 7 days** options.

---

### Post by Chymera on 2007-08-23
10x a lot

do you also know how i could add spellcheck for other languages than english in evo?

---

### Post by PaulFr on 2007-08-23
1. Use **Synaptic Package Manager** and search for **aspell** (I assume you have the universe repository enabled).
2. Pick the language dictionaries *(like aspell-sv for Swedish)* you wish to install and mark for installation.
3. Then click the Apply button to actually install these dictionaries.
4. Now _close and restart_ Evolution. In the **Edit -> Preferences** menu, select **Composer Preferences** and then the **Spell Checking** tab.
You can now enable the appropriate dictionaries that you want to use for spell checking.


.

---

### Post by Chymera on 2007-08-24
great, but how can i select only one language at a time?

---

### Post by PaulFr on 2007-08-24
When you compose a message for sending, select **Edit -> Current Languages** menu in the Compose window and select the language(s) you are going to use. Then **Check Spelling (F7)** will use the language dictonaries as per your selection(s).

---

### Post by Chymera on 2007-08-25
ok, worked like a charm, 10x....

---

