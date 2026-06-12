---
title: "mutt problems"
date: 2007-01-22
forum: General Help
---

### Post by maliy on 2007-01-22
Hi,

I used before and want to install it to my ubuntu dapper 6.10 again but i got some problems.

I mistakenly delete the /var/mail/john file and then mutt gave 
"/var/mail/john there is no such a file or directory errno=2" error.

So, I read some tutorial and did the below:

touch /var/mail/john
chown john:john /var/mail/john
chmod 600 /var/mail/john

After doing this mutt stoped crying about the errno=2. Also fetchmail works perfectly.
mutt shows new mails /var/mail/john however  mutt can not remove N flag from  the new mails therefore could not move mails to my local folder(~/mail).

I guess the problem is releated to permissions of the /var/mail/john file.

Any idea?

---

### Post by djf_jeff on 2007-01-22
Here the mail file is like this :

john:mail 660 /var/mail/john

So :

chown john:mail /var/mail/john
chmod 660 /var/mail/john

---

### Post by maliy on 2007-01-23
I did the things that u said but still mutt put N to all mail although i read them.

my ubuntu does not have mail as a user group.

Everything works fine for root so the problem is definitely about permissions

---

### Post by djf_jeff on 2007-01-23
Do you have the :

[SIZE=-1]set mark_old=no[/SIZE]

configuration option set?

I really don't know beside that.

---

### Post by andrew.46 on 2007-07-02
Hi,

 Rather than try to fix the problem why not bypass it and tell mutt you have a new mail spool. For example:

set spoolfile = $HOME/.newspoolfile

  And change your MTAs / MDAs to reflect this.

                   Andrew

---

