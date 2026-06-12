---
title: "Evolution Crashes when writing new message and leaving connection live ..."
date: 2008-06-18
forum: General Help
---

### Post by AiBo on 2008-06-18
Having some new problems with Evolution after upgrading to Hardy.

I have been using Ubuntu and Evolution at work since 2006 and whether it is good practice our not I have 7-8 email addresses pouring into the Inbox.  Each dist upgrade since I just tar the Evolution folders and then extract them after a fresh install and all is good.

Now with 12,000+ messages my inbox and stepping up to Hardy I have begun encountering a problem.  If I leave Evolution connected and repsond, or write a new message, the whole thing locks up and I am forced to "force quit" of force shutdown from terminal.  

I discovered though if I disconnect, write the message, connect and send it, no problem everything works great ...

No idea where to start in addressing this problem.  Can anyone get me started down the right road?

Thanks in advance!

Ai Bo

---

### Post by griztown on 2008-06-19
I'm having the same problem.  I just upgraded to Hardy but I'm running Xubuntu so I'm not sure if that makes a difference.  As soon as I try and respond to an email it freezes and I have to kill it.

---

### Post by AiBo on 2008-06-19
hmmm, maybe this needs a bug ticket

---

### Post by griztown on 2008-06-19
AiBo, I'm not sure about you but I'm currently using the exchange package for evolution.  Not sure if that is part of the problem.

Thanks.

---

### Post by AiBo on 2008-06-19
How can you tell if you are using the exchange package?  One of the accounts I have it set up to check is on an exchange server ...

I submitted a bug report via bugzilla:

[http://bugzilla.gnome.org/show_bug.cgi?id=539088](http://bugzilla.gnome.org/show_bug.cgi?id=539088)

---

### Post by AiBo on 2008-06-20
Listed as critical by the triage team ...  trying to get together the stack information for them.  griztown, maybe you can send in your stack info too and help out the debug team?


[http://bugzilla.gnome.org/show_bug.cgi?id=539088](http://bugzilla.gnome.org/show_bug.cgi?id=539088)

---

### Post by AiBo on 2008-07-03
still working through this one ... no solutions yet.  Any one have any thoughts?  Griztown did you ever find a solution?

---

### Post by AiBo on 2008-07-23
I know others out there are experiencing the same problems.  It seems to be a bug, perhaps connected to exchange.  

Please anyone else out there struggling with us help out the bug team over at:  [http://bugzilla.gnome.org/show_bug.cgi?id=539088](http://bugzilla.gnome.org/show_bug.cgi?id=539088)

Bug 539088 – Evolution Mail and Calendar: Evolution Crashes when ...

---

### Post by mailkarthi on 2008-07-24
I am facing this issue too. It happens for me when I click "Reply" or "Compose" or "Contacts".

I believe the problem could be when it tries to look for contacts in the exchange server. Can you suggest any option to disable Evolution from looking for contacts stored in servers "Global Address Book"?

---

### Post by mailkarthi on 2008-07-24
Server is "Exchange Server 2003" and I am connected to server using its webmail address "webmail.mycompany.com/exchange".

---

### Post by anlog on 2008-07-25
I think you're right. I disabled all forms of autocompletion and Evolution stopped freezing after replying to an email.

Regardless, this app crashes more than any I've ever encountered. A real pain.

> **mailkarthi said:**
> I am facing this issue too. It happens for me when I click "Reply" or "Compose" or "Contacts".

I believe the problem could be when it tries to look for contacts in the exchange server. Can you suggest any option to disable Evolution from looking for contacts stored in servers "Global Address Book"?

---

### Post by mailkarthi on 2008-07-25
Yes, it works for me as well, when i disabled "Auto complete" all server address books (GAL and my personal address book on server).

Now I copied some frequent address to local address book and using that for autocomplete.

Too bugy app but no alternative for Exchange OWA.

---

### Post by anlog on 2008-07-25
New Evolution Exchange plugin released today in Ubuntu. Will test and report back here.

---

### Post by AiBo on 2008-07-29
Just tested, mine still crashes after the update ;(

Seems more activity on bugzilla.  Voice in if you haven't already.  Quite annoying bug, I hope it gets solved soon!

[http://bugzilla.gnome.org/show_bug.cgi?id=539088](http://bugzilla.gnome.org/show_bug.cgi?id=539088)

---

### Post by varaonaid on 2008-07-29
I'm still having this problem as well.  It's uber annoying!  I finally have to disable the exchange account if I don't want evolution to crash all the time but that really screws up shared contacts etc.  I hope they fix it.  

I wish they would allow me to disable the global address book altogether.  I thought they used to have that option in previous versions.  I need the exchange contacts but my exchange server doesn't support the GAL.

---

### Post by AiBo on 2008-07-30
Looks like we might be waiting for an update in Ubuntu to Evolution 2.23 as this seemed to fix the problem for our Fedora brothers ... [http://bugzilla.gnome.org/show_bug.cgi?id=532771](http://bugzilla.gnome.org/show_bug.cgi?id=532771)

looking forward to a bump up ;)

---

### Post by timzak on 2008-08-10
I'm having a similar problem lately.  If I leave Evolution open throughout the day, it inevitably locks up with a grey window, which then must be force quit.  If I leave it closed and only open when mail-notify tells me there is mail, I never have any problems.

I haven't had any problems while reading or composing.  Only when it remains open for a long period of time.

---

### Post by mailkarthi on 2008-08-12
> **anlog said:**
> New Evolution Exchange plugin released today in Ubuntu. Will test and report back here.

Is there any update with this fix?? I am still facing this problem though my system has all updates installed

---

### Post by AiBo on 2008-08-12
.... no update that I know about.  I will still crash unless first disconnecting from the exchange server.

Have you helped by posting your stack with the bug people?  [http://bugzilla.gnome.org/show_bug.cgi?id=532771](http://bugzilla.gnome.org/show_bug.cgi?id=532771)

---

### Post by mailkarthi on 2008-08-12
The bug has log files of some users already. Since it is much similar to mine I didnt post it again

---

### Post by fermin on 2009-07-14
I have this same problem and I do not use Exchange accounts. Evolution crashes when I press de 'reply' icon, I force quit it, but no need to restar the computer, I can even restart Evolution after force quitting it and runs normally.

My guess is that it has to do with the evolution data server, which connects the contacts database between evolution, pidgin and the gnome panel, I think. The reason is that I've had problems with this process before, as it ate up a great deal of CPU and tended to cause crashes. The latter does not occur to me anymore, since I upgraded to jaunty.

---

