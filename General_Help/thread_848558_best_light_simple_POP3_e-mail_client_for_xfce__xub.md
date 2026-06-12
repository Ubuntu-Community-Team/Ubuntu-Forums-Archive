---
title: "best light simple POP3 e-mail client for xfce / xubuntu?"
date: 2008-07-03
forum: General Help
---

### Post by bluepowder7 on 2008-07-03
so i'm on 8.04 xubuntu, and would like a single basic pop3 e-mail client to just scan my inboxes and let me read mails.  pop3 is enough, since it's safer and if i really want to reply or get involved, i can just log in to the actual e-mail account and do the real work there.

so, what's the best, light, simple, xfce-ish client to use?  the default is thunderbird, but isn't that overkill for just pop3?

i would require:
* graphical
* can read multiple accounts
* can set refresh / check rate (global is fine, per-account would be ideal)
* very light, just check the inbox, no other folders (like sent, spam, etc)

---

### Post by HermanAB on 2008-07-03
mutt

---

### Post by bluepowder7 on 2008-07-03
hmm, mutt seems to be text based.  is there a nice yet simple gui'd version of it?

how's claws-mail?
EDIT - ok, i don't like claws at all.  my inbox had 51 messages, and yet it managed to pull in over 500, the newest of which seemed to be a year old.

---

### Post by bluepowder7 on 2008-07-04
bump - any other suggestions?

---

### Post by timzak on 2008-07-07
> **bluepowder7 said:**
> hmm, mutt seems to be text based.  is there a nice yet simple gui'd version of it?

how's claws-mail?
EDIT - ok, i don't like claws at all.  my inbox had 51 messages, and yet it managed to pull in over 500, the newest of which seemed to be a year old.

That sounds like an issue with "leave email on server" which probably has a setting in Claws.  Generally I set my email reader to delete emails from the server at the time I download them.  If you've been keeping them on the server for over a year, this is why they all downloaded.  You probably have to:
a) delete all old messages from your email server or
b) download them all to Claws and delete them from Claws after downloading.

You might have to dig around in the Claws settings and preferences.

I've never used Claws, but it's supposedly what you are looking for.  I have tried Sylpheed (a relative of Claws) on Windows and it seems to be about on par with Outlook Express 6 in terms of "lightness" (that is, it is very light on system resources compared to Thunderbird).

Good luck.

---

### Post by sujoy on 2008-07-07
i am using claws, with gmail
and in gmail settings theres an option that lets you download all messages in inbox or just the ones arriving afterwards

---

### Post by bluepowder7 on 2008-07-07
ok, yes my two accounts are with GMail, but on each of those accounts, the actual INBOX on the GMail side is no more than 50 messages.  the rest are all filed and archived into the "all-mail" folder with whatever tags and labels i want.  so, the INBOX is not 500 items long, but 50.  also, the INBOX has recent messages, and not stuff that's at least 1 year old.  that's the weirdness i'm seeing with Claws - it pulls in 500+ messages from what it thinks is GMail's inbox, yet there's at least 1 year old and don't match up with anything that [www.gmail.com](www.gmail.com) shows me i have.

so, i dunno, i installed Claws and set up the 1st account just to check it out, and got an instant "WTF?" reaction.

oh, also, i don't want to delete messages from the server - i just want a client that'll say "hey, this is what's currently in your account's INBOX, read it and if you wanna reply or delete it, go to the webmail version cuz i'm just a stupid reading client and all i can do is read - i can't send or delete or touch your server stuff at all"

---

### Post by Olav on 2008-07-07
> **bluepowder7 said:**
> oh, also, i don't want to delete messages from the server - i just want a client that'll say "hey, this is what's currently in your account's INBOX, read it and if you wanna reply or delete it, go to the webmail version cuz i'm just a stupid reading client and all i can do is read - i can't send or delete or touch your server stuff at all"
You probably want a client that can handle the IMAP protocol (Claws does). Then it will still let you send mail, but you can configure it so that it puts your sent mail into a folder of the remote mailbox as well - so you will keep all your mail in a centralised location (I gather this is what you worry about).

---

### Post by bluepowder7 on 2008-07-07
> **Olav said:**
> You probably want a client that can handle the IMAP protocol (Claws does). Then it will still let you send mail, but you can configure it so that it puts your sent mail into a folder of the remote mailbox as well - so you will keep all your mail in a centralised location (I gather this is what you worry about).

well, all i want it to do is read, nothing more - which is why i'm thinking POP3 is the safe way to go (i've been known to make the odd mistake).

i'd feel a whole lot more comfortable with an unintelligent-POP3 interface than with an IMAP just in case i bugger up a setting or it gets autobuggered (somehow) - i dunno, a stray quark sneezes on my hard drive and rearranges the machine-alphabits.

if claws is as light as it gets in the GUI realm, then i might just scrap the whole idea.  pity, as it seems like such a simple task - use POP3 to do read-only on my inbox (and only inbox, no other folders).

---

### Post by timzak on 2008-07-08
Sylpheed is lighter than Claws.  Have you tried it?  It's very similar looking to Claws, but stripped down even more.  According to Synaptic, claws-mail uses 3117 kB of disk space while Sylpheed uses 1507 kB.  The latest version of Sylpheed is 2.5.0, but Hardy's repositories have 2.4.8.  At least with Claws, you can use their custom repository to get the latest version (3.5).

Edit:  there is a setting in Sylpheed called "Download all messages (including already received) on server"

I wonder if leaving this unchecked will get what you are looking for.

---

### Post by bluepowder7 on 2008-07-08
ok, this is retarded.  downloaded and installed sylpheed, so it also downloaded and installed claws-mail (why!?!?!?)  and now of course there's no menu item for sylpheed, but there is one for claws.  only way to start sylpheed is from the terminal, but then closing terminal closes sylpheed.  and of course sylpheed runs into errors when trying to connect to the gmail servers, and doesn't tell me much else.

irritating and annoying.  screw this, i'm giving up on this stuff.  and of course claws is yet again trying to download 391 (very old) messages from my inbox on gmail, which only contains 51 (new and recent) messages.  and there's no way to stop or cancel it.  piece of crap!!!

i just tried thunderbird, and i get the same ridiculous results - 471 messages downloaded, all from 2005 and 2006.  hello?  it's 2008 now!!!  where the deuce are my CURRENT messages???

---

### Post by apmcd47 on 2008-07-08
> **bluepowder7 said:**
> 

irritating and annoying.  screw this, i'm giving up on this stuff.  and of course claws is yet again trying to download 391 (very old) messages from my inbox on gmail, which only contains 51 (new and recent) messages.  and there's no way to stop or cancel it.  piece of crap!!!

i just tried thunderbird, and i get the same ridiculous results - 471 messages downloaded, all from 2005 and 2006.  hello?  it's 2008 now!!!  where the deuce are my CURRENT messages???

Presumably you are so fed up you won't even read this thread now I'm putting my oar in? I'll put it in anyway.

Okay, I don't know much about Google Mail but I'm guessing that the POP server is giving your clients all your mail. Do as a previous poster implied and go to your google mail settings and select "Enable POP for mail that arrives from now on".

Secondly, every time you use a NEW client it will download ALL the messages in your server's inbox. Only on the second and subsequent connections will it pick up new messages. So every client you try will start from the same place.

Thirdly, you are using XFCE. I know there is a panel plugin for monitoring email. Does that do what you want? Probably not, but I know Korn for KDE allows you to read messages (but I don't think it will monitor POP mailboxes; I think the XFCE one does), so try it.

I hope you haven't given up and have another look at this thread. I hope my advice here does help you and you have a better experience as a result.

Andrew

---

### Post by bluepowder7 on 2008-07-08
i'm quite fed up, but mosty utterly baffled and confused as to why it would be pulling in hundreds of messages even though my gmail inbox clearly has no more than 60.  it appears that it's pulling from the "all mail" folder, and not "inbox" folder.  and if all three clients are doing that, then it's useless and a massive waste of time (downloads 4000+ messages, even though i just want the 50 in "inbox")

now, i COULD enable "mail from now on" on the gmail side of the fence, but that wouldn't show me the older messages that i still keep in my inbox for quick reference or to (eventually) follow up on - which of course means i need to come right back to webmail.  i also have filters set up to auto-file stuff, and if the POP clients just read my "all mail" folder, then they'll show me the auto-filed stuff too - which i don't want to see (which is why i auto-file them in the first place)

yeah, that Xfce mail panel plugin thing is here, but all it does it give me a message count - 4 unread in this inbox, and 7 unread in that inbox.  it doesn't give anything else.  so, nice, but much too limited.

IF (and this is a big if) there was a client that would quite simply read ONLY the contents of what is in gmail's inbox (and specifically inbox, not sent, not all, not drafts), then i'd be thrilled.

---

### Post by bluepowder7 on 2008-07-08
eh, update?  i submitted my "wtf is going on?" on gmail's discussion board, and it seems the problem (dare i say MAJOR FAWKUP) is on gmail's side - it seems that their POP server doesn't look at inbox when being told to get new messages from inbox - it looks at allmail!  what the deuce!?!?

so, my apologies to you all and to the mail clients.  the (not officially confirmed, but my test using thunderbird supports this) fault appears to be entirely with gmail and their code writer.  ugh!  i don't write code, but COME ON!!!!  a dead money with a broken stick could have written THAT part better...

i'll update this thread when i get more details from the gmail discussion board.  i'm NOT holding my breath!  :P

---

### Post by timzak on 2008-07-09
I'm glad you at least know why this is happening!  If Gmail fixes this problem, give Sylpheed another try, but first uninstall Claws.  My impression is that Sylpheed and Claws use the same code base (maybe that's why you had that mixup after installing Sylpheed), but Claws developers have worked more on plugins for added functionality while Sylpheed developers are keeping it as simple and lightweight as possible.

Claws has a repository set up that will give you the latest version through Synaptic.  Otherwise, the version that Ubuntu provides is fairly old.

Sylpheed has no such repository, so you are forced to use what Ubuntu provides - currently version 2.4.8.  The latest version is 2.5.0.

Good luck.

---

### Post by Gryllida on 2013-02-05
Sylpheed is lightweight, simple, and it has default setups for each e-mail host. You type gmail, enter username and password, and it works. :)

---

### Post by oldos2er on 2013-02-05
Old thread closed.

---

