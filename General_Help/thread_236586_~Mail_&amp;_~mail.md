---
title: "~/Mail &amp; ~/mail"
date: 2006-08-15
forum: General Help
---

### Post by calx on 2006-08-15
I use mutt which stores mail in ~/mail, and it works fine. But when I login I get the MOTD and then "No mail." Even when mutt shows new mail.. I also have another folder called ~/Mail which the "mail" program is obviously checking on login, how can I redirect this?

---

### Post by hopstah on 2006-08-15
no guarantees that it will work for this specific problem, but what often works is creating symbolic links

```
 ln -s (target) (link name)
```

so to get something to be redirected to ~/Mail when it accesses ~/mail, you would use ```
 ln -s /home/username/Mail /home/username/mail 
```

do a little reading on the ln command ```
man ln
``` to be more familiar with it.  it's WAY better than the lousy shortcuts that windows uses.

---

### Post by calx on 2006-08-15
I was hoping it would be something like that, but unfortunately it didnt seem to work in this case. Thanks anyway **hopstah**!

I guess what im asking is how do you reconfigure "mail" so that it looks in the ~/mail folder instead of ~/Mail

---

### Post by cssutto on 2006-08-15
I don't know how your system works and I my brain is numb right now, but I have been through this in the last week as I am a convert to mutt.

On my system, I use fetchmail to get the mail.  All it does it get the mail.

It (oversimplified non tech explanation) turns it over to procmail who decides where it goes, in what folders, etc.

So you need, if your system is like mine, a file called .procmailrc.
Note the period at the head of it.

Create the file with the text editor, enter into it something like:

#Default parameters for procmail


# what is the default place to store mail   
MAILDIR=/var/mail
DEFAULT=$LOGNAME

# keep a log
LOGFILE=/var/log/procmail.log    

Substitute whatever you have named your personal folder in /home for "claude69694".

Then save the file in that named folder.

You create the log file the same way and put it in /var/log.

Your system may not be like mine, but I think you need .procmail regardless.

The set up above will store all new mail in /var/mail

You also need to create a file /var/mail/whatever your personal folder name as above......mine is /var/mail/claude69694

Then there is that file .muttrc

You have to enter stuff in it like:

set realname            = "Claude Sutton"
    set from                = "claudesutton@cognisurf.com"
    set use_from            = yes
    set envelope_from       = yes

    set spoolfile           = /var/mail/claude69694
set timeout=60
# specify where the read messages, sent messages  and the postponed
    # messages are kept.
    set folder              = ~/Mail	
    set postponed           = postponed
    set mbox                = mbox
    set record              = sent
    mailboxes /var/mail/claude69694 /var/mail/family /var/mail/trash  /var/mail/saved

The last line lists the various mailboxes I have.

There are other lines in .procmailrc as follows:

#Save family mail in family box
:0: 
* ^TO_liz|paige|ginny
family

#Claude's mail
:0:
* ^TO_claude
$DEFAULT


Those lines tell procmail to put mail addressed to those persons in those boxes.

Enough for tonight.

CSSJR

---

### Post by SepheeBear on 2006-08-15
The $MAIL environment variable in your shell is responsible for this behavior of showing that you have new mail in the your $MAIL folder. By default it is set to /var/mail/$USER IIRC. To change which file/folder is checked, edit ~/.bashrc to include a line like:

     export MAIL="~/.maildir/"

Check `man bash` and search for "MAIL" for the full rundown on this.

---

### Post by calx on 2006-08-17
None of that seemed to help unfortunately, I think it's because the mail goes into a directory, instead of the regular flat file that it's looking for.. if that makes sense.

Thanks for the replies! :)

---

