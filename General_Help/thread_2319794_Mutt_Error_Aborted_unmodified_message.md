---
title: "Mutt Error: Aborted unmodified message"
date: 2016-04-07
forum: General Help
---

### Post by shag00 on 2016-04-07
Ubuntu 15.10, mutt 1.5.23-3 (latest available through Synaptic)

I have been using mutt for some years now and until about a week ago it always sent e-mails as expected, then suddenly all emails stopped. After hunting down the problem I found that mutt worked again and only needed a system restart, however that only worked for a day. On my second attempt at pinning down the problem I have narrowed it down to the text editor used by mutt but cannot see a solution.

In my case I use gedit as the text editor which is specified in my .muttrc file (and has worked for years).

Now here is where it gets tricky as there are 3 ways I use to send an email:
1/ from the command line:     mutt -s "Test Email" [EMAIL="me@yahoo.com"]me@yahoo.com[/EMAIL] < /dev/null,
2/ from within mutt (using m),
3/ called from a shell script.

Now in all cases, 1, above is successful, ie the email with a header and no body is sent. So we have established that mutt can send an email, in other words .muttrc is correct. In cases 2 and 3 they are only successful if gedit is not open (which is why my first attempt to fix the problem worked).

I assume something has changed in Ubuntu recently, around 1/4/16, as there have been no changes to mutt. Can anybody advise a solution that enables me to keep a gedit window open (normally 24/day) and have mutt send emails. A copy of my .muttrc is attached.

[ATTACH]268222[/ATTACH]

---

### Post by howefield on 2016-04-07
Not sure anything has changed, at least using 15.10 here and the same version of mutt is working with gedit as the editor (opened or otherwise).

I use nano as the text editor but changed muttrc to use reflect gedit and it seems to be working as intended, probably not much use to you other than confirming that it should be "fixable". For info my muttrc is as follows..

```
# Local folder
set mbox_type=Maildir
set folder=~/Mail

# IMAP Settings
set realname="xxxx xxxxxx"                    
set from="xxxx xxxxxx <xxxxxxxxx@xxxxxx.com>" 
set imap_user=xxxxxxxxx@xxxxx.com
set imap_pass=xxxxxxxxxxxxxxxxxxxxxxxx           
set folder=imaps://imap.gmail.com                
set spoolfile=imaps://imap.gmail.com/INBOX       
set record=imaps://imap.gmail.com/Sent            
set postponed=imaps://imap.gmail.com/Drafts        
mailboxes =INBOX # check for new email here                                 
set header_cache=~/.mutt_cache     

# Reading Mail
set timeout=10  
set mail_check=300
set sort=threads
set sort_aux=date
set move=no     
set mark_old=no
ignore * # ignore all headers except for ...
unignore Date: From: To: CC: Bcc: Subject:
hdr_order Subject: Date: From: To: CC: Bcc:
set index_format="%{%b %d} %-15.15L [%Z] %s" # custom index format

# Composing Mail
set editor="gedit"     
set markers=no     
set signature=~/.sig  
set include=yes     
set forward_format="Fwd: %s"                

# Sending Mail
set copy=yes      
set smtp_url="smtps://xxxxxxxxx@xxxxx.com:xxxxxxxxxxxxxxxxxxxxxxxxx@smtp.xxxxx.com/" 

# Pretty Colors
color hdrdefault white black  # headers white on black
color header brightgreen black ^From:  # sender's name in green
color quoted cyan black  # quoted text in blue
color signature red black   # signature in red
color status white yellow
color index green  default ~N  # new
color index red default ~D  # deleted
color index brightmagenta default ~T  # tagged
color index brightyellow default ~F  # flagged
color header green default "^Subject:"
color header yellow default "^Date:"
color header yellow default "^To:"
color header yellow default "^Cc:"
color header yellow default "^Bcc:"
color header yellow default "^From:"
color header red default "^X-.*:"

# View Special Formats
# set mailcap_path=~/.mailcap
auto_view text/html auto-render html inline mutt

#set sort=threads
#set sort_browser=date
#set sort_aux=reverse-last-date-received

# Use abook with Mutt
set query_command="abook --mutt-query '%s'"
macro index a     "|abook --add-email\n" 'add sender to abook'
macro pager a     "|abook --add-email\n" 'add sender to abook'
```

---

### Post by shag00 on 2016-04-08
Thanks for your reply, I have tested using nano as the text editor in  mutt and found that there are still problems. I have uninstalled and  re-installed both gedit and mutt and that does not fix the problem  either, I still get the aborted unmodified message, message.

---

### Post by shag00 on 2016-04-09
I think I have found a solution, I have changed my muttrc file as follows:
set editor="gedit"      to      set editor="gedit --wait".

I found that from the mutt window this change allowed a body to be added:
set editor="gedit"     to     set editor="gedit --new-window

I will just wait another 24 hour cycle to see what happens.

---

