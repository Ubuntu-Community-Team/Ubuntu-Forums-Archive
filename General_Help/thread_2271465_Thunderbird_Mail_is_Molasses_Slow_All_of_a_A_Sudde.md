---
title: "Thunderbird Mail is Molasses Slow All of a A Sudden."
date: 2015-03-30
forum: General Help
---

### Post by wbee on 2015-03-30
Hello,

I'm running 12.04 Ubuntu and Thunderbird Mail connected to gmail by means of IMAP. All the storage is in gmail's system.

After working perfectly for a long time,suddenly,this morning,Thunderbird Mail is really,really slow.  Everything works,but everything is really slow,like seven minutes to load and display a handful of overnight emails. Selecting one,reading it,and deleting it are the same stories;the functions work,but slowly.

I manually opened my gmail account without using the Thunderbird and it displayed two unread emails. I closed that and opened Thunderbird and as I said above,it took seven minutes to download,but it downloaded nine emails,including the two mentioned previously.

--Should I wait to see if this is a gmail problem? If it still persists after a while,is there a quick fix I should know about?(Yes,I have the debugging port open and permission granted;I'm not using any firewalls or virus software. With the mail download from gmail to Thunderbird,I was using less than twenty percent of memory and no swap at all.)

--If I go into the synaptic manager,delete the present Thunderbird and download it again,will that process retain my address book?


-----------

Thank you.

---

### Post by SeijiSensei on 2015-03-30
All your Thunderbird settings are contained in the "hidden" directory $HOME/.thunderbird. You'll see another directory with a name consisting of a string of characters followed by .default.  That's where your profile is stored.

You can export your address book by clicking on Tools > Address Book > Tools.

One thing you can try before reinstalling is seeing whether starting over with a new empty profile helps.  Close Thunderbird, rename .thunderbird to .thunderbird.old, then reopen the program.  Recreate your account with the wizard.  It will probably take a few minutes to resynchronize with the server, especially if you have a lot of folders containing lots of messages.  If that improves T-Bird's performance, import your saved address book.

---

### Post by wbee on 2015-03-30
Thanks.

I appreciate the information,now knowing something I did not know before.

Since it's working now,I'm assuming it was a gmail burp,and will mark it solved.

---

### Post by gifford on 2015-03-30
Yes, it was a Google issue and now should be corrected.

---

