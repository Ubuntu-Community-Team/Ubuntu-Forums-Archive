---
title: "Fetchmail, Procmail &amp; Docecot mail server problem"
date: 2013-04-28
forum: General Help
---

### Post by PM47 on 2013-04-28
Can someone please help me get a simple stand-alone mail server working before I throw myself off the nearest tall building ?? 

I'm running Xubuntu, logged on as user 'mailserver' 

So far I've done the following...

Install the software :

   sudo apt-get install fetchmail
   sudo apt-get install procmail
   sudo apt-get install dovecot-imapd dovecot-pop3d

Set up '/etc/fetchmailrc' to collect mail from an external account and pass it to procmail :
(for test purposes I limit the message size and don't flush the source mail spool)

   set daemon 300
   poll mail.messagingengine.com protocol pop3
     username "me@fastmail.fm" ssl password "mypassword" is "junk" here fetchall limit 10000 keep
   mda '/usr/bin/procmail -d %T'

Root must own this file as it needs to run as a service :

   sudo chown root: /etc/fetchmailrc
   sudo chmod 600 /etc/fetchmailrc

Set up '/etc/procmailrc' :

   MAILDIR=/var/spool/mail
   DEFAULT=junk/
   LOGFILE=/var/log/procmail
   VERBOSE=on

   :0:
   * ^To:.*user1@mydomain.com
   user1/

   :0:
   * ^To:.*user2@mydomain.com
   user2/

Create three new 'Desktop' users - 'junk', 'user1', 'user2'

Create mailboxes :

   sudo mkdir -p /var/spool/mail/junk
   sudo chown junk:mail /var/spool/mail/junk
   sudo chmod 770 /var/spool/mail/junk

   sudo mkdir -p /var/spool/mail/user1
   sudo chown user1:mail /var/spool/mail/user1
   sudo chmod 770 /var/spool/mail/user1

   sudo mkdir -p /var/spool/mail/user2
   sudo chown user2:mail /var/spool/mail/user2
   sudo chmod 770 /var/spool/mail/user2

Add the following to the end of '/etc/dovecot/dovecot.conf' :

   mail_location = maildir:/var/spool/mail/%u

Test by runnning Fetchmail from the command line :

   sudo fetchmail --daemon 0 -v -f /etc/fetchmailrc

Fetchmail runs and collects the messages from Fastmail. The messages are sorted into the three mailboxes by procmail as expected, placed in the 'new' folder in the three mailboxes. However, mail files for 'user1' and 'user2' are owned by 'root' while mail for 'junk' is owned by 'junk'. The net result is that when I access the mail using an IMAP client I can see the mail in the 'junk' folder but not the mail in the 'user1' or 'user2' folders. The Dovecot log tells me 'access denied' for 'user1' and 'user2', presumably due to the root ownership of the mail files. The mail files are, however, shifted from the 'new' folder to the 'cur' folder in all three mailboxes when accessed from the IMAP mail client. If I manually change the ownership of the 'user1' and 'user2' mail files then they appear in the IMAP client as expected.

It appears that if procmail delivers a message as a result of a 'match' it writes the file with root ownership, if it's delivered to the default mailbox, as there are no matches, it writes the file with the default (in this case 'junk') ownership. I obviously need to get procmail to write the 'user1' and 'user2' mail files with the appropriate ownership for Dovecot to work.

I've been struggling with this problem for several days and would very much appreciate some help to solve it ??

Finally, once this is solved, how do I set Fetchmail to run in daemon mode when the system is started ??

Thanks in advance for any help offered, I would seriously like to recover my sanity :-)

---

### Post by SeijiSensei on 2013-04-28
The root user executes /etc/procmailrc.  To have rules applied with the permissions of the user you create a user-level file called .procmailrc in the user's home directory (/home/username/.procmailrc).

However I think you have made this process more difficult than it need be.  Fetchmail understands users and their inboxes and will deliver to them directly without using procmail at all.  I think this example from the [fetchmail documentation]("http://fetchmail.berlios.de/fetchmail-man.html#42") fits most of your needs:

> Here&#8217;s what a simple retrieval configuration for a multidrop mailbox looks like:
```
poll pop.provider.net:
     user maildrop with pass secret1 to golux &#8217;hurkle&#8217;=&#8217;happy&#8217; snark here

```
This says that the mailbox of account &#8217;maildrop&#8217; on the server is a multidrop box, and that messages in it should be parsed for the server user names &#8217;golux&#8217;, &#8217;hurkle&#8217;, and &#8217;snark&#8217;. It further specifies that &#8217;golux&#8217; and &#8217;snark&#8217; have the same name on the client as on the server, but mail for server user &#8217;hurkle&#8217; should be delivered to client user &#8217;happy&#8217;.

You'd replace the entries like "golux" and "snark" with your "user1" and "user2" above.

---

### Post by PM47 on 2013-04-28
Hi,

Thanks for your reply

> **SeijiSensei said:**
> The root user executes /etc/procmailrc.  To have rules applied with the permissions of the user you create a user-level file called .procmailrc in the user's home directory (/home/username/.procmailrc).

I tried that for one user but the .procmailrc file in that users home directory was never parsed. I came to the conclusion that maybe only the .procmailrc file in the logged in users home directory would be parsed, I need to sort mail for all users (there will be 9 in total). Have I got this wrong and if so how do I get procmail to parse all the users .procmailrc files ? What I don't understand is why procmail manages to set the correct ownership for the default mailbox but doesn't for the matched exits ?

> **SeijiSensei said:**
> 
However I think you have made this process more difficult than it need be.  Fetchmail understands users and their inboxes and will deliver to them directly without using procmail at all.  I think this example from the [fetchmail documentation]("http://fetchmail.berlios.de/fetchmail-man.html#42") fits most of your needs:

You'd replace the entries like "golux" and "snark" with your "user1" and "user2" above.

Not really, I'm replacing an existing mail server, VPOP3 on Windoze,  and make extensive use of mail filters for our extended family, plus I  need to add spam filtering and anti-virus functions as well. While  Fetchmail can handle the latter, unfortunately procmail is necessary to handle the  mail filtering I need to use.

Thanks again for your reply, I'll have another look at the user .procmail files and see if I can get that to work.

---

### Post by PM47 on 2013-04-28
Just tried adding '/home/user1/.procmailrc' again, bear in mind I'm logged in as 'mailserver' not 'user1'. It's not parsed. If I add 'INCLUDERC=/home/user1/.procmailrc' to '/etc/procmailrc' it's then parsed but the retrieved mail messages are once again owned by root :-(

---

### Post by SeijiSensei on 2013-04-29
Are you sure user1 owns /home/user1/.procmailrc?  Put this line at the top of /etc/procmailrc
```

LOGFILE=/var/log/procmail

```
and this line at the top of /home/user1/.procmailrc
```

LOGFILE=/home/user1/procmail.log

```
That will give you some useful debugging information.

> Not really, I'm replacing an existing mail server, VPOP3 on Windoze, and make extensive use of mail filters for our extended family, plus I need to add spam filtering and anti-virus functions as well. While Fetchmail can handle the latter, unfortunately procmail is necessary to handle the mail filtering I need to use.

Is the intent to have procmail call the clamd and spamd clients?

---

### Post by PM47 on 2013-04-29
> **SeijiSensei said:**
> Are you sure user1 owns /home/user1/.procmailrc? 

Yes I created it that way with CHOWN & CHMOD

> Put this line at the top of /etc/procmailrc
```

LOGFILE=/var/log/procmail

```
and this line at the top of /home/user1/.procmailrc
```

LOGFILE=/home/user1/procmail.log

```
That will give you some useful debugging information.


Already tried that /home/user1/.procmail is never touched

> Is the intent to have procmail call the clamd and spamd clients?

Haven't really addressed that one yet, it looks like either Fetchmail or Procmail could do this but no point until I've sorted out the mail filters.

I tried this earlier...

:0c
* ^To:.*user1@mydomain
{
  DEFAULT=$MAILDIR/user1/
}

...to see what happened if I changed the default mailbox and just let it drop through, the resulting messages are put in the correct mail boxes but now all owned by 'junk', so still no solution :-(

I may just have a look at courier-maildrop and see what that offers ?

---

### Post by PM47 on 2013-04-29
Finally got it to read my /home/user1/.procmailrc file, it only does it if /etc/procmailrc does not exist !!

---

### Post by PM47 on 2013-04-30
Still no good, it only reads the .procmailrc file in the home directory of the logged on user and any mail written is owned by the logged on user. Log on as a different user, reads that users .procmailrc file and any mail written is again owned by that logged on user.

I've come to the conclusion that in order to run a simple stand alone mail server, as I'm trying to do, I'll have to use virtual mail boxes, e.g. using postfix or whatever, and setting up these is way over my head. I've looked at things like ClearOS and Vpostmaster but these are either way too complex for what I need or don't quite do what I need, e.g. ClearOS seems good but doesn't offer any mail filtering, or at least it does but only by editing the config files manually, which defeats the object of using ClearOS.

Not sure where to go from here. I'm looking to replace Vpop3 on an ageing Windoze XP box because it's the last Windoze machine I run (everything else is now on Ubuntu) and Windoze XP support vanishes pretty soon, so XP will become a virus writers heaven. I don't feel inclined to buy overbloated Windows 7 or 8 simply to run a simple mail server and Vpop3 doesn't run on Wine, so at present I'm stuffed !!

Thanks for your interest anyway, if I find a workable solution to this problem I'll post the details here for anyone else who may be interested.

---

### Post by PM47 on 2013-05-04
To conclude this thread, here are some notes re the working mail system I've actually ended up with :

My 'maildir' format mailboxes live in '/var/spool/mail/..' and are  'owned' by the respective users. Mail files written into the mailboxes  by Procmail are also owned by the respective users, necessary for  Dovecot to be able to read them out to an imap client.

I've ended up routing the incoming mail to defined users using Fetchmail as I've not managed to get Procmail to work in a sensible manner (see later). The '.fetchmailrc' and '.fetchmail_log' files live in my Home directory and fetchmail is called by my login user.

This is my '.fetchmailrc file' :

# Fetchmail Configuration for MailServer 
 
```

set daemon 300 
set logfile "/home/mailserver/.fetchmail_log" 
set postmaster "junk" 
set no bouncemail 
set no spambounce 
set softbounce 
set properties "" 
 
poll mail.messagingengine.com with protocol POP3 
    options    envelope    'X-Delivered-to' 
        localdomains    myusername.fastmail.fm 
    user 'myusername@fastmail.fm' there with password 'mypassword' 
    is    'user1' 
        'user2' 
        'user3' 
        'anothername'='user4'    here 
    options    ssl 
#        keep 
#        fetchall 
#        limit 10000 
    mda '/usr/bin/procmail -d %T' 
 
poll pop.googlemail.com with protocol POP3 
    user 'myusername@gmail.com' there with password 'mypassword'  
    is 'user1' here  
    options ssl 
#        keep 
#        fetchall 
    mda '/usr/bin/procmail -d %T' 
 
poll mail.plus.net with protocol POP3 
    user 'myusername' there with password 'mypassword' 
    is 'user2' here 
    options 
#        keep 
#        fetchall 
    mda '/usr/bin/procmail -d %T' 
 
poll pop.orangehome.co.uk with protocol POP3 
    user 'myusername.fsnet.co.uk' there with password 'mypassword' 
    is 'user3' here 
    options 
#        keep 
#        fetchall 
    mda '/usr/bin/procmail -d %T' 

```

Mail from Fastmail is for more than one user so Fetchmail uses 'multidrop' mode for Fastmail. Fastmail reliably writes the 'X-Delivered-to:...' header line in my emails. The 'envelope' option tells Fetchmail to read the 'X-Deivered-to' line and 'localdomains' appears to be necessary for Fetchmail to extract the user names from this line. no idea why, but without 'localdomains' set to my Fastmail account name it doesn't work.

Four local users are specified, one with an alias (anothername) in the email header for 'user4'.

The options 'keep', 'fetchall' and 'limit 10000' are used for testing.

The 'mda....' line is required for EACH mail server polled and Procmail called with the mail 'recipient' passed as %T.

Three additional mail providers are polled in a similar manner in the subsequent sections but only in 'singledrop' mode.

Procmail called with the '-d %T' parameter will ONLY read the global run file '/etc/procmailrc'. It will NOT automatically read any '.procmailrc' files in any home directories. The '%T' parameter in this instance passes the mail recipient name to Procmail so Procmail writes mail files to the mail folders with the correct owner, but this ONLY happens if no matches are found and procmail writes mail to the default mail folder. If a procmail 'recipe' provides a match, then mail files are written to the mail folders with 'root' ownership' and Dovecot can't read them !! I've not found any way round this behaviour.

If Procmail is called without any parameters, then it will read the '.procmailrc' file in the logged on users directory ONLY and any mail files are then written with the current logged on users ownership. Again Dovecot can't read these files and I've not found any way around this behaviour.

My global '/etc/procmailrc' file only has one line :

```

INCLUDERC=/home/mylogon/.procmailrc

```

This uses the '.procmailrc' file in my home directory but is only done to allow me to edit a Procmail run file without resorting to root permissions to edit the '/etc/procmailrc' file directly. This is NOT the same as Procmail using the '.procmailrc' file directly as any mail files written as a result of matches in this file still have 'root' ownership !

My '/home/mylogon/.procmailrc' file is as follows :

```

MAILDIR=/var/spool/mail
DEFAULT=$LOGNAME/
LOGFILE=/home/mailserver/.procmail_log
#VERBOSE=on

```

The key is the second line, which causes Procmail to write all mail it receives to the $LOGNAME mail folder with the correct owner. $LOGNAME is the %T parameter provided by Fetchmail. If any 'recipes' are included in this file then the resulting match will cause the mail file to be written with 'root' ownership and Dovecot will be unable to read them. 

I've tried various combinations of global and local '..rc' files for both Fetchmail and Procmail and not found any other way to get Procmail to write the mail files with the correct ownership other than to use this setup.

For completeness, the default dovecot.conf file has a single line added to the end :

```

mail_location = maildir:/var/spool/mail/%u

```

..which directs dovecot to read the correct mail folders when accessed by an imap client.

There's still a lot I don't understand about Fetchmail, Procmail and Dovecot, and Linux in general, but this setup works for me, it does 90% of what I need to do so it'll suffice until I find a better way of achieving what I need.

Thread closed....

---

### Post by PM47 on 2013-05-06
Just an added note :

While this works most of the time...

```

poll mail.messagingengine.com with protocol POP3
       options    envelope    'X-Delivered-to'
       localdomains    myusername.fastmail.fm      
      user 'myusername@fastmail.fm' there with password 'mypassword'      
is    'user1'
       'user2'
       'user3'
       'anothername'='user4'    here
options ssl  
#        keep  
#        fetchall  
#        limit 10000      
mda '/usr/bin/procmail -d %T' 

```

.. the line 'anotheruser'='user4' sometimes doesn't appear to work

This is more reliable...

```

poll mail.messagingengine.com with protocol POP3
      options    envelope    'X-Delivered-to'
      user 'myusername@fastmail.fm' there with password 'mypassword'
is    'user1@myusername.fastmail.fm'='user1'
      'user2@myusername.fastmail.fm'='user2'
      'user3@myusername.fastmail.fm'='user3'
      'anotheruser@myusername.fastmail.fm'='user4' here
 options ssl
#           keep
#         fetchall
#         limit 10000
mda '/usr/bin/procmail -d %T'

```

---

### Post by PM47 on 2013-05-11
Discovered Webmin a few days ago. Would thoroughly recommend it if, like me, you are struggling to get simple things working. It's not perfect, but it does most of the work for you and sets up the basic config files, all you need to do is to tweak the set-up to do exactly what you want - I just wish I'd discovered Webmin two or three weeks ago :-)

---

### Post by PM47 on 2013-05-13
Just found the *very simple* solution to my original problem with procmail - 'DROPPRIVS=yes' inserted in the appropriate place in the '.procmailrc' file drops the root priveliges and assumes the identity of the mail recipient, which means any files written are owned by the recipient - problem solved !!! DROPPRIVS is in the man page for procmail, I just didn't understand the significance of it's use until I saw it used, and described, in another context.

I sincerely hope this thread may be of some use to other 'newbies' like me struggling with the intricacies if Linux mail servers and in particular procmail :-)

---

