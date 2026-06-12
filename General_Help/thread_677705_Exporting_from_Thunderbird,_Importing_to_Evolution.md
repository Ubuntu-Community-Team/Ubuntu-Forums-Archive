---
title: "Exporting from Thunderbird, Importing to Evolution"
date: 2008-01-25
forum: General Help
---

### Post by Kourosism on 2008-01-25
I'm a relative newcomer to Linux. I've been using Ubuntu on my laptop since Gutsy came out, and had been toying with the LiveCD for about a year before that.

Now it has come to the point when I need to do something about my desktop, which is in need of a reinstall after getting clogged up with crapware by my son. I've heard great things about Fedora 8, and have considered using it for that machine. However, I really like Ubuntu, and for the sake of consistency I think I'll probably stick with it.

I currently use Thunderbird in XP, and I want to keep my emails and account settings when I transfer - any recommendations about how I may go about that? Is there a quick and easy way?

---

### Post by wjp.reg on 2008-01-25
Thunderbird will export your contacts to an LDIF file which can be directly imported into evolution.

Getting your mail is more complicated.  As thunderbird uses mbox, evolution is able to import your mail directly, but you will need to copy the mbox file which is stored under your thunderbird settings in XP and import that file.

You can find the mbox file by looking at the *local directory* settings in your email account config screen.

As far as actual email accounts, I don't think that can be imported directly, but wouldn't take much to re-create.

cheers,

---

### Post by Thanoulis on 2008-01-25
Try out Conduit...it's in the repos...

---

### Post by HP_Boehler on 2008-01-25
> **wjp.reg said:**
> 
Getting your mail is more complicated.  As thunderbird uses mbox, evolution is able to import your mail directly, but you will need to copy the mbox file which is stored under your thunderbird settings in XP and import that file.

cheers,

Hi,
Did as described but: is there a special place I have to copy the files to? It did not work for me.

Thanks

Regards

---

### Post by wjp.reg on 2008-01-25
Copy to some media and then import directly into evolution.

---

### Post by HP_Boehler on 2008-01-26
Hi,

The Evolution import tool does not ask for a place to import from. Did I miss anything?

Regards

---

### Post by dcstar on 2008-01-26
> **HP_Boehler said:**
> Hi,

The Evolution import tool does not ask for a place to import from. Did I miss anything?

Regards

You should use the "Single file" option, and then select the mbox file.

---

### Post by HP_Boehler on 2008-01-26
:)...like a charm

Thanks

---

