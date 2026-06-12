---
title: "Impossible to import contacts from outlook.com (Hotmail) into Thunderbird"
date: 2014-10-19
forum: General Help
---

### Post by kazakore on 2014-10-19
And I do mean impossible!!

Why? Because the number of fields checked by Thunderbird runs out before you get to the useful information from the .csv provided by Hotmail!!

IE. This is the first "contact" containing field names as per the export from Hotmail.

"Title","First Name","Middle Name","Last Name","Suffix","Given Name Yomi","Family Name Yomi","Home Street","Home City","Home State","Home Postal Code","Home Country","Company","Department","Job Title","Office Location","Business Street","Business City","Business State","Business Postal Code","Business Country","Other Street","Other City","Other State","Other Postal Code","Other Country","Assistant's Phone","Business Fax","Business Phone","Business Phone 2","Callback","Car Phone","Company Main Phone","Home Fax","Home Phone","Home Phone 2","ISDN","Mobile Phone","Other Fax","Other Phone","Pager","Primary Phone","Radio Phone","TTY/TDD Phone","Telex","Anniversary","Birthday","E-mail Address","E-mail Type","E-mail 2 Address","E-mail 2 Type","E-mail 3 Address","E-mail 3 Type","Notes","Spouse","Web Page"

If you check at Import then the very last field is ISDN. (Almost) Everything that might be of use to me (Mobile Number and EMAIL especially!!) fall after this field, and thus there is absolutely no attempt to import it!!!


Now I should probably report this at least to the Mozilla forum, if not on their bug tracker, but I don't have an account and it seems to be about the most popular email client so sure plenty of you may use it and know the situation. EG has it been fixed in an upstream version 14.04 wont see? Or is there a tool I can use to easily convert my exported .csv to remove say some address fields and bring the ones I want further up the list so that they'll be imported??

Rather annoying!! But then again I expect nothing less from Hotmail/Outlook/M$!! ;)

(On that note can anybody recommend a decent webmail? Something small and based on something reasonably light, such as Squirrelmail, would be ideal.)

---

### Post by rbmorse on 2014-10-19
This has been the case for at least ten years (why I swore off MS Outlook, which, in turn, led me to Linux).  It was easier to switch than fight.

---

### Post by kazakore on 2014-10-20
There's gotta be a simple app for editing out the fields of the .csv file pretty easy, no?? Yeah M$ suck!! But everybody, including all my work contacts, know my Hotmail address so changing that is too much work!!!

---

### Post by amanchesterman on 2014-10-20
I don't keep contacts in my Hotmail account so I've never tried what you are attempting. But reading your post, I don't understand what prevents you from editing the Hotmail .csv file before you import it in to Thunderbird. The advice given on the T'Bird forum says:
1) Export your Hotmail contacts and save as a .csv file using a spreadsheet, which you have obviously done;
2) Create a single contact in T'Bird and export that as a .csv file, to understand the format of the T'Bird record structure;
3) Using a spreadsheet, edit the Hotmail contacts .csv to match the T'Bird format;
4) Import the edited contacts .csv into T'Bird.
That seems straightforward to me: what is impossible about it? Or are you saying that it's a lot of work, rather than actually not possible?

---

### Post by nerdtron on 2014-10-20
> **kazakore said:**
> **There's gotta be a simple app for editing out the fields of the .csv file pretty easy, no??** Yeah M$ suck!! But everybody, including all my work contacts, know my Hotmail address so changing that is too much work!!!

Actually there is! Open the csv file in Excel or Libre Office Calc. Each comma will correspond to a column upon importing so it's just a matter of selecting the column and delete it. Save again and you're done.

I also remember using a website before, I upload my csv from outlook, then it converted to Thunderbird format. Forgot it now though.

---

