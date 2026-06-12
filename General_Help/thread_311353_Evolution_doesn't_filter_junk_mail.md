---
title: "Evolution doesn't filter junk mail"
date: 2006-12-02
forum: General Help
---

### Post by Nebu Pookins on 2006-12-02
Evolution doesn't seem to filter any of the junk mail. When I start up evolution from the terminal, I see the following text, which seems relevant:

(evolution-2.6:24295): evolution-mail-WARNING **: ignored this junk plugin: not enabled or we have already loaded one

(evolution-2.6:24295): e-utils-WARNING **: Plugin 'Bogofilter junk plugin' failed to load hook 'org.gnome.evolution.mail.junk:1.0'

(evolution-2.6:24295): camel-WARNING **: camel_exception_get_id called with NULL parameter.

** (evolution-2.6:24295): WARNING **: Failed to connect to the D-BUS daemon: Unable to determine the address of the message bus

Not sure how to proceed from here.

---

### Post by Spin Doctor on 2006-12-02
You are running  Evo 2.6 on Dapper?

---

### Post by ciscosurfer on 2006-12-02
You can always try Thunderbird instead :-)

---

### Post by Spin Doctor on 2006-12-02
Ciscosurfer has a point...

If you dont need the other personal management tools in Evolution, I would probably try Thunderbird which has an excellent spamfilter .... =)

---

### Post by Nebu Pookins on 2006-12-02
I'm using Dapper, yes, and the version of evolution which comes preinstalled with Dapper, which according to the about box is 2.6.1.

I do use the other features in evolution, namely the calendar, contacts and tasks. I've tried Thunderbird for e-mail before, but I didn't like how it doesn't have a calendar. I still use Thunderbird for RSS feeds, though.

---

### Post by ciscosurfer on 2006-12-02
> **Nebu Pookins said:**
> I'm using Dapper, yes, and the version of evolution which comes preinstalled with Dapper, which according to the about box is 2.6.1.

I do use the other features in evolution, namely the calendar, contacts and tasks. I've tried Thunderbird for e-mail before, but I didn't like how it doesn't have a calendar. I still use Thunderbird for RSS feeds, though.Mozilla's Sunbird might interest you: [http://www.mozilla.org/projects/calendar/sunbird/download.html](http://www.mozilla.org/projects/calendar/sunbird/download.html)

Or, you might be even more interested in Lighning: [http://www.mozilla.org/projects/calendar/lightning/](http://www.mozilla.org/projects/calendar/lightning/)

---

### Post by Nebu Pookins on 2006-12-02
Thanks for the pointer to Sunbird and Lightning. Sunbird looks like it's a stand alone calendar application, not integrated with any e-mail client. And I had problems installing the Lightning extension into Thunderbird. First, Firefox kept trying to install Lightning into itself, rather than letting me download the file. When I tried to download the file outside of FireFox, Thunderbird told me the XPI hash is incorrect, and wouldn't install it.

If possible, I'd really like a solution that involved fixing Evolution, rather than switching to a different set of applications.

---

### Post by ciscosurfer on 2006-12-02
I believe there are 3rd party add-on spam-filter apps for Evolution (and other email clients, for that matter).  Off the top of my head (I'm sure there are others) there's: spamassasin, dspam, spamprobe

---

### Post by Spin Doctor on 2006-12-03
Nebu,

I am using Evo 2.8.1 bundled with Edgy. I belive they changed the junkmail settings for the new version, so I cant help you on this one, since I never ran 2.6.1.

---

### Post by ayoli on 2006-12-03
For junk filtering in evolution, spamassassin is needed.
1. install spamassassin
2. train spamassassin with a mbox full of spam
3. create a rule in evolution to use spamassassin.

check full how-to [here]("http://www.ubuntuforums.org/showthread.php?t=99603&highlight=how-to+evolution+spamassassin")

---

### Post by speckman on 2006-12-14
i have the same problem.  why, oh why, would the default install come with evolution that gives the no-junk mail filter errors?  seriously.

:)

---

### Post by wpshooter on 2006-12-14
Can't the message filters under the edit button in Evolution perform this task ?

And also by checking the junk parameters under mail preferences tab ?

---

### Post by dcstar on 2006-12-14
> **speckman said:**
> i have the same problem.  why, oh why, would the default install come with evolution that gives the no-junk mail filter errors?  seriously.

:)

The default Junk filter for Evolution is Spamassassin (which works fine with my Evolution, albeit a little slow), if you want to use Bogofilter, do a forum search for the various HOWTOs on the subject.

---

### Post by duva on 2006-12-18
Well, I too have Edgy with Evolution 2.8.1 and used to use Thunderbird.  But since I got a Palm and wanted syncronization and an integrated solution, I came back to Evolution since I used it last time like 3 years ago maybe.  It's come a long way but had problems with junk mail, and I tried marking for weeks every junk mail and waited to see when it would really detect them bu itself.  Until I read this thread and checkes in Synaptic if I had installed Spamassassin.  And to my supride I hadn't.  And that did it!

---

