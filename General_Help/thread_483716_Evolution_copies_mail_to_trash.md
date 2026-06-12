---
title: "Evolution copies mail to trash"
date: 2007-06-25
forum: General Help
---

### Post by stchman on 2007-06-25
Hello all, I am a happy Evolution user.  One minor annoyance is that everytime I send an email, move one piece of email to another folder Evolution makes a copy of that mail in the trash.

Is this normal?  How do you disable that?

Thanks.

---

### Post by rbmorse on 2007-06-25
That's not normal.  Understand that "trash" to evolution is a special place and when you delete mail or an appointment or other data it doesn't really get moved to the "trash folder"...it just gets flagged for deletion the next time you"expunge" a folder, and disappeared from sight so you don't think about it. It does get listed in the folder labeled trash so you can see what is pending if you need to, but what is actually showing is akin to a symbolic link to the real data.   

So, if evolution is creating the "deleted" link to every mail message upon arrival, something is definitely off. Look at all of your user settings, especially mail and view, for something that isn't right. Also, if you have setup any mail filtering make sure all of the filter definitions are still sane.

---

### Post by stchman on 2007-06-25
> **rbmorse said:**
> That's not normal.  Understand that "trash" to evolution is a special place and when you delete mail or an appointment or other data it doesn't really get moved to the "trash folder"...it just gets flagged for deletion the next time you"expunge" a folder, and disappeared from sight so you don't think about it. It does get listed in the folder labeled trash so you can see what is pending if you need to, but what is actually showing is akin to a symbolic link to the real data.   

So, if evolution is creating the "deleted" link to every mail message upon arrival, something is definitely off. Look at all of your user settings, especially mail and view, for something that isn't right. Also, if you have setup any mail filtering make sure all of the filter definitions are still sane.

All my filters work.  I have Evolution check 5 different email accounts.

If I delete and email it goes to the trash as expected.  If I drag an email to another it makes a copy of it in the trash.  When I empty the trash the mail that I dragged is still there.  Evolution has its quirks, but no more than any other email program.

---

### Post by rbmorse on 2007-06-25
What happens when you "expunge" the trash folder?

---

### Post by stchman on 2007-06-26
> **rbmorse said:**
> What happens when you "expunge" the trash folder?

I have not tried that.  I will and post what happens here.

Thanks

---

