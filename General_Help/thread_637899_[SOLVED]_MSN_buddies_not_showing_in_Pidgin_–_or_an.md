---
title: "[SOLVED] MSN buddies not showing in Pidgin – or any other IM program"
date: 2007-12-11
forum: General Help
---

### Post by itsjustarumour on 2007-12-11
Greetings All,

(I&#8217;ve previously brought up this problem having got side-tracked on another thread in the &#8220;Absolute Beginner Talk&#8221; section, so apologies for double-posting but I thought it belonged better in this section.)

Long story short &#8211; my MSN buddies aren&#8217;t showing in Pidgin, or any other IM program

My problem started 2 days ago, when I noticed my MSN contacts in Pidgin (from the main Gutsy repos) were behaving strangely.  I suspected that changes to my display name weren't updating, and that I was showing as "offline" to other MSN users. I deleted and re-added the MSN group and then discovered I couldn't get my MSN buddies to show up again. Reinstalling Pidgin didn't help.

Yesterday I tried installing Pidgin 2.3.0 from the GetDeb website, and also 2.3.1 from the Linux MINT website at [http://www.linuxmint.com/forum/viewt...hp?f=47&t=7177](http://www.linuxmint.com/forum/viewt...hp?f=47&t=7177) (this how-to states its 2.3.0, but its actually 2.3.1). Everything worked perfectly except MSN - buddies didn't appear in the buddy list (Yahoo and AOL buddies appeared fine). Also, the MSN "mail-checker" told me I had 10 emails in my Hotmail account, and I could click on the link to access them OK.

I've since tried installing the latest stable versions of Emesene IM, Kopete and aMSN, and get exactly the same problem with all of these.

So &#8211; is this an MSN protocol issue?  Or is there something seriously broken on my Gutsy?  I read a few posts where &#8220;MSNP13&#8221; and &#8220;MSNP14&#8221; were mentioned, but I&#8217;m a bit lost on the significance of these.  Anybody else having these same problems?

Any wisdom or help gratefully received!  :-)

Best Regards,

itsjustarumour

---

### Post by ajgreeny on 2007-12-11
Try uninstalling pidgin completely and then also removing or renaming the .purple folder, which is where pidgin keeps its config files, in your /home/username.  It is perhaps a problem of configuration of the IM progs that is causing the difficulty.

---

### Post by itsjustarumour on 2007-12-11
> **ajgreeny said:**
> Try uninstalling pidgin completely and then also removing or renaming the .purple folder, which is where pidgin keeps its config files, in your /home/username.  It is perhaps a problem of configuration of the IM progs that is causing the difficulty.

Hi ajgreeny,

Thanks for your post, I've just given that a try - but still have the same problem!

Any other ideas?

EDIT - just for the record, I've not made any other changes to my system since Pidgin was working fine, apart from the standard official Ubuntu updates.  Also haven't made any changes to Firewall settings etc - and Yahoo and AOL do work just fine, it just seems to be MSN thats the problem...

I'm also guessing that if this was a protocol issue the forum would be buzzing with other peeps having the same problem by now.  This just seems weird!

---

### Post by itsjustarumour on 2007-12-11
BUMP - anyone?

---

### Post by itsjustarumour on 2007-12-11
Bump..

---

### Post by itsjustarumour on 2007-12-11
Hmmm, still trying.  I've reinstalled Pidgin 2.2.1 from the Gutsy repos again, and uninstalled my Firewall (Firestarter) just in case this was causing a problem, but no joy.

Another weird thing is, if I go into /home/(my username)/.purple and open blist.xml all my MSN contacts are listed in there, so Pidgin has successfully connected to my MSN account and pulled up this list, it just can't do anything with them... 

:confused::confused::confused:

---

### Post by itsjustarumour on 2007-12-12
Bump

---

### Post by Sef on 2007-12-12
Download amsn; it is in add/remove.  Just be sure and set the top bar to all available applications.    This way you can chat while you resolved the pidgin problem.

---

### Post by itsjustarumour on 2007-12-12
> **Sef said:**
> Download amsn; it is in add/remove.  Just be sure and set the top bar to all available applications.    This way you can chat while you resolved the pidgin problem.

Hi Sef,

Thanks for your reply.

I downloaded aMSN but I still get the same problem as with Pidgin (and also Emesene and Kopete!) 

I am logged in to aMSN OK and I am actually connected to MSN (it even tells me I have 13 messages in my Hotmail Inbox!) but my MSN buddies list is empty - it shows Online Buddies as "0" and also Offline Buddies as "0". I've spoken to a couple of my friends on the phone, they can see that I am online and when they try and message me I even get a "toaster popup" at the bottom of my screen with their message!  But whatever I do, I just can't get any of my MSN buddies to appear in my buddies list (buddies from AOL, Googletalk, ICQ etc all appear fine though!)  This is just weird!!

Any other suggestions?  :)

---

### Post by itsjustarumour on 2007-12-12
Btw - heres a pic of my Pidgin to prove I'm not going mad!  There should be about 12 buddies in my MSN list, of which at least 3 are currently online.  As you can see, I'm online and connected to MSN as I have 13 emails showing, also I'm connected to AOL fine and have 1 of my 3 AOL buddies online.  

If I go into the Accounts menu, both MSN and AOL show as "Enabled".  And under the Buddies menu if I go to "Show", I have everything ticked to be visible.

Also, if one of my online MSN buddies initiates a chat with me, I can click on the "toaster popup" notification and open up a chat window, and have a normal chat conversation.

But whatever I do, I just can't get my MSN buddies to show up in my MSN list!  (And my MSN buddies still won't show up in aMSN, Emesene or Kopete either!)  

I've tried uninstalling and reinstalling Pidgin several times now, including removing  the config files in the .purple folder in my /home/(username) directory...

Sorry about the kitten btw, he gets everywhere ;-)

---

### Post by itsjustarumour on 2007-12-12
Bump.

---

### Post by itsjustarumour on 2007-12-20
Well, I finally cured this myself.

My solution - give up on the Linux, take the side panel off my machine, unplug and remove hard drive containing Ubuntu, plug in hard drive containing Windows XP, and log into MSN Messenger.

But you didn't really think I'd abandoned Ubuntu, did you ;-)

I put my Linux drive back in, clicked on the icon and Pidgin/MSN worked perfectly first time!

Its a bit bad that a Linux app can only be fixed by using the Windows XP version, I think!

I have no idea what software/protocol trigger caused this, but thinking about it I suddenly remembered having exactly the same problem with Yahoo contacts about 18 months ago in GAIM Beta 3 - and the problem cured itself after I logged into Yahoo IM on my XP box.

Weird!! :confused::confused:

---

