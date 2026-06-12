---
title: "freeware mail emailers?"
date: 2017-01-22
forum: General Help
---

### Post by wbg45 on 2017-01-22
I have a couple of non-profit orgs for whom I maintain mailing lists for periodic
announcements. One runs about 250 names and the other about 70 names.
I am looking for a mass email application, a very simple, command-line based one,
that can accept the target databases of names and emails in .csv format,
then mail a simple text file out to the list. 

Doing it in my email software (Evolution) is a large pain, and TBird doesn't
appear to be much better.

Does anyone know of a piece of freeware that could accomplish this? I have 
invested a good deal of time browsing the web for such and cannot seem to
 refine the searches adequately to filter out the MS-Win programs, and the
web-based fancy and complicated ones.

??

TIA,

Brewster

---

### Post by TheFu on 2017-01-23
I suspect you need to think differently, think the Unix way.
All the email lists I'm on use a tool called a "list server" to manage membership.  There are a few of those - mailman, slist come to mine. If those don't work for your needs, I would search "mailman vs" and look at the other options.

These all work the same way.  People join the "list" and manage their own membership  via emailed commands.  You also join the list.  The list has different email addresses for sending to everyone and for managing the list and their membership.  After setup, all administration is via emailed commands.  Sending an email to everyone means just sending 1 email to the "list" and the server will send it out to everyone over time.

Ok, so due to spam, some email systems get confused with this clearly supported (in the RFCs) method of email and block some of the messages.  In the lists I'm a member of, people using gmail appear to block lists from time to time enough that they get dropped completely.  mailman sees non-delivery and after some amount of those, drops addresses.

Oh and "freeware" is generally only a Windows thing.  On Unix, we look for "F/LOSS" to have the most open software that provides many added rights with the license.

Another way to solve this communications need is to use RSS and/or a usenet newsgroup. These methods require positive action by all your users, however.  I have a habit of checking RSS feeds and Usenet groups, but most people today seem to have lost that habit and non-technical people never had it.

---

### Post by mastablasta on 2017-01-23
search under: 
massmail linux
unique massmail Linux
bulk emails linux
unique bulk emails Linux

web solutions come on top since they are perhaps easier to administer-->  more popular.

---

### Post by SeijiSensei on 2017-01-23
You can handle all of this by installing a mail exchanger like sendmail or Postfix and using "aliases."

In the file /etc/aliases create an entry like
```
mylist:      :include:/path/to/list/of/addresses
```
then run the command "newaliases" to update the alias database.

Put each address in /path/to/list/of/addresses one per line.

Now send an email to "mylist".  It will be delivered to all the addresses on the list.  

I've enabled the secretaries for my college class to send a monthly newsletter to 1,300 recipients using this method on a server I manage.

---

### Post by wbg45 on 2017-01-23
You have misunderstood the query - I know what a listserv is, and am a member of three or four of them. 
This mailing I described is nothing at all like a discussion group - I need to periodically mail announcements
of upcoming events. That's all. And email clients don't do well at that, esp. when there may be 250 addresses.

Thanks anyway,

Brewster

---

### Post by SeijiSensei on 2017-01-23
I didn't misunderstand the query at all, and I gave you a method for accomplishing your goal.

---

### Post by wbg45 on 2017-01-23
That sounds appealingly simple. The only part that is not clear is how you get masses of names
and addresses from their databases (as .csv) over to the list in one stroke - the way you've 
described it, it sounds as if each name and email address pair has to be added individually.
I may be misinterpreting it....

??

Thanks,

Brewster

---

### Post by SeijiSensei on 2017-01-24
Well, I'd just use the simplest solution, putting the CSV list into a spreadsheet and copying the column of email addresses to a text file.  Or you could write a script that takes the CSV file as input, parses the lines, and writes the email addresses to a file.

In my case we maintain our database in PostgreSQL, and I wrote a small PHP app to let people update addresses when we know they change.  Then I run a hourly task in /etc/cron.hourly that uses the psql client to extract the email field and write it to the text file referenced in the aliases file.
```

#!/bin/bash
DBHOST=database_host
DBNAME=database_name
LIST=name_of_list_file

cd /directory/where/the/list/is/kept

mv -f $LIST $LIST.bak

psql -h $DBHOST $DBNAME < create_list.psql   | grep '@' | sort -t'@' -k2 > $LIST

chmod 644 $LIST

```
where create_list.psql looks like this
```

select email from address_table where deceased=0;

```
The "grep" command extracts only lines containing a "@" from the result; the sort command orders the list by domain so all the "gmail.com" addresses are contiguous.  That isn't necessary, but it speeds up the process a bit because of the way sendmail (my exchanger) bundles messages together if they are intended for a single target server.

---

### Post by wbg45 on 2017-01-24
Thanks, Sensei; that's something like what I've been doing, but the author of
it just died, then my exposed mail server on which I'd been running the scripts
died, so I can't retrieve the code until we get it back up. By the way, Sensei, it wasn't you
who misunderstood the query, it was the Fu guy.

Thanks,


Brewster

---

### Post by TheFu on 2017-01-24
Listsrvs can be used for announcements and NOT allow members to post/reply.  Isn't that what you wanted?
Just block the list@ address from the public interface, but allow the management list-admin@ address so folks can manage their subscription.

Sorry that wasn't clear in my post.

Aliases can work too. I use them for static lists, like extended family members. Makes it convenience for everyone to be able to email everyone, but you'd have to block it from the public side so everyone cannot spam you list.

Did a quick search - found this: [http://caspian.dotconf.net/menu/Software/SendEmail/](http://caspian.dotconf.net/menu/Software/SendEmail/)
It is GPL licensed.  I tend to just use the Mail program instead for needs like this.  Sending 100 emails, 1 per second, isn't a big deal.
```

$ /usr/bin/mail -s "[listname] Jan 2017 Announcement" some-email@gmail.com  < $HOME/2017-01-announcement.txt

``` Run that 50-500 times, once for each different email account. An easy loop.
or 
```

$ /usr/bin/mail -s "[listname] Jan 2017 Announcement" some-alias@yourdomain.com  < $HOME/2017-01-announcement.txt

``` sent to a single alias with all the accounts.
I always use a [listname] so people can filter it as they like.  If you like, you can set the FROM to be anything.

---

