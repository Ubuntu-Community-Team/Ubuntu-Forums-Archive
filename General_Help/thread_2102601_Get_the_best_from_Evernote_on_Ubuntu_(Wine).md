---
title: "Get the best from Evernote on Ubuntu (Wine?)"
date: 2013-01-07
forum: General Help
---

### Post by sberla54 on 2013-01-07
Hello guys.
Evernote has become an important tool for my work, but i've very limited by the lack of a good Linux client (i'm on 12.04).

I've tried the two availables and them both have major problems: Everpad ([https://github.com/nvbn/everpad](https://github.com/nvbn/everpad)) is for a very basic user, because tags are managed very poorly, the editor is limited and it slows the launcher down; NixNote ([http://nevernote.sourceforge.net/](http://nevernote.sourceforge.net/)) is better but is still limited and bugged in tag usage, sometimes has weird problems with Evernote formatting and it often crashes or freeze.
The official Evernote web interface is simply too slow and i hate it.

So, i'm stuck with the Windows Evernote Client (4.5.6.6884) under Wine (1.5.5), installed using PlayOnLinux because without it i wasn't able (or Evernote didn't sync).
Anyway, it's far from perfect...

A couple of problems: 
- Tray icon disappear and works weird
- Special keys get locked on (for Wine i'm keeping the Alt button pressed but i'm not...)
- Notes scrolling is too fast (so i always miss the stuff i'm searching for...)
- The interface isn't fitted in Unity (for not saying is a punch in an eye)
- The fonts are from Windows, so they are often hard to read and i'm not used to them, which bothers me (a lot...)
- It is quite slow to start

I don't upgrade the Windows Evernote Client because i'm not skilled with Wine, i (think i) have to re-install Evernote every time and i'm always worried that something strange won't work...

I'm about to tie me to Evernote even more, because i'm migrating a lot of job documentation and general notes to it, but i would like to improve the usability before starting this job.

Do you have any suggestions?
Is there a way to make NixNote working perfectly? It would have pretty everything i need, if it only wasn't so full of bugs...i'm using version 1.4 from Launchpad.. 
Are there any other Linux clients i didn't mentioned?
Do someone of you use Windows Evernote Client under Wine and has discovered something that improve his usability under Ubuntu? All tips are welcome!

Thank you in advance! This would be a really important issue to fix for me!

---

### Post by Bucky Ball on 2013-01-07
Have you tried Zotero? It runs as an add on to Firefox or standalone (not both at the same time, though).

There is add-ons for Open Office and Libreoffice which make referencing a breeze. Very versatile and gets better all the time.

[http://www.zotero.org/](http://www.zotero.org/)

---

### Post by tgalati4 on 2013-01-07
I like zotero as well, but I'm not aware of an Android client, but I haven't look lately either.  Perhaps send an email to the Evernote developers.  They seem to want feedback, so let's get proactive and get a better evernote client for linux!

---

### Post by orb9220 on 2013-01-08
Tried all those and agree sourly lacking for evernote.
This one is new for evernote but a cli driven interface
.
[Geeknote Work with Evernote from command line]("http://www.geeknote.me/")

And I use evernote web clipper for firefox. Which helps with lack of at least with a lot of notes,text,links on the web.
.

---

### Post by sberla54 on 2013-01-08
>  		Have you tried Zotero? It runs as an add on to Firefox or standalone (not both at the same time, though).

I didn't know it. It seems pretty cool but, sadly, in my company everybody use Evernote: we share notes and documentation in Evernote format and so on...

I really need and Android client too. I use it for everything, from reading my shopping list at mall to look at servers documentation when i'm in data center...

> Perhaps send an email to the Evernote developers.  They seem to want  feedback, so let's get proactive and get a better evernote client for  linux! 	

I'm gonna do it but i'm sure a lot of other people already do it....
I've already asked for a Linux client on Facebook and Twitter a couple of times :)

>  		Tried all those and agree sourly lacking for evernote.

What do you use? Only Geeknote?

---

### Post by orb9220 on 2013-01-08
> Tried all those and agree sourly lacking for evernote.

What do you use? Only Geeknote?
Nope not even that as am more a gui type guy. And sadden would love a evernote desktop widget kind of based on the android version would be cool and useful to me.

Nixtnote: Just way to much java hog and cumbersome. And leaves Evepad in tray for quick things. And evernote web clipper for firefox is real dandy for a lot of snagging text,links,web pages.
.

---

### Post by tgalati4 on 2013-01-08
I use zim for internal notes.  I have one copy of zim on a server and I run it via an launcher:  (ssh -2 -Y tgalati4@homeserver zim) from all of my laptops and desktops.  This way I have one repository of notes.  This works really well as the changes show up automatically in each instance running.  Quite cool.

For stuff that I need on my Android phone, I use nixnote and a combination of web evernote clipper and web-based evernote.  Not ideal, but it works for getting stuff accessible on the phone.

I can cut and paste between zim and nixnote or the evernote webclient with ease.

I have not used geeknote, but I will check it out.

We need someone to write and host an email script that will send a form letter to evernote with a block for user comments and put a button in this thread.

---

### Post by sberla54 on 2013-01-08
> Nixtnote: Just way to much java hog and cumbersome. And leaves Evepad in  tray for quick things. And evernote web clipper for firefox is real  dandy for a lot of snagging text,links,web pages.3 softwares for the same stuff? :)
You should check out the Windows Evernote Client installed with PlayOnLinux and Wine. It's not so bad, as i've said...

I've never used Web Clipper. I've Pocket (formerly Read It Later) for saving articles to read offline and never needed a Clipper for anything else.
By the way, for which purposes do you use it?

>          I use zim for internal notes.  I have one copy of zim on a server and I  run it via an launcher:  (ssh -2 -Y tgalati4@homeserver zim) from all  of my laptops and desktops.  This way I have one repository of notes.   This works really well as the changes show up automatically in each  instance running.  Quite cool.Quite cool indeed! :)

>  For stuff that I need on my Android phone, I use nixnote and a  combination of web evernote clipper and web-based evernote.  Not ideal,  but it works for getting stuff accessible on the phone.I'm quite confident that NixNote will became what we all need. I've tried it a year ago and it really sucked hard. Now it's already much better!

Web-based Evernote is terrible. It's too slow and it has the problem that you don't have your note syncronized offline anywhere. 
Once, we had a major problem at office and our internet connection was down because of a data center problem, and i found myself without any documentation that could help me solve the issue.

>  We need someone to write and host an email script that will send a form  letter to evernote with a block for user comments and put a button in  this thread.     I don't know how much Evernote staff could care about Linux users, considering that they've made no effort 'till now to make a Linux client, but it is a nice, annoying (for them) idea.
I support it! :)
Someone is able to do it?

---

### Post by tgalati4 on 2013-01-08
How about a poll and then send a single email pointing them to the poll results.  Then keep sending the poll results every month.  They can't ignore us forever.

---

### Post by orb9220 on 2013-01-08
> 3 softwares for the same stuff?

Nope just everpad & web clipper extentsion.

> You should check out the Windows Evernote Client installed with PlayOnLinux and Wine. It's not so bad, as i've said...

Yep maybe if comes to that. Tho trying to stay win free.

> I've never used Web Clipper. I've Pocket (formerly Read It Later) for saving articles to read offline and never needed a Clipper for anything else.
By the way, for which purposes do you use it?


[Web clipper extension]("http://evernote.com/webclipper/") allows me to clip just some text or clip an image within the page or the whole page with links to it. And all sync to evernote account so don't need an additional program like pocket. 

And yep don't do the web page based evernote account but find web clipper useful for gather info on the internet. Can copy and paste large clips of text then put in notebooks like linux commands. Or a Solution to a problem kind of thing. Works for me.
.

---

### Post by sberla54 on 2013-01-12
> **tgalati4 said:**
> How about a poll and then send a single email pointing them to the poll results.  Then keep sending the poll results every month.  They can't ignore us forever.

That would be the easiest choice.
Are we going to do it?

> [Web clipper extension]("http://evernote.com/webclipper/")  allows me to clip just some text or clip an image within the page or  the whole page with links to it. And all sync to evernote account so  don't need an additional program like pocket. 

Thank you, i'll give it a try.

Anyway, so we have no real solution to the lack of a good Linux Evernote client, have we?

What about sharing tips for making NixNote or even the Windows Client more usable and reliable?

---

### Post by sberla54 on 2013-01-19
By the way, i've reinstalled Everpad. 
I must say it's pretty usefull when you have to read a note quickly, and the editor is good enough to write new notes, even if you always have to organize tags and other stuff with the Windows client.

Anyway, everpad-provider keep crashing, once a day...

---

### Post by tgalati4 on 2013-01-19
Only the original poster can create a poll in this thread.  A simple question:

Do you want an Evernote Linux Client?  Yes, No, Maybe, Don't Use Evernote, What is Evernote?

---

### Post by Martinjo84 on 2013-01-19
Evernote is the primary program i miss :(
I used to pay for my account

---

### Post by sberla54 on 2013-01-20
> **tgalati4 said:**
> Only the original poster can create a poll in this thread.  A simple question:

Do you want an Evernote Linux Client?  Yes, No, Maybe, Don't Use Evernote, What is Evernote?

Sorry. I know you are gonna think i'm stupid but i've searched everywhere and i really can't find where to add a poll to this thread.
Could you please help me?

---

### Post by Mark Phelps on 2013-01-20
If you're going to use Evernote with Wine, looks like version 4.6 is the way to go.  The older versions fall off rapidly in usefulness:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=2566]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=2566")

---

### Post by Bucky Ball on 2013-01-20
> **sberla54 said:**
> Sorry. I know you are gonna think i'm stupid but i've searched everywhere and i really can't find where to add a poll to this thread.
Could you please help me?

Thread Tools at top right of this page. 'Add Poll to this Thread' ...

No, you're not stoooopid. We are all stupid and incredibily clever at once. :)

---

### Post by sberla54 on 2013-01-20
> If you're going to use Evernote with Wine, looks like version 4.6 is the  way to go.  The older versions fall off rapidly in usefulness:Thank you!
I'm still using 4.5...i'll try an upgrade...

> Thread Tools at top right of this page. 'Add Poll to this Thread' ...It seems like i can't...

[IMG]http://i.imgur.com/As24MxB.png[/IMG]

Maybe because i've only got 22 posts? I can't even change my personal profile..

---

### Post by tgalati4 on 2013-01-20
I made a poll and it can be found here:  [http://ubuntuforums.org/showthread.php?t=2106962](http://ubuntuforums.org/showthread.php?t=2106962)

Moderaters can merge the threads if they desire.

---

### Post by sberla54 on 2013-01-21
Voted! Thanks!

---

