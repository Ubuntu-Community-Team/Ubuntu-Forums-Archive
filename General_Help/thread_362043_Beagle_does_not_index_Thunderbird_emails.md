---
title: "Beagle does not index Thunderbird emails"
date: 2007-02-15
forum: General Help
---

### Post by johann_p on 2007-02-15
The [Beagle FAQ]("http://beagle-project.org/FAQ#Does_Beagle_support_Mozilla_Thunderbird.3F") says that Beagle does index Thunderbird emails and address book entries, but this does not happen on my system.

Here is the output of "beagled --list-backends" (I have not disabled or otherwise messed with what I got with the default package installation):

```

Current available backends:
User:
 - EvolutionMail
 - EvolutionDataServer
 - KMail
 - Files
 - GaimLog
 - IndexingService
 - Tomboy
 - Labyrinth
 - Blam
 - Liferea
 - Akregator
 - KonquerorHistory
 - KonqBookmark
 - KNotes
 - KOrganizer
 - KAddressBook
 - Kopete
 - Konversation
System:
 - applications
 - documentation

```

Does Beagle expect the Thunderbird files in .mozilla-thunderbird (Ubuntu's way) or .thunderbird (every other distro's and Mozilla's way)?

---

### Post by nikhilk on 2007-02-15
This [link]("http://www.mail-archive.com/dashboard-hackers@gnome.org/msg02994.html") seems to indicate that Beagle has problem with non-standard (w.r.t. Debian/Ubuntu) location of Thunderbird files. Whether the problem was fixed and if yes then in which version was not clear though.

---

### Post by johann_p on 2007-02-15
Hmm, I kind of thought that could be the reason and I have made sure that the thunderbird directory is called .thunderbird (making a symbolic link to .mozilla-thunderbird for the non-standard Ubuntu Thunderbird program).

However, Beagle still ignores my email.

I also do not see anything that would indicate that a Thunderbird backend even exists in the --list-backends listing, shouldn't there be something like "ThunderbirdMail" in the list?

---

### Post by Rhubarb on 2007-02-15
[http://beagle-project.org/Indexing_Data](http://beagle-project.org/Indexing_Data)
> Beagle is smart about how it determines when to index your files. It tries not to interfere with other applications you may be running. But if you want to force it to index everything as fast as possible, before running Beagle:

$ export BEAGLE_EXERCISE_THE_DOG=1

However, this will slow down your system considerably as Beagle reads data from the hard drive and uses the CPU to index it. 

---

### Post by nikhilk on 2007-02-15
> **johann_p said:**
> I also do not see anything that would indicate that a Thunderbird backend even exists in the --list-backends listing, shouldn't there be something like "ThunderbirdMail" in the list?
Which version are you using? Thunderbird support has been removed from Beagle, version 0.2.15 onwards.

---

### Post by penno on 2007-03-18
> **nikhilk said:**
> Which version are you using? Thunderbird support has been removed from Beagle, version 0.2.15 onwards.

According to [this beagle page]("http://beagle-project.org/Supported_Filetypes"), it is currently supported.

> 
Beagle supports the following data sources:

    * File system
    * Evolution mail, calendar, and addressbook
    * Thunderbird mail, news, RSS feeds, and addressbook
    * Korganizer events and TODOs
    * KMail mail
    * KAddressbook addressbook
    * Gaim and Kopete instant messaging and IRC logs
    * Firefox and Epiphany web pages (as you view them, through browser extensions)
    * Konqueror web pages
    * Blam, Liferea and Akregator RSS feeds
    * Tomboy, KNotes, and Labyrinth notes
    * Konversation IRC logs
    * Opera Web History 


---

### Post by johann_p on 2007-03-18
Not a single Thunderbird email made it into the index here, ever, unfortunately.

---

### Post by earlycj5 on 2007-03-26
> **nikhilk said:**
> Which version are you using? Thunderbird support has been removed from Beagle, version 0.2.15 onwards.

From the Beagle FAQ, [http://beagle-project.org/FAQ](http://beagle-project.org/FAQ)

**Does Beagle support Mozilla Thunderbird?**

Yes! Thunderbird support was added to Beagle 0.2.8. Email, news, RSS feeds and addressbook contacts are indexed.

---

### Post by johann_p on 2007-03-26
> **earlycj5 said:**
> From the Beagle FAQ, [http://beagle-project.org/FAQ](http://beagle-project.org/FAQ)

**Does Beagle support Mozilla Thunderbird?**

Yes! Thunderbird support was added to Beagle 0.2.8. Email, news, RSS feeds and addressbook contacts are indexed.

Still not happening with the beagle that Ubuntu Feisty Fawn provides (unfortunately none of the beagle commands has a --version option, but synaptic shows the version as 0.2.16.3).

When I run the demon, the console output shows that beagle accesses the .evolution directory and the .kde/share/apps/kmail directory but not the .thunderbird directory.

This is broken in many ways really because I have configured beagle to ONLY index a directory /some/dir - NOT my home directory.
The directory .thunderbird of Thunderbird is in /some/dir and my home directory only contains a symbolic link to it. That directory does not get processed although it should.

On the other hand, .evolution and .kde are in my home directory and should therefore  should not get processed by beagle, according to my configuration BUT they are processed.

---

### Post by johann_p on 2007-03-26
HOW should thunderbird email get indexed? WIth a backend? 

Then the backend should be somewhere -- I could not find it anywhere.

When the beagle demon starts up it reports about the following backends:

```

Debug: Found 2 backends in /usr/lib/beagle/Backends/EvolutionBackends.dll
Debug: Starting Inotify FSQ file event backend
Debug: Found 16 backends in /usr/lib/beagle/BeagleDaemonLib.dll
Debug: Starting backend: 'EvolutionMail'
Debug: Starting backend: 'EvolutionDataServer'
Debug: Starting backend: 'KMail'
Debug: Starting Evolution mail backend
Debug: Starting backend: 'Files'
Debug: Starting KMail backend
Debug: Starting backend: 'GaimLog'
Debug: Starting backend: 'IndexingService'
Debug: Starting backend: 'Tomboy'
Debug: Starting backend: 'Labyrinth'
Debug: Starting backend: 'Blam'
Debug: Starting backend: 'Liferea'
Debug: Starting backend: 'Akregator'
Debug: Starting backend: 'KonquerorHistory'
Debug: Starting backend: 'KonqBookmark'
Debug: Starting Konq history backend ...
Debug: Starting backend: 'KNotes'
Debug: Starting backend: 'KOrganizer'
Debug: Starting backend: 'KAddressBook'
Debug: Starting backend: 'Kopete'
Debug: Starting backend: 'Konversation'
Debug: Starting backend: 'applications'
Debug: Starting backend: 'documentation'
Error: Unable to start EvolutionDataServer backend: Unable to find or open libraries:
(followed by more error messages for this error)

```

---

### Post by tperica on 2007-03-27
Does anybody have any solution how to index Thunderbird e-mails and contacts?

Additionally, if i want to run command: beagled, i get Beagle Daemon exited with errors. ..., _but_, indexing is working, except without e-mails and contacts from thunderbird?

cheers
tomislav

---

### Post by danyul on 2007-03-28
Beagle isn't currently supported by default in the Beagle builds.  The FAQ was out of date.  (I changed it.)  I suppose you might be able to build Beagle yourself with Thunderbird support enabled, but the whole reason why it was disabled was because it didn't work very well (when I was using it it turned into a runaway memory hog).  I remember reading the developers mentioning that the way that Thunderbird implements mail storage is not very conducive to efficient indexing.  I think they may have bounced around the idea that Thunderbird/Beagle integration could make a good Google Summer of Code project. Either way, hopefully once Thunderbird switches to a SQLite backend (Which I think is going to happen in TB3?), good Beagle integration will be possible.

---

### Post by johann_p on 2007-03-29
> **danyul said:**
> Beagle isn't currently supported by default in the Beagle builds.  The FAQ was out of date.  (I changed it.)  I suppose you might be able to build Beagle yourself with Thunderbird support enabled, but the whole reason why it was disabled was because it didn't work very well (when I was using it it turned into a runaway memory hog).  I remember reading the developers mentioning that the way that Thunderbird implements mail storage is not very conducive to efficient indexing.  I think they may have bounced around the idea that Thunderbird/Beagle integration could make a good Google Summer of Code project. Either way, hopefully once Thunderbird switches to a SQLite backend (Which I think is going to happen in TB3?), good Beagle integration will be possible.

Thanks for making this clear. However [this page](http://beagle-project.org/Supported_Filetypes) still lists Thunderbird mail as supported.

It is a pity that Beagle does not seem to allow a simple and well documented pluggable way how to add support for indexing additional file types and the mono implementation is probably not exactly helpful here.
Other desktop indexing/search solution are more flexible here.

---

### Post by dbera on 2007-04-01
> **johann_p said:**
> It is a pity that Beagle does not seem to allow a simple and well documented pluggable way how to add support for indexing additional file types and the mono implementation is probably not exactly helpful here.

You mean like this :
1) [http://beagle-project.org/ExternalFiltersRepository](http://beagle-project.org/ExternalFiltersRepository)
    To add support for more file types
    Written using shell script and command line programs
2) [http://svn.gnome.org/viewcvs/beagle/trunk/libbeagle/examples/beagle-external-indexer.c?view=markup](http://svn.gnome.org/viewcvs/beagle/trunk/libbeagle/examples/beagle-external-indexer.c?view=markup)
    To add support for more data sources (e.g. to index thunderbird emails, you have to do more than just index the email data files; you also have to parse the TB database)
    This can be done using C#, C or python.
    [http://joeshaw.org](http://joeshaw.org) recently blogged about how to do this.

---

### Post by mac.ryan on 2007-04-21
Just thought to update this thred:
[http://beagle-project.org/Summer_Of_Code_2007](http://beagle-project.org/Summer_Of_Code_2007)

---

### Post by johann_p on 2007-04-22
As I said recently on the beagle mailing list, I think that supporting Thunderbird mail via a Thunderbird extension would be better than doing it by parsing mail files and mork-metadata files, for many reasons. Thunderbird's way to store email and email metadata sucks big time - avoiding that mess by indexing email with an extension that sends email and its metadata to an indexing queue and accepting requests to show an result from a beagle search would be the much cleaner way to do this.

---

### Post by johann_p on 2007-04-22
> **dbera said:**
> You mean like this :
1) [http://beagle-project.org/ExternalFiltersRepository](http://beagle-project.org/ExternalFiltersRepository)
    To add support for more file types
    Written using shell script and command line programs
2) [http://svn.gnome.org/viewcvs/beagle/trunk/libbeagle/examples/beagle-external-indexer.c?view=markup](http://svn.gnome.org/viewcvs/beagle/trunk/libbeagle/examples/beagle-external-indexer.c?view=markup)
    To add support for more data sources (e.g. to index thunderbird emails, you have to do more than just index the email data files; you also have to parse the TB database)
    This can be done using C#, C or python.
    [http://joeshaw.org](http://joeshaw.org) recently blogged about how to do this.

Thanks for pointing this out. I see a couple of questions and problems here: 
1) how does beagle determine the mime type before running such a filter? Unlike Microsoft seems to think, not every file's type is uniquely identified by its extension, there might be files without extensions that can be many different types and there might be extensions that map to several types.
2) the filter cannot pass back any metadata to the indexer, just text. It would be good to have a way, e.g. by using yaml format, to pass arbitrary metadata (e.g. author names) to beagle so that one can search for this too.
3) definition of filters cannot be done on a user-by-user basis, it seems. Since beagle is designed to work and run on a user-by-user basis, it would be nice to have user-specific filters too, instead of having to mess with the system-wide configuration.

Otherwise it is nice to have this and I will definitely try this out to see where I can get with it.

---

### Post by jviscosi on 2007-05-06
When I noticed Thunderbird e-mails (actually Seamonkey, but same format -- for now) had disappeared from my Beagle search results, I downloaded the latest Beagle source code and compiled it with Thunderbird support.  This does appear to make Beagle a bit of a pig, but not all the time, and it's not really all that noticeable to me except when I'm compiling or otherwise heavily using my machine (which frankly isn't that often).  To me, it's worth it to have the e-mails indexed, because searching inside Seamonkey/TB for e-mail bodies is pretty slow.  (I'm the sort of person who never deletes e-mails.)

The information about Thunderbird possibly moving to SQLite is interesting.  (I stopped using Sunbird when they moved it from ICS to SQLite because this broke cross-application access to my calendar [Orage, KOrganizer, wmCalendar].  I know Sunbird exports to ICS but didn't want to bother with the extra step.)  Anyway, if they do move TB to SQLite and there's a substantial performance improvement, maybe I'll switch back to it.

---

### Post by Tickle Me Elmo on 2007-05-08
I can't wait until Beagle has Thunderbird indexing support by default as it is a very nice and lean desktop search engine.

---

### Post by Hopey on 2007-05-29
I really can't understand what is taking forever to get this working on standard install in Ubuntu. In my opinion this is major feature missing in Feisty.

---

### Post by Tickle Me Elmo on 2007-06-04
Hi,


How do I make Beagle indexing Thunderbird emails? I didn't quite get that yet...


TIA :)

---

### Post by mlissner on 2007-07-13
I have been reading the beagle development mailing list for the past month or so, and here's what I've figured out:
 - TB support is not built in by default because of the memory hoggingness of it. Apparently this is the fault of the formats that TB uses to store its mail, which apparently suck.
 - TB support is a top priority, and is being worked on. Last I heard, the fix was balanced between an extension and a beagle backend, which theoretically will fix the memory problems.
 - If I had to guess, I'd say wait for the next Ubuntu version, and we'll have it. It seems to be nearing completion.

---

### Post by Tickle Me Elmo on 2007-07-15
Thank you for that update! :)

It is strange that Google Desktop indexes Thunderbird mail, but not Beagle. I'd prefer to run Beagle over Google Desktop, though if the Beagle developers don't put in one or more sticks in the fire and get a move on, I think a great number of users will simply opt in for Google Desktop instead (myself included).

---

### Post by beow on 2007-07-17
While waiting for this Beagle feature, I can recommend "mairix" [http://www.rpcurnow.force9.co.uk/mairix/](http://www.rpcurnow.force9.co.uk/mairix/) 
It is increadible fast and lean on system resources. You do have to use the command line like

```

$ mairix search for this

```

in order to search thunderbird for messages with "search", "for" and "this" words in the message. All search results appears in a thunderbird "search-results" folder that contains a copy of the found messages. Very smooth. Works very well for me, I use IMAP and Maildir but mairix supports mbox (POP) folders as well. Very easy to compile with ./configure, make, sudo make-install. Try it, it rocks... :guitar:

---

### Post by Depressed Man on 2007-09-05
There's a backend for Thunderbird now (but not in the main trunk yet). It's still being tested but it does work (in the trunk that has Thunderbird support). It requires installing an extension in TB which then compiles the info and sends it off to Beagle to index.

---

### Post by dbera on 2007-09-20
Beagle has a Thunderbird backend since 0.2.8+ but it was disabled **by default** since 0.2.14/15 because it had performance issues. In the mean time, there was a Google summer of code project in which a new Thunderbird backend was written. This one has been reported to work much better. This new backend will be released in beagle 0.3.0 but is otherwise available from beagle svn trunk.

---

### Post by posterboy on 2007-09-21
The T'bird backend was a compile time option over a number of beagle releases. Like this:
./configure --enable-thunderbird. That would cause the backend to be built, and it worked great for me, on FC6. There were some issues on some distros, These were being addressed, and may have been solved by now. Later packages might include the T'bird backend by default. The devs hang out on the gimpnet IRC server in channel #dashboard.

---

### Post by gaussian on 2007-09-21
If you need to index your Thunderbird emails, my experience is that **Recoll** (should be available via Synaptic/Apt-Get) works perfectly. The UI is not as polished as Beagle's, but it has done the one indexing task that I care about (Thunderbird emails) right for couple years now. It is really great tool in general, I currently have it enabled in all my Linux machines (two old Mandriva desktops and a brand new Ubuntu Laptop) and Beagle disabled. I am sure that there are things that Beagle does better (instant indexing of chats and IM, instant indexing of Firefox history/cache), but I don't find those that valuable (others might disagree). What I want to find is my old documents/emails and for this purpose I have found Recoll to be the perfect tool.

Google Desktop did index the Thunderbird email perfectly, except that every time I received an email the CPU usage jumped up to 100% for awhile when GD was indexing (this was with the initial "Beta") and the computer was unusable. I don't know if this has been fixed, I remember reading that I was not the only one with these issues. I gave up on GD back then, since I am perfectly happy with Recoll.

---

### Post by posterboy on 2007-09-21
Just to voice another opinion, I too was much impressed with recoll. Worked just great. however, I did wind up abandoning it for beagle.

---

