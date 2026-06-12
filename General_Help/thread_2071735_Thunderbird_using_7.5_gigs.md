---
title: "Thunderbird using 7.5 gigs"
date: 2012-10-16
forum: General Help
---

### Post by Blackwolf_Oz on 2012-10-16
469 items, totalling 7.5 GB...I have compacted all folders......I have a 120GB ssd...this is taking valuable space... I have removed all sent emails....compacted everything, removed trash..... ideas?

Please!

---

### Post by pompel9 on 2012-10-16
How many e-mails do you keep?

I have a total of 3000 e-mails, and my thunderbird folder is not even a GB. And I haven't compressed the folders.

---

### Post by Karlchen on 2012-10-16
Hello, legend1264.

You may use the disk usage analyzer **baobab**. Navigate to your Thunderbird profile folder, $HOME/.thunderbird, and have **baobab** analyze which subfolder occupies how much disk space. 
This should put you on the right track.
In order to see the content of a particular folder, you may then use Nautilus or Gnome Commander or Krusader, whichever you prefer.

Kind regards,
Karl

---

### Post by Blackwolf_Oz on 2012-10-16
> **Karlchen said:**
> Hello, legend1264.

You may use the disk usage analyzer **baobab**. Navigate to your Thunderbird profile folder, $HOME/.thunderbird, and have **baobab** analyze which subfolder occupies how much disk space. 
This should put you on the right track.
In order to see the content of a particular folder, you may then use Nautilus or Gnome Commander or Krusader, whichever you prefer.

Kind regards,
Karl

Thanks...I hardly have any emails.....that I know of...

/home/blackwolf/.thunderbird/j96qdzot.default/ImapMail/imap.googlemail.com/[Gmail].sbd / [COLOR="Red"]All Mail[/COLOR]

 is 6.7 GB (6,652,788,088 bytes) :confused:   just a huge text file...safe to delete or will that bork everything?

---

### Post by pompel9 on 2012-10-16
I think that textfile is all the e-mails you have in your folders. I can be mistaken about this.

Do you have many e-mails with attachments? Like big images or PDF files.

---

### Post by oldfred on 2012-10-16
I moved all my data to separate data partitions on my rotating drive. I also moved both my Thunderbird & Firefox profiles to my data partition. 

I did this when first booting both XP & Ubuntu and my wife wanted to check Internet (with bookmarks) or email and I was trying to learn Ubuntu. Rebooting all the time was a hassle. So using same profiles eliminated the reboots.

I regularly houseclean large email and deleted emails, then run a script to run the sqlite vacuum and reindex commands on every db file.

new 
[http://kb.mozillazine.org/Moving_your_profile_folder](http://kb.mozillazine.org/Moving_your_profile_folder)
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

Same thing for Thunderbird:
sqlite3 $HOME/.mozilla/firefox/yourprofile/places.sqlite "vacuum"

---

### Post by Blackwolf_Oz on 2012-10-17
I thought hard....yes it hurt....thought, whats the point...I'll just log into Google account & check emails!

Removed Thunderbird....

Solved

---

