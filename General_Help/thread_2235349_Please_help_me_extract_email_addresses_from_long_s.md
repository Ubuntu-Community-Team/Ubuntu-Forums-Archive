---
title: "Please help me extract email addresses from long string of text."
date: 2014-07-20
forum: General Help
---

### Post by Bobby_James on 2014-07-20
Hello,

If I have lines and lines and lines of text like:

John*Brown aaa My Contacts ::: a* [email]whatever@gmail.com[/email] &&&***

How can I delete everything and leave the [email]whatever@gmail.com[/email]

I know you use sed, awk, tr, etc but I'm lost as to the precise usage.

Any ideas?

---

### Post by steeldriver on 2014-07-20
How robust do you need it to be? there are lots of quick'n'dirty ways of matching somthing *like* an email - but [there is no simple regular expression for this problem]("http://stackoverflow.com/a/201378")

Also your title says 'extract' but in the body of the post you say 'delete' - which do you want to do, exactly (a grep-like extraction, or a sed-like replacement)?

---

### Post by SeijiSensei on 2014-07-21
If the data are arranged in columns, I'd just read it into a spreadsheet like LibreOffice Calc.  Tell Calc to use space as the field delimiter.  You should end up with a column of email addresses.

There are lots of times using Unix tools like sed and awk are the best solution, but sometimes it's just easier to use something like a spreadsheet.

---

### Post by |{urse on 2014-07-21
I second the hint above me, I've tried building regular expressions to do this sort of thing and they fail every time, use a spreadsheet, calc is great.

---

