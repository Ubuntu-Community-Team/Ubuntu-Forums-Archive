---
title: "Evolution (Edgy) lost almost all of my e-mail!"
date: 2006-10-25
forum: General Help
---

### Post by Aleksandersen on 2006-10-25
Oh no! ](*,) 

I have [lost well over five hundred e-mails](http://bonaveo.net/2006/10/edgy-real-is-kinda-edgy/)!

Any suggestions on how to recover those!?

Evolution just says that "there have been an error while syncronizing the folder(s)."

:-| I realy need those e-mail folks.

[SIZE="1"]Backup? What is that? Some kind of frog?[/SIZE]

---

### Post by tronica on 2006-10-25
you might try 

> /home/user/Evolution

I read your blog posting and would have to disagree about stability, i haven't had a bit of trouble. I think its just as stable as dapper is. Oh well just my 2cents

---

### Post by Aleksandersen on 2006-10-25
Can I convert or fix broken mbox files somehow?

---

### Post by dcstar on 2006-10-26
> **Aleksandersen said:**
> Oh no! ](*,) 

I have [lost well over five hundred e-mails](http://bonaveo.net/2006/10/edgy-real-is-kinda-edgy/)!

Any suggestions on how to recover those!?

Evolution just says that "there have been an error while syncronizing the folder(s)."

:-| I realy need those e-mail folks.

[SIZE="1"]Backup? What is that? Some kind of frog?[/SIZE]

Close Evolution, go to your (hidden) ~/.evolution/mail/local/ folder and delete any "ev-summary" files (including those in sub-folders).

Then restart Evolution (which will now re-create the deleted index files, which could take some time.....) and see if things have changed.

---

### Post by Aleksandersen on 2006-10-26
I tried to remove the ev-summary and it did not help.

Now Evolutions freezes the computer when it opens... ;(

---

### Post by skymt on 2006-10-26
> **Aleksandersen said:**
> I tried to remove the ev-summary and it did not help.

Now Evolutions freezes the computer when it opens... ;(

Just wait for it. It will take some time to rebuild the indexes, and it will probably stop responding as it does so.

---

### Post by Aleksandersen on 2006-10-26
Now I've got yet another error message saying "Error while fetching mail. Summary and folder mismaatch, even after a sync."

And another one (which I have seen before) saying "Error while storing mail. Summary and folder mismatch, even after a sync."

:confused: And can I somehow export just the mbox-files without loosing attachments or anything? So that when I import the file bak into Evolution, it whould be forced to reindex it from scratch.

---

### Post by swhit on 2006-10-26
I lost almost all of my email too. And all of my contacts. Sucks.

> **Aleksandersen said:**
> Oh no! ](*,) 

I have [lost well over five hundred e-mails](http://bonaveo.net/2006/10/edgy-real-is-kinda-edgy/)!

Any suggestions on how to recover those!?

Evolution just says that "there have been an error while syncronizing the folder(s)."

:-| I realy need those e-mail folks.

[SIZE="1"]Backup? What is that? Some kind of frog?[/SIZE]

---

### Post by Aleksandersen on 2006-10-26
I do not think I have lost them. They appear when I open Evolution at random . But I am unable to figure out how to actually restore them or to export and reimport them.

And please folks! Do not start every reply with a quotation. I see it all the time here in the Ubuntu forum. It is really annoying reading the same messages over and over agian in a thread.

---

### Post by skymt on 2006-10-26
It gets even more confusing without them. See? ;)

EDIT: It's even in an RFC:[quote=RFC 1855]If you are sending a reply to a message or a posting be sure you summarize the original at the top of the message, or include just enough text of the original to give a context.  This will make sure readers understand when they start to read your response.[/quote]

---

### Post by Aleksandersen on 2006-10-26
I just discovered that I am also unavailable to empty the trash folder. The option is greyed out.

---

### Post by Aleksandersen on 2006-10-26
I fixed it myself!

I just installed a package called "razor." It was a spam thingy for Thunderbird... One's I removed it Evolution started working again and restored all my e-mails!

---

