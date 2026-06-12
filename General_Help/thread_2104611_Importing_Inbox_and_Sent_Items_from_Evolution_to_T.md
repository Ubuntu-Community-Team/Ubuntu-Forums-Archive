---
title: "Importing Inbox and Sent Items from Evolution to Thunderbird"
date: 2013-01-13
forum: General Help
---

### Post by Penfold73 on 2013-01-13
I've just bought a new desktop and installed Ubuntu 12.10 on it. My old desktop has Ubuntu 12.04 with Evolution as the mail client. As Evolution is no longer supported on 12.10 I'm trying to get my Inbox and Sent Items from Evolution onto my new computer such that Thunderbird can read them. So far all the tutorials on the net say to navigate to .evolution/mail/local and copy the Inbox and Sent Items folders from there into the appropriate directory in Thunderbird. Unfortunately I only have an SQLite folders.db file there and not individual Inbox and Sent Items files. How do I get around this?

All help appreciated,

P

---

### Post by gifford on 2013-01-13
In Evolution you can export your mail as mbox and if you have added on import-export tools to Thunderbird, you can import the mbox file.

Good luck, Thunderbird is never easy to do such simple tasks.

---

### Post by howefield on 2013-01-13
Just so as you know, Evolution may not be the default email client in Ubuntu 12.10 it is still available via the Software Centre, so if it is your preference, you can still get it.

---

### Post by brusegadi on 2013-01-13
I did this a few days ago and used:

[http://ubuntuforums.org/showthread.php?t=308994](http://ubuntuforums.org/showthread.php?t=308994)[URL="http://ubuntuforums.org/showthread.php?t=308994"]
[/URL] 
It worked well.  If you have nested directories under inbox, you will need to copy the *.sbd directories too (these are nested!), try it and you will get the hang of it.  In essence, if a directory is named <blah>, there should be a file named <blah> containing the messages in the directory.  If the directory <blah> also has subdirectories, there will be a directory named <blah.sbd> containing the messages for the subdirectories as well as the *.sbd directories for any nested subdirectories. 

Since you will overwrite the thunderbird messages with the evolution messages I suggest you do the following before starting the guide above:

i) Set up the thunderbird account so that the directory structure is created.

ii) Check the email account with evolution so that the latest messages exist in evolution.  This assumes that the server is set up to not delete messages after they are downloaded.  Ensure everything is saved by logging out.  After this, do not check email with either client.

iii) Follow the guide above.  i) and ii) should ensure you do not lose messages.

If something goes wrong, you always have .evolution as a backup.

Good luck!

---

### Post by Penfold73 on 2013-01-14
Many thanks guys, I'll try and install Evolution on 12.10 as a first step. If all goes well I won't have to do anything else but if not I'll go further and try to port to Thunderbird with your suggestions.

---

