---
title: "Evolution junk filter not applied to incoming messages"
date: 2007-10-24
forum: General Help
---

### Post by realbot on 2007-10-24
Hi,

I'm running Evolution 2.12.0 in 7.10 Gutsy using the Exchange and Bogofilter plugins.
The problem is that the junk filter is not automatically applied to the incoming messages.
If I manually select messages and run the "Messages/Check for Junk" command, they are marked as spam, so everything should be configured correctly (and yeas I've turned on the "Check incoming mail for junk" switch in Mail preferences).
Also everything was OK in Feisty...

Any hint?

Thanks
  --Alberto

---

### Post by kroiz on 2007-11-14
Same here.
realbot, If you got a solution please post.

---

### Post by realbot on 2007-11-14
Unfortunately I haven't found one yet. 
Sorry.

---

### Post by kroiz on 2007-11-14
I guess it got something to do with exchange or the exchange addon.

---

### Post by aweller on 2007-11-21
Bump! As I have the same problem using an Exchange server. I have 'taught' the filter, but they are simply not moved... I have to keep teaching it for them to move. Does anyone know how to solve this problem? Thanks.

[EDIT] This is with Spamassasin.

---

### Post by kroiz on 2007-11-21
I don't have a solution yet.
Not bugging me enough to find the solution. but annoience is accumelating.

---

### Post by realbot on 2007-11-21
I've updated Evolution to version 2.12.1, but the problem persists. :(

---

### Post by ububaba on 2007-11-22
> **realbot said:**
> I've updated Evolution to version 2.12.1, but the problem persists. :(

Please count me in. I simply can't find a way to rid of spam. Thanks

---

### Post by Tuxi on 2007-11-26
I can confirm that autofiltering isn't working for me on Evolution 2.12.1.

---

### Post by torgrot on 2007-11-26
You have to keep all of the junk in the junk folder for the filter to function.  Sounds stupid to me, but once I kept from deleting the stuff in the junk folder everything started working as it should.

torgrot

---

### Post by Tuxi on 2007-11-26
> **torgrot said:**
> You have to keep all of the junk in the junk folder for the filter to function.  Sounds stupid to me, but once I kept from deleting the stuff in the junk folder everything started working as it should.

torgrot

Over in this thread [http://ubuntuforums.org/showthread.php?t=354040&highlight=bogofilter&page=3](http://ubuntuforums.org/showthread.php?t=354040&highlight=bogofilter&page=3), there is the following statement 

> **dcstar said:**
> There is a new "Default Junk Filter" setting in the Evolution Mail Preferences in Gutsy, you have to go in and manually set it to use Bogofilter after changing over/upgrading.

I went to my preferences and this was not set.  I don't really have a test as yet.

---

### Post by Tuxi on 2007-11-27
One day of testing, and this seems to have fixed the problem. 

Two machines 3 mailboxes in total with one being domain catchall -- only one junk mail in the inbox.  The machine with the catchall address put a *lot* of junk into the junk folder.

---

### Post by kroiz on 2007-11-28
> **Tuxi said:**
> One day of testing, and this seems to have fixed the problem. 

Two machines 3 mailboxes in total with one being domain catchall -- only one junk mail in the inbox.  The machine with the catchall address put a *lot* of junk into the junk folder.

I don't get it. What fixed the problem?

---

### Post by Tuxi on 2007-11-28
What fixed the problem was that I configured the Preferences/Mail/Junk correctly.  If you need more information see [http://ubuntuforums.org/showthread.php?t=354040&highlight=bogofilter&page=3](http://ubuntuforums.org/showthread.php?t=354040&highlight=bogofilter&page=3).

---

### Post by kroiz on 2007-11-28
Glad it works for you but that is not the case for me and others from this thread and also the thread you posted.

We have all configured correctly but still the inbox is not scanned for junk.

---

### Post by Tuxi on 2007-11-30
Do you have bogofilter or spamassassin installed?  Does your dialog box include the message that the filter has been found (see attached screen shot)?

---

### Post by AVH on 2007-11-30
Mine doesn't. 
All I have are the check boxes for 'Check incoming mail for junk' and 'Include remote tests'. I am trying to use spamassassin and it is checked in 'Plugins and Bogofilter is unchecked. According to the Synaptic Package Manager spamassassin is installed. I'm using version 2.10.1

---

### Post by kroiz on 2007-12-01
SpamAssasain is not installed according to synaptic but I see it in the plugin dialog but it is unchecked.

---

### Post by kroiz on 2007-12-01
> **AVH said:**
> Mine doesn't. 
All I have are the check boxes for 'Check incoming mail for junk' and 'Include remote tests'. I am trying to use spamassassin and it is checked in 'Plugins and Bogofilter is unchecked. According to the Synaptic Package Manager spamassassin is installed. I'm using version 2.10.1

Hi, [-X This is not what this thread is about. please don't steal it.

---

### Post by AVH on 2007-12-01
> **kroiz said:**
> Hi, [-X This is not what this thread is about. please don't steal it.

I'm sorry. I thought that this thread was about spam filters not working and mine isn't

---

### Post by btdown on 2007-12-03
I have 317 emails trained at junk and neither Spamassassin or Bogofilter works at all. Never, not one email has been tagged and moved. Both binaries are found and everything looks to be ok.

This has been an issue for a long time, I'm surprised this has never been resolved.

I know people actually go in there and set up rules and forwards/pipes through spamassasin/etc, but it should not be necessary. Thats what the plugin(s) are for.

BT

---

### Post by kroiz on 2007-12-03
This is not what this thread is about.
This thread is about ppl that have bogofilter working fine but just not auto filtering the inbox for new incoming mail (works manualy)
There are plenty of threads in this forum which already disscussing what you are saying. please don't steal this thread. 
( not that it is going anywhere ) (-:

---

### Post by bigken on 2007-12-03
this how I did it 
sudo apt-get install spamassassin 

then in evolution I moved all my mail to the junk folder then in the junk folder selected all the mail what is not  junk and it seems to work quite well now but i still go though the junk folder to check that its not spamming normal mail :)

---

### Post by bigken on 2007-12-03
oops for got about bogofilter also installed

---

### Post by btdown on 2007-12-04
> This is not what this thread is about.This is exactly what this thread is about. If I manually mark the messages as junk with both Spamassassin or Bogofilter, they get moved to the junk folder. Yet it does not automatically scan incoming email and mark/move it. I cant ever remember it working in any of the last three Ubuntu releases I've run.

---

### Post by kroiz on 2007-12-05
> **btdown said:**
> This is exactly what this thread is about.

You are right. please receive my appologies.

was it so even before the upgrade to gutsy?

---

### Post by medotin on 2007-12-05
Incoming exchange mail filtering appears to be fixed with the evolution-exchange module at rev 1502 and later.  The first release after 1502 is 2.21.2, tagged at rev 1504.

[http://svn.gnome.org/viewvc/evolution-exchange?view=revision&revision=1502](http://svn.gnome.org/viewvc/evolution-exchange?view=revision&revision=1502)
[http://svn.gnome.org/viewvc/evolution-exchange?view=revision&revision=1504](http://svn.gnome.org/viewvc/evolution-exchange?view=revision&revision=1504)

You could checkout from trunk and build/install yourself to fix this, or wait for this change to make it into the repositories.

---

### Post by kroiz on 2007-12-06
This is great news.

I think I can wait for it to get in the repositories.
Any one know when to expect it in ubuntu? ( weeks? monthes? years?)

---

### Post by Tuxi on 2007-12-06
kroiz,

Was the filtering working on incoming mail in Feisty?  Have you tried clearing the check box, restarting Evolution, ticking the check box and restarting Evolution?  I think I did these things suspecting that the state of the plugins at evolution startup was important.

I assume bogofilter still isn't working for you automatically.  My apologies for dropping off the thread.

---

### Post by kroiz on 2007-12-06
> **Tuxi said:**
> kroiz,
Was the filtering working on incoming mail in Feisty?  Have you tried clearing the check box, restarting Evolution, ticking the check box and restarting Evolution?


Yes it worked perfectly before the upgrade to gutsy.
I did that now and I am waiting for a new junk mail to see what will happen.

> **Tuxi said:**
> My apologies for dropping off the thread.
NP

---

### Post by kroiz on 2007-12-06
Nope junk coming to inbox is still not filtered.

---

### Post by Tuxi on 2007-12-06
It may be worth checking your ~/.gconf/apps/evolution/mail/junk/%gconf.xml file.  Here are the contents of mine:
```

<?xml version="1.0"?>
<gconf>
        <entry name="empty_date" mtime="1196522513" type="int" value="13848">
        </entry>
        <entry name="default_plugin" mtime="1196122028" type="string">
                <stringvalue>Bogofilter</stringvalue>
        </entry>
        <entry name="empty_on_exit" mtime="1196121917" type="bool" value="true">
        </entry>
        <entry name="check_incoming" mtime="1196121909" type="bool" value="true">
        </entry>
</gconf>

```
I would think the key lines are default_plugin and check_incoming.  Presumably, either bogofilter or spamassin should work.

---

### Post by kroiz on 2007-12-09
Yours
```
<?xml version="1.0"?>
<gconf>
        <entry name="empty_date" mtime="1196522513" type="int" value="13848">
        </entry>
        <entry name="default_plugin" mtime="1196122028" type="string">
                <stringvalue>Bogofilter</stringvalue>
        </entry>
        <entry name="empty_on_exit" mtime="1196121917" type="bool" value="true">
        </entry>
        <entry name="check_incoming" mtime="1196121909" type="bool" value="true">
        </entry>
</gconf>
```Mine:
```
<?xml version="1.0"?>
<gconf>
        <entry name="check_incoming" mtime="1196948037" type="bool" value="true">
        </entry>
        <entry name="empty_on_exit_days" mtime="1195020594" type="int" value="0">
        </entry>
        <entry name="default_plugin" mtime="1193809978" type="string">
                <stringvalue>Bogofilter</stringvalue>
        </entry>
</gconf>

```

Looks fine to me. the only difference is that you delete your junk on exit. 
I will set this option and check if it makes a difference.

---

### Post by karhulitos on 2008-01-20
I have exactly same problem; no automatic spam scanning of incoming mails. Manually spam filter works perfectly.

Did I understand correctly that the only option is to wait for an update to Evolution?

---

### Post by kroiz on 2008-01-21
I guess you could also get the latest from the SVN and build.

---

### Post by karhulitos on 2008-01-30
Hi,

I think I've used Evolution incorrectly. My case is a bit off topic for this thread as I do not connect to Exchange but instead to IMAP mailboxes. Nevertheless the symptoms were exactly same as the thread starter had.

So, I was at this stage (all "option labels" not neccessarily correct as my Evolution talks finnish):
- Edgy>Feisty>Gutsy, Evolution 2.12.1, 2 IMAP mailboxes configured since Edgy
- bogofilter enabled (plugin was enabled by default)
- bogofilter taught with few tens of spam/ham
- spam filtering worked superbly by selecting new messages -> "message" -> "search for spam"
- "check incoming mail for spam" in "edit" -> "options" -> "email options" -> "spam" was checked 
= spam was never moved to Spam folder automatically, I needed to do "search for spam" manually

So all was OK except spam check for incoming mails was not working for me.

What did I do to fix this?
I didn't realize there are individual settings for each email account as well. So this helped me:
 "edit" -> "options" -> "email accounts" -> <select account> -> "edit" -> "**receive options**" -> check "search spam from new messages"
(**receive options** is most propably incorrectly translated to english but I hope you get the point what I am trying to say)

Voilá. That was it for me. Now all spam bogofilter detects are in Spam folder before I get the Inbox open.

Now, I do not know if this applies to Exchange accounts as well but wanted to share this with you as I've tried to find this for a long time.
I just wonder what is the use for *"edit" -> "options" -> "email options" -> "spam" -> "check incoming mail for spam"* unless it's kind of default value for new email accounts to be created in Evolution. Those 2 accounts didn't have the spam setting enabled by default.

"works on my machine" certified ;)

---

### Post by kroiz on 2008-02-01
:( Nope that did not work for me.
but thanks for trying.:)

---

### Post by Neffscape on 2008-02-05
The procedure explained by karhulitos is correct but it apparently works only wiith IMAP accounts. I'm currently using evolution to check 3 POP mailboxes and 1 IMAP account. What Evolution does is automatically filtering the IMAP account, but for POP3 the thing is not working at all. 
I'm so frustrated man... I can't wait Hardy to see this whole issue finally fixed.
I've been using Thunderbird for years but now I was trying to use Evolution in order to have a better integration with the rest of the ubuntu desktop. Unfortunately EVOLUTION SUCKS in filtering and in usability. I really wonder why users have to tell evolution to filter junk message for each account they decide to check. Thunderbird does it well just by enabling the filter for all the accounts. A working out of the box filter for junk mail it's nowadays a basic function for an e-mail client. What are evolution developers waiting for?

---

