---
title: "Howto: Get Bogofilter working in evolution"
date: 2007-02-05
forum: General Help
---

### Post by graigsmith on 2007-02-05
*updated*
Ok So it took me forever to figure out how to get bogofilter running.  But it's really easy.

```
sudo apt-get install bogofilter
```

Now open evolution.  click edit, and then plugins.  make sure that the bogofilter is selected. and your spam assassin plugin should be deselected 

EDIT, for gutsy. you have to go to Edit, Preferences, Mail preferences, Junk tab. and set bogofilter to the default junk plugin, cause it does not do this automatically. THEN it should work.

Now go to your email inbox folder. And mark your **whole** inbox as junk,  all the spam and all your good mail needs to be marked junk!  if you don't mark some of your good mail it wont know whats good when you mark it as not junk.  Now go to the junk folder and mark all your good mail as "not Junk" using evolutions not junk button.

And then it should start working normally from now on!  :)

---

### Post by buellman on 2007-02-07
> **graigsmith said:**
> Now go to your email inbox folder. And mark your whole inbox as junk,  all the spam and all your good mail needs to be marked junk!  if you don't mark some of your good mail it wont know whats good when you mark it as not junk.  Now go to the junk folder and mark all your good mail as "not Junk" using evolutions not junk button.

Hey... cool. Yesterday I searched nearly the whole web for a Howto that finally works. Congratulations... your Howto seems to work :-) A least it looks so for the moment :-)

Greets. Buellman

---

### Post by graigsmith on 2007-02-07
and thankfully it's simple.  the ones i tried earlier required you to make wierd filters and call the bogofilter command thru the filter.  but thankfully this is pretty integrated.  and seems to work as well as thunderbirds email thing.

So, where do i file a bug report about this?

---

### Post by graigsmith on 2007-02-07
you know. now that i have it working. i decided to test it. i think deleting the spam assassin plugin is probably not necessary.    i think disabling it in the preferences works too. 

i think the biggest thing is marking everything as spam, and then marking some of the good stuff as not spam.  So, mabey there is no bug. it's just not obvious that you have to mark some of your good mail as not junk.  because before bogofilter starts working it needs to know some spam, and some good mail (aka ham).

---

### Post by buellman on 2007-02-08
> **graigsmith said:**
> i think the biggest thing is marking everything as spam, and then marking some of the good stuff as not spam.  So, mabey there is no bug. it's just not obvious that you have to mark some of your good mail as not junk.  because before bogofilter starts working it needs to know some spam, and some good mail (aka ham).
Yep... thats it. It' sort of not intuitive to mark all mails in the INBOX as Spam and than mark mails you want as "Not Junk". But it works.
Maybe some sort of Checkbox should be displayed when you first start Evolution and set up your Acoount:
```
"Would you like
[] SpamAssassin
[] Bogofilter
[] none
as your Junkfilter."
```
Than it will download what is necessary to get the filter to run with a little notice how to train your filter.
Could not be that hard to implement :-)

Greets. Buellman

---

### Post by kevmartin on 2007-03-26
Great - thanks :grin:

If you're like me and have a significant number of mails kept semi-permanently in your Inbox, and already have heaps of mails in your Junk folder placed there manually, a quick approach is to mark all mails in the Inbox as Important, mark them as Junk, sort the mails by Important Flag, select them all in 1 block again, and move them back.  Then send/Receive mail and see the junk mail go where it belongs.  Excellent!

---

### Post by quercusrobur2002 on 2007-03-26
> **kevmartin said:**
> Great - thanks :grin:

If you're like me and have a significant number of mails kept semi-permanently in your Inbox, and already have heaps of mails in your Junk folder placed there manually, a quick approach is to mark all mails in the Inbox as Important, mark them as Junk, sort the mails by Important Flag, select them all in 1 block again, and move them back.  Then send/Receive mail and see the junk mail go where it belongs.  Excellent!

It seems to have worked for me too!! I'd just about given up... Only problem now is that its still recognising some genuine emails as spam since I did that whole palava above... But hopefully this can be rectified over time provided i keep marking the good posts as 'not junk'

Yes I agree that the junk filters need to be made far more intuitive, I hope that Evolution develoopers are taking note!

---

### Post by eudemus on 2007-04-10
This has not solved things for me. How can I get help?
I have tried the following strategies.

1. Simply using the plugin (Bogofilter, Spamassassin, - each separately, and together.). Did not work at all.

2. Pipe to Spamassassin, worked for a bit then stopped working.

3. Pipe to Bogofilter. Again, worked for a bit, then stopped working.

No idea what made the change that stopped these working.
And despite having lots of spam and ham, and having run the various training suggestions multiple times, Bogofilter does not detect spam ever.

I don't know what additional info to put up here, because I have no idea what the problem is.
I've wondered whether somehow (I know not how this might have happened) the filter has been trained wrong, and it would be good to start again and retrain it. But I've no idea how to get bogo to unlearn all its previous training and start from scratch in training it again.

Oh, I've reinstalled the bogo plugin, and - yes, you've guessed it - it still doesn't work.
Frankly, this is yet another really really basic bit of functionality in Ubuntu that just doesn't work, and should work, out of the box.
If the free software agenda is goign to be successful (and I sure hope it will be!), this kind of basic failure of basic functionality just can't be allowed to be present. Some of us - indeed many many people - haven't got the time to spend getting the nuts and bolts of a system to do their most basic functions competently.

Help!
Eudemus

---

### Post by kevmartin on 2007-04-10
> **eudemus said:**
> 
Frankly, this is yet another really really basic bit of functionality in Ubuntu that just doesn't work, and should work, out of the box.
If the free software agenda is goign to be successful (and I sure hope it will be!), this kind of basic failure of basic functionality just can't be allowed to be present. Some of us - indeed many many people - haven't got the time to spend getting the nuts and bolts of a system to do their most basic functions competently.

Help!
Eudemus

I'm not sure I have any helpful suggestions to offer unfortunately, but I do want to say that I don't think spam filtering is ever going to work 'out of the box'. Filtering needs to know what is junk (and, crucially in this case, also what isn't) - and the only way is for you to tell the software.  As soon as I knew this and used the simple technique in this thread, the filtering started working like a charm. I get 500+ mails a day of which very few are legitimate.  Evolution now filters very very well - far better than Outlook ever did.  I've never had first hand experience with Hotmail, AOL, Yahoo mail etc, but plenty of second hand experience through clients, and they seem to also have very negative experiences of legitimate mails being marked as junk on the basis of arbitrary filters put in place by the mail program, instead of based on the user's criteria.

"Yet another  really really basic bit of functionality in Ubuntu that just doesn't work" seems extremely harsh.  For one, it does work for most people - and secondly, I'm not aware of any other basic functionalities that don't work in Ubuntu.  Fee free to provide examples.

On your problem, how many mails have you given the program as examples of junk to work with? And how many examples of good mails? (The more the better in both cases). Are you leaving the junk mails permanently in the junk mail folder?

If you want to test if it's working try sending a mail to yourself from another address which has some content copied from a spam you've received.  Go to Evolution, mark it as junk.  Then send another copy of the same mail to yourself and see if it gets filtered as junk the second time.

Sorry I probably wasn't more help but I'm pretty new at this too. :)

---

### Post by eudemus on 2007-04-10
KevMartin,
Thanks for the reply.
I totally agree with all you have written here, but none of it really addresses my issue (although I'll try the test you suggest of sending spam content, and seeing if bogofilter will learn).

I've given bogofilter 2662 spam (perhaps some duplicates in there, but that gives you some idea of the volumes), and about 900 or so good mails. I leave the spam in "Junk" because I'm told the filter needs them there for some reason.

the irritating thing (and hopefully this will mean it could be solved more easily) is that this is not just a case of bogofilter needing training. It is not filtering ANYTHING AT ALL. Nothing ever gets put into junk automatically now. My best attempts at using my thousands of ham and spam to train it seem to be utterly in vain. It simply NEVER marks anything as junk. I'm hoping that there's something I haven't done, some box I haven't checked, some program I haven't activated. But I'm getting weary of all this sleuthing you have to do just to get a program to do what it says it ought to.

(My other basic functionality gripes over which I have had more trouble than I care to mention have been getting my monitor to work, getting mp3 files to play, streaming both music and video from webpages, connecting my pda - the latter, admittedly not really "basic". I stick with Ubuntu/Linux/Free Software because (a) I believe in it, and (b) I can't afford the alternatives and the hardware they require.)

Thanks again for taking an interest.
Eudemus.

---

### Post by eudemus on 2007-04-10
KevMartin,
Nice diagnostic test. Tried it.
Sent a spam-content-filled email (and indeed it appears instantly to have fallen foul of the corporate spam filtering for a university email account I have).
Evolution allowed it.
I marked it as Junk.
then resent an identical mail.
Evolution allowed it again.

I guess this means that bogofilter is not learning, or that the plugin is not working at all - perhaps? How could I tell which of these is the case?

Any further ideas?
Eudemus

---

### Post by eudemus on 2007-04-11
OK, I've got a workaround, which is to use filters on incoming mail.
Pipe to program /usr/bin/bogofilter -u  does not return 0 (zero), then set status as Junk.

The problem with this workaround is that the learning bit is not easy to engineer, and requires a bit of manual periodically, I think. What's really wanted is for it to learn each time I manually mark something as spam (where the filter has missed it) or as not spam (for where the filter gets a false positive).

Much better would be to get the plugin working. But I can't currently see how to do that.
Any ideas? Are there any settings for the bogofilter plugin that I can see and tweak?

Eudemus

---

### Post by eudemus on 2007-04-16
I have managed to get bogofilter "working" using filters (piping to bogofilter and using "does not return 0").

But now it simply consigns everything to spam, depsite giving it repeatedly thousands of examples of clear spam and ham to learn from.

Can anyone help?

(I have wondered if bogofilter has had faulty "teaching" info passed to it by something I've done along the way. Is there a way to reset the teaching and start again?
On the other hand, the problem may be nothing to do with that.)

Eudemus

---

### Post by eudemus on 2007-04-16
I've just tested a clear spam and a clear ham, and both when piped to bogofilter return the value 1.
That means that bogofilter isn't telling the difference between my ham and spam.

It makes me think that reteaching from scratch will be the way forward, but how do I do that?

All help appreciated.

---

### Post by eudemus on 2007-04-18
Found a wordlist.db file to delete. That gives a clean start.
I need the "pipe to" bit in my filter *not* to have the -u flag, as that causes it to treat its decision as correct and learn additional keywords from the emails it is just in the process of classifying as junk/non-junk. I think that the -u flag is what you need once bogofilter is basically trained and getting most things right.

Return value does not equal 1.

It seems now to be getting things right.
I'll train it periodically manually, and try and work out how to put the training commands into a script that is called every time I open Evolution. But I don't know how to do that yet.
bogofilter -n < /home/jamie/.evolution/mail/local/Inbox
bogofilter -s < /home/jamie/.evolution/mail/local/Spam
(I don't use the junk folder, I get the filter to put all spam into a separate Spam folder. Evolution's standard junk "folder" isn't really a separate folder, it's still in the inbox file, just flagged. That screws up the training if you do it using the above command)

Ho hum. Is anyone out there?

Eudemus

---

### Post by kevmartin on 2007-04-19
Sorry - have not been checking my subscribed threads in the forums lately - other stuff absorbing me :)

It seems like you are working it out well and better than I could have suggested anyway - but I thought I'd say hello since you seemed all alone in here ;)

---

### Post by WNDS1701 on 2007-05-09
Hey guys!


I think that this is the right thread to work on my problem...

I am using an Exchange server for my communication and now have the following problem:

If I mark an e-mail as read, it is recognized and moved to the Junk-folder. The problem is, that they come back to the Inbox after closing Evolution and that they are not marked as Junk...


I hope that you can help me with this.


THANKS A LOT IN ADVANCE!

---

### Post by MDanihy on 2007-05-30
To tell you the truth, I would like to see a setting where everything is considered junk unless I mark it good or the sender in in my contacts.  Training a junk mail filter is so old-school.

---

### Post by eudemus on 2007-09-17
What I ended up doing in Evolution / Gnome was as follows:
(And the latest version of Evolution is annoying since it doesn't allow you to select options when piping to bogofilter)

1. create a separate local folder for Spam (this is important, cos you need it to be stored as a separate mail file (which the standard Evolution spam isn't).

Your best bet is to manually put a load of definitely spam messages in there, and run the following from the terminal to train the filter.
bogofilter -Ns < /home/jamie/.evolution/mail/local/Spam

2. Set up Filter on Incoming mail:
Pipe to program /usr/bin/bogofilter
does not return 1
Mark as spam, stop processing.

3. Using the Session Manager, run the following on login:
bogofilter -Ns < /home/username/.evolution/mail/local/Spam
or
bogofilter -s < /home/jamie/.evolution/mail/local/Spam
(the first is safer than the second, because everything in the Spam folder is "deregistered" as non-spam and registered as Spam. So, just in case anything got wrongly classified through bogofilter as ham on a previous occasion, this will correct that. This should mean that you help to train bogofilter whenever you put something manually into your Spam folder)
This training command will then run whenever you log into Ubuntu (GNOME).

Hope this helps. (I've actually switched to KDE desktop now, and am running a similar thing in KMail - which is slightly easier, and has a nice wizard that configures this all for you.)

Cheers
Eudemus

---

### Post by wild_oscar on 2007-10-12
> **kevmartin said:**
> 
On your problem, how many mails have you given the program as examples of junk to work with? And how many examples of good mails? (The more the better in both cases). Are you leaving the junk mails permanently in the junk mail folder?


Does this mean that in order to use bogofilter you can't delete the junk mail folder?

That seems to be bad, I don't really want to have a huge spam folder of useless mail...

Can anyone clarify on this?

---

### Post by tog on 2007-10-17
If my experiences and observations are correct, there may be two issues at play here. First, I just upgraded to 7.10 RC, so it uses Evolution 2.2.

To use bogofilter, ensure that the plugin is enabled in Evolution. Also, under mail preferences, you will see an option under the Junk Tab to use bogofilter.  To train bogofilter, first mark all your junk mail as "junk" in Evolution, and that will move it to the Junk folder. Here comes the catch, at least for me. Once I have trained Evolution, and I get junk mail, it does not recognize it as such.

The problem is NOT that bogofilter is not seeing it as junk, but that, bogofilter is NOT being appled to the inbox. I can easily verify this by selecting all messages in my inbox, which now contains new junk mail, and then choosing the option "Check Messages for Junk." This pipes it to bogofilter and correctly marks the junk mail. Thus, bogofilter works, but is not being applied on the inbox. I suspect this is similar to [http://bugzilla.gnome.org/show_bug.cgi?id=444503](http://bugzilla.gnome.org/show_bug.cgi?id=444503)

I don't have a solution yet, but if somebody does, that would be great :-)

Thanks.

tog.

---

### Post by graigsmith on 2007-10-30
> bogofilter works, but is not being applied on the inbox.  

this is because you must mark ALL of your mail as junk, and then mark the stuff that's not junk as not junk, it should move it back to the inbox, and start working.

make sure you have under edit, preferences, mail preferences, junk tab, you have the default plugin selected.  and then make sure that the bogofilter junk plugin is enabled and working, then make sure the spam assassin plugin is disabled.

in fact, the newer version of evolution lets you click the mark as not junk on things in your inbox. that should tell bogofilter that it is in fact not junk.

---

### Post by tog on 2007-10-30
That's not what I meant. Bogofilter as it works. That is, it has already been trained, and knows which messages are junk, and which are not. The problem is that as new messages come to the Inbox, Bogofilter, and actually, any filter, is not being applied to them automatically. I have to manually select all the messages, then do "check for junk", at which point, all the Junk messages are moved to the Junk folder.

This behavior, which is incorrect, happened only after I upgraded to 7.10.

tog

---

### Post by dcstar on 2007-10-31
> **tog said:**
> That's not what I meant. Bogofilter as it works. That is, it has already been trained, and knows which messages are junk, and which are not. The problem is that as new messages come to the Inbox, Bogofilter, and actually, any filter, is not being applied to them automatically. I have to manually select all the messages, then do "check for junk", at which point, all the Junk messages are moved to the Junk folder.

This behavior, which is incorrect, happened only after I upgraded to 7.10.

tog

There is a new "Default Junk Filter" setting in the Evolution Mail Preferences in Gutsy, you have to go in and manually set it to use Bogofilter after changing over/upgrading.

---

### Post by showcaser on 2007-10-31
I can confirm what Tog said.

If I highlight new messages and select "Check for Junk" it catches the junk messages fine, however, it is NOT applying the junk filter automatically to new messages. This is despite having a check on the option "Check incoming mail for junk" and having the default junk plugin set to Bogofilter.

I should also mention i'm running a fresh install of Gutsy 7.10 not an upgrade. I'm wondering if it has to do with the account type being IMAP as opposed to pop?

Anyone have any thoughts?

---

### Post by showcaser on 2007-10-31
Sorry, double post.

---

### Post by cmus on 2007-11-07
I am also having this same problem. Mine is an upgrade from Ubuntu 7.04 to 7.10 but no spam filtering is working. It worked fine before the upgrade. I should mention I have 2 accounts on this computer - one is a POP3 account and one is an Exchange account - neither is processed for spam.

---

### Post by asmiller-ke6seh on 2007-12-04
Yup - the trick is to mark all the email in your inbox as spam, then go to the Junk folder, and mark the good stuff as not spam, and VOILA! it's working.

The reason for this is that Bogofilter is a Beysian filter. It needs to generate a SPAM score and a HAM score and compare the two. If you have never said "this is HAM", even though you have said "this is SPAM" it will never be able to make a comparison, and it will just treat everything as HAM.

Still, you need to look in your JUNK folder from time to time to see if there is any HAM hidden in the SPAM, and mark it as NOT SPAM. Over time, the more you do this, the "smarter" bogofilter gets.

:guitar:

---

