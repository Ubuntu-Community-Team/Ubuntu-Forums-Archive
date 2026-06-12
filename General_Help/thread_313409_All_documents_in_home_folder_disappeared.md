---
title: "All documents in home folder disappeared"
date: 2006-12-06
forum: General Help
---

### Post by mozkaynak on 2006-12-06
Hello,
I use Ubuntu dappler drake at office and I have windows at home.
But most of the time I use vncultra to get connected to my computer in the office. Till last weekend, I did not have any problem and I had pretty quick connection. However, last saturday night when I was creating a document in lyx and suddenly Ubuntu became responseless. It did not freeze however I could not open up anything. on sunday I restarted the computer and my desktop was empty. There was nothing on that. Then I noticed that my root directory was full. I found some recommendation in the forum and applied them then now. And i disabled some services such as mail fethcher, computer activity logger, action scheduler.
Today I noticed that I did not lose only my desktop but all files except lyx. I LOST MAY MAIL FOLDER which is my main concern. I used to use pine and downloding all my mails to that machine.

1 day before this happened I had installed a few backup programs to play around and decide on a good backup system. But I dont think this messed up my system.

I would appreciate any help. This situation is really frustrating because I lost all my emails and some literature research that I use in my research.

---

### Post by ingo on 2006-12-06
have you tried
> sudo updatedb
followed by 
> locate NAME_OF_A_LOST_FILE
perhaps they got shunted somewhere unexpected...

---

### Post by mozkaynak on 2006-12-06
when I try 

sudo updatedb

it gives the following error:
updatedb: fatal error: The temp file '/var/lib/slocate/slocate.db.stf' already e                                             xists and does not appear to be a valid slocate database. Please remove before c                                             reating the database.

I am completely lost at this point.

---

### Post by ingo on 2006-12-06
Well, it appears to have probs with the existing database. How are you on space? Have you managed to free any since your first post?

If so, rename the old database and then create the new one. Any questions just ask...

---

### Post by mozkaynak on 2006-12-06
well i did the following (after copying the file)

sudo updatedb
locate ~/mozkaynak/mail

nothing happened :(

any other/further idea?

---

