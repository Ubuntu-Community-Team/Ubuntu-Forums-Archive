---
title: "Forward mail ?"
date: 2007-05-22
forum: General Help
---

### Post by Subban on 2007-05-22
Evolution  not to include the ability to forward mail on a filter, I've kind of accepted that up till now, but after showing a few people Ubuntu, and two have stuck with it; one now asked about how to forward mail in Evolution (so i'm not alone in this)

Is there some way around this obstacle and actually filter and I guess pipe a command to forward it ?

Its only a few mails a week, it doesn't warrant a procmail install etc.

Thanks

---

### Post by Subban on 2007-05-23
Is there really no way to forward a mail using a filter in Evolution ?

Any way to pipe it from a filter and get the same result ?

---

### Post by xurizaemon on 2007-06-20
> **Subban said:**
> Is there really no way to forward a mail using a filter in Evolution ?

Any way to pipe it from a filter and get the same result ?

Hi Subban

You just need a simple pipe script. Why Evo doesn't offer a GUI for this five-line functionality, I don't know. But they don't.

[QUOTE=guenther]There is no "Forward" or "Redirect" filter action, because this seriously is not the duty of an MUA...[/QUOTE]

So, here's how I just did it. You could skip the tmp file entirely if you want, or improve it to do whatever you want. Of course, if add much to this you might want to look at procmail, but ... bugger that!

```
#!/bin/sh

## tmp file for email
REDIR='/tmp/redirected-email.txt'
## recipient (change)
RECIP='nomail@nomail.org'
## subject
SUBJECT="Secret love letter"

echo "Hi, I'm forwarding you this email. Because I love you, and stuff.
-------------------------------------------------------------------" > $REDIR

while read LINE ; do 
  cat $LINE >> $REDIR
done

cat $REDIR | mail -s "$SUBJECT" $RECIP
```

Save that as your forward-mail.sh file and then pipe to that command based on filter action. Salt to taste.

---

### Post by Subban on 2007-06-22
> **xurizaemon said:**
> Hi Subban

You just need a simple pipe script. Why Evo doesn't offer a GUI for this five-line functionality, I don't know. But they don't.

So, here's how I just did it. 
< < < S N I P > > >    < < < S N I P > > >


Thanks a heap for taking the time to reply and show how you achieved it. I haven't tried it yet but will put that in later and give it a whirl.

I am utterly dumbfounded that this isn't built into Evolution, and the quoted comment in your solution from guenther is even more disturbing, as more and more people take up linux, more and more people are going to expect what is a pretty basic function without the need of writing bash scripts or running procmail. I sure as heck don't need to forward enough emails to warrant running a mail server, its just a couple a week I forward to my mobile and such

---

### Post by xurizaemon on 2007-06-22
Yes. Bear in mind that's the opinion of one developer on IRC, not Gnome policy.

There is some mention of an earlier (evo1.0?) "Redirect" command, but I can't find that in evo2 either. WIERD.

[http://bugzilla.gnome.org/show_bug.cgi?id=204891]("http://bugzilla.gnome.org/show_bug.cgi?id=204891")

Also ... if that's not "the duty of an MUA" ... WTF? This app has calendaring, memos, task management, contact management, phone syncing ... but not mail forwarding, oh no, THAT'S a job for procmail ;)

Are there any Evolution devs in Ubuntu land who we can get onside? This missing feature is a major reason to avoid switching IMO. Would be happy to contribute to its addition.

---

### Post by xurizaemon on 2007-06-22
More light reading on this topic:

[LIST]
[*][http://mail.gnome.org/archives/evolution-list/2006-October/msg00154.html](http://mail.gnome.org/archives/evolution-list/2006-October/msg00154.html) - simple answer
[*][http://mail.gnome.org/archives/evolution-list/2005-March/msg00002.html](http://mail.gnome.org/archives/evolution-list/2005-March/msg00002.html) - more detailed script
[*][http://mail.gnome.org/archives/evolution-list/2002-September/msg00021.html](http://mail.gnome.org/archives/evolution-list/2002-September/msg00021.html) - in the TODO list (Sep 2002)
[*][http://bugzilla.gnome.org/show_bug.cgi?id=220417](http://bugzilla.gnome.org/show_bug.cgi?id=220417) (duplicate bug request)
[*][http://bugzilla.gnome.org/show_bug.cgi?id=231256](http://bugzilla.gnome.org/show_bug.cgi?id=231256) (dupe)
[*][http://bugzilla.gnome.org/show_bug.cgi?id=200166](http://bugzilla.gnome.org/show_bug.cgi?id=200166) (dupe - note REDIRECT not FORWARD)
[*][http://bugzilla.gnome.org/show_bug.cgi?id=239183](http://bugzilla.gnome.org/show_bug.cgi?id=239183) (dupe)
[*][http://bugzilla.gnome.org/show_bug.cgi?id=245602](http://bugzilla.gnome.org/show_bug.cgi?id=245602) (dupe)
[/LIST]

---

### Post by Subban on 2007-06-23
> **xurizaemon said:**
> Yes. Bear in mind that's the opinion of one developer on IRC, not Gnome policy.

Ok, I wasn't aware of the origin of the quote and assumed the worst.

>  There is some mention of an earlier (evo1.0?) "Redirect" command, but I can't find that in evo2 either. WIERD

Sounds somewhat similar to when I wanted to save an entire newsgroups text posts to HD from Pan.I soon found I wasn't able to select all the  post,in one  then click save to disk,  the function wasn't there, save to disk only applies to single selections, but what gauls me, is that it was removed to prevent bloat... I mean, they had the function in there apparently, and took it out. I think I ended up writting a script to extract the subject line from each post in the cache and renaming them, then a second script to remove all the header info, pain in the bum when the function used to be there. A job that should have literally taken 5seconds took me 3 evenings (still learning the foibles of Bash script)

> Also ... if that's not "the duty of an MUA" ... WTF? This app has calendaring, memos, task management, contact management, phone syncing ... but not mail forwarding, oh no, THAT'S a job for procmail ;)

 This missing feature is a major reason to avoid switching IMO.

A friend who switched to Ubuntu after seeing it in action and realizing it was suitable for him soon found that Evolution wouldn't forward mail, it was at that point I joined the mailing list and asked about it there as well as here, I never did receive a reply there and unsubcribed after a month.

I love Ubuntu and linux, its been my sole desktop for 18mnths, but its hard to fathom omitting functions that seem fairly basic and trivial to implement  are either left out, or worse, removed.

---

### Post by xurizaemon on 2007-06-24
The "Forward To" filter action was removed in 2001 (!!!) according to the evolution ChangeLog (2001-07-18, ChangeLog.pre-1.4)

I had a look at the changes from that day, and the only change made was to filtertypes.xml. This file looks like it dictates the UI in the filter manager, so perhaps all that's needed is to re-enable the UI element and call the correct Camel function when it's used.

I tried doing just that and rebuilding evo from Ubuntu's source so we can provide a diff, but it didn't add the filter selection box as I hoped. So now I'm trying to dig around the Camel bindings (which I can't find a reference for) to see what I should be doing.

Any hackers more familiar with Evolution, Camel or C generally who would put a bit of energy towards this?

Will keep you posted with progress ... hopefully we can fix this in Ubuntu's version with a patch, then encourage Evolution to pick it up in their trunk.

Should we open a Launchpad bug for this? I searched hard and couldn't find a matching one.

We'll see ...

---

### Post by Subban on 2007-06-26
I don't have the necessary coding ability myself to assist with that but would be more than willing to help test any changes made. The last serious coding I really did was on the C64 and Amiga (I loved 6810 assembleron the 64 and E on the Amiga)

This does seem to be something that has kept popping up over time from various people but has never had a sensible solution,  my friend who converted to Ubuntu now uses Sylpheed I believe solely because of the lack of mail forwarding in Evolution. I prefer Evolution and make use of the calendaring and addressbook with my PocketPC so would much prefer a solution in that (easier than scripting it i might add)

---

