---
title: "Setup Email client and automatically print new emails"
date: 2019-01-04
forum: General Help
---

### Post by benjamin-ihrig on 2019-01-04
Hi all,

first of all Happy new Year to everyone.
Feel free to move this to a more appropriate channel. I was not sure where to post this.

What I am looking for is a solution, to setup a headless email client to automatically print incoming messages. Printing may e.g. be via CUPS. Of course this can all be done via a Desktop OS and Thunderbird or so, but I am looking for a headless variant of that, consuming much less resources.
Googled for it and found some points to start with, but mainly broken links.

The things I found so far are around fetchmail, mailx and cups.

Maybe someone has a more convenient idea?

Thanks,
Benjamin

---

### Post by slickymaster on 2019-01-04
Thread moved to **General Help** for a better fit

---

### Post by LHammonds on 2019-01-04
Can you telnet into the mail server?

Example:

```

telnet mail.mydomain.com 110
user user@mydomain.com
pass YourEmailPassword
list
quit

```

If you can, then you might be able to create a script that can output the email to a text file that can then be sent to a print queue or whatever.

You could setup one script that will show the contents of the 1st email and save that to a unique file.  To get the 1st email, type "retr 1"
Then a 2nd script could delete the 1st email...but only do this if you know the email was retrieved successfully.  To delete the 1st email, type "dele 1"

Once you can get the output to a text file, you can probably even clean up the file a bit such as deleting any repeating and unnecessary lines before printing and maybe include a custom header/footer.

LHammonds

---

### Post by benjamin-ihrig on 2019-01-04
Hi LHammonds,

telnet indeed works. Any easy way to check if there have new emails arrived? Or via a comparison to the "unique file"?

Thanks!

---

### Post by HermanAB on 2019-01-04
Email automation is best done with a program called procmail.

---

### Post by LHammonds on 2019-01-04
> **benjamin-ihrig said:**
> Any easy way to check if there have new emails arrived? Or via a comparison to the "unique file"?
As a disclaimer, I don't do this with email so don't expect that I have been through this or have any kind of "best practice" information.  This is just me making a best guess.

Now, if it were me, I would pipe to a text file what the output of your batched commands on an empty mailbox and save that output file for reference.  When you do your normal runs, compare the output of your current batched commands to that of the "empty mailbox" file.  If the files have identical text inside, then you do not need to process any mail.

LHammonds

---

### Post by HermanAB on 2019-01-04
Don't re-invent the wheel.  You will invariably end up with a square one.

Install procmail.  Read the man page.  Search google for a few examples.

---

### Post by TheFu on 2019-01-05
+50 on using procmail.  Though I would worry that dealing with non-text emails might not be much fun and someone could use it for DoS attack blowing through consumables daily.

Also, if you can get away with it, consider printing either to files with a date-timestamp or, if you must, to paper but with 2 pgs per page to save some dead trees.  A handy alias:
```
alias lp2pg='lp -d laser -o number-up=2'
```

---

### Post by SeijiSensei on 2019-01-06
A simple procmail "recipe" to print every message might look like this:

```

:0
| lpr

```

You would put this in a file called .procmailrc (notice the leading dot) in the user's home directory.  That will, I believe, only print the messages but not store them in a folder.  For that you'd need

```

:0c
! lpr

```

which makes a copy of each message, prints the copy, then delivers the original to the user's inbox.

The printed messages will have complete headers starting with Return-Path.  Any attachments will be printed as MIME-encoded text.

---

