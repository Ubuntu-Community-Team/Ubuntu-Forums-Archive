---
title: "Firefox doesn't close properly in Gutsy 7.10"
date: 2008-06-06
forum: General Help
---

### Post by StewartM on 2008-06-06
Hello all,

I'm running Gutsy 7.10 on a Dell Inspiron 1525N laptop (essential hardware listed on the Dell site, if it's of interest) just recently purchased. I also use Scramdisk for Linux version 1.3-0 to which I have containers (formatted in ext3) copied from a Feisty 7.04 machine which were created using a previous version of Scramdisk (but still should be compatible). I direct Firefox to look for my user profiles within the encrypted containers. 

On my Feisty machine (until it was murdered recently, great sadness :() there were never any problems. However, on my new Gutsy machine, it seems that I'm experiencing:

a) more hangups (like 20 seconds to a minute) on loading web pages (ok, this could be at the web server end) but which nearly freeze up my system. It does this even though a quick look at the system monitor does not show high RAM or CPU usage. 

b) A lot of times when this happens (but even when it doesn't) when I close Firefox and restart it I get a "Firefox is already running, you must either close Firefox or restart your system" error. In the system monitor it does not show Firefox running. 

When I open the terminal and type in:

ps -e -a

thinking that I might see Firefox listed there still running (and thus could issue a kill command) I don't see it there either. Nothing puts things right except a system restart, which is a pain and distressingly Windows-like and un-Linux-like.

c) If I do restart (or even if I don't have to restart after an apparently normal session but have turned on the machine normally and logged in) when I start Firefox I get a "Firefox was unexpected closed during the last session" error asking me if I want to start a new session or to restore the old one. I get this error message even if Firefox *did* seem to close normally at the end of last session;

d) When I dismount the normal encrypted container file after a session, to log out and shut down the laptop, the container formatted in ext3 where the folder with the profile data is listed usually has to be brutally dismounted. Even there it will not dismount until a 2nd dismount command is issued. (Previously, on my Feisty machine, that happened occasionally too, but I think there the problem was memory leaks in gaim, not Firefox, and a single brutal dismount was sufficient. Nor did it seem to affect the system adversely in any other way).

The reason why I think Scramdisk is involved in some way (and a post will be made to the Scramdisk user's group on this) is:

a) I am currently helping a married couple run their new Dell Linux 530N box, using Gutsy 7.10, without Scramdisk, and I have not observed this problem. Neither has a friend who's running Gutsy without Scramdisk on a Zareason Limbo 2440 box and who says Firefox runs "flawlessly".

b) I am experiencing another problem which seems to be Scramdisk related. My user account is the one where I use Scramdisk, my administrative rights account does not. 

When I use the new applet feature that lists the users and allows for quick switching from my admin (non-Scramdisk using) account to my user account which does use Scramdisk, there is no problem. However, when I go the reverse way using the quick switching applet, from my user account (with Scramdisk containers open) to my non-Scramdisk using admin account, four applets on the panels crash when the admin account screen loads (the quick switcher, trash, and two others--I forget but can post them later). Going from one account to another in either direction doing it the old-fashioned way--by using the "stop" button--causes no problems. This bug is *very* repeatable.

Like I said, I'll post this to the Scramdisk User's forum so that the developers can read this. FWIW, the only thing that I could be running that might be considered a plug-in is the one which allows Firefox to run Flash (to play Youtubes and such).

Stewart

---

### Post by StewartM on 2008-06-06
Several more ideas about this to bounce off everyone's head:

a) (From my local Linux guru): "Try turning off ipv6 in firefox. It seemed faster for me once I did this, the other issues I’ll have to think about a bit more."

To turn off IPv6:
Open Firefox
Type about:config in your url bar.
In the "filter" bar that appears on that "page", type IPv6.
Set network.dns.disableIPv6 to True

b) Try creating a test profile which is not set in Firefox/Mozilla default folder for profiles but is not within a Scramdisk container, and see if the problem replicates. That might distinguish between a purely Firefox problem or a Scramdisk problem;

c) Likewise, set all the profiles back in their default directory, /.mozilla, then try moving the entire /.mozilla folder to the encrypted directory. Then delete the original under /home/user and create a link under that pointing to the /.mozilla folder within the encrypted directory (which is what I do for evolution, pan, and pidgin, and it seems to work fine).

d) As these are TrueCrypt containers, download and open them with Truecrypt (the new GUI version) and see if the error repeats;

e) While I don't see this problem on two boxes running Gutsy, I hasten to add that these two boxes are desktops, not laptops, and I can see some differences just in normal operation switching between users between the two, with no Scramdisk containers open (these differences replicate on my Linux guru's friend Dell Inspiron 1525N, and he thinks they might be because the video card isn't fully supported). He says that upgrading to Hardy might then be the simplest answer.

f) Could this be a problem (at least with Firefox telling me that it's still running when Ubuntu says it's not) with Flash?

Anyway, I'd be open to more ideas. I could live with this problem if I could only figure when Firefox tells me that it can't open a new window because it's still running, even though it's closed, how to kill whatever app is causing the mischief in a terminal window. Then I could at least avoid restarting the computer, which is a pain.

Stewart

---

### Post by StewartM on 2008-06-09
Think I've solved most of this problem; it's with Adobe Flash--I had created a shortcut within the encrypted container for \multimedia on my old box, and when I copied everything to the new box I notice that Flash worked from the get-go without being formally installed. 

I first thought "hooray!" but then Friday evening I began to think  of that I might have in essence *two* \multimedia directories in my home user directory, and that this might be causing a conflict. When I looked at my home directory, this indeed was the case! 

So my testing went like this:

a) I first switched between my two accounts with no Scramdisk containers open, using the fast switching applet. As I expected, that worked like a charm;

b) then I opened the containers but started no programs, and then did the switching. Again, that worked;

c) Then I started Evolution and then checked mail and then made the switch. No problems there;

d) I repeated the process in c) with Pan and Pidgin, without incident;

e) I renamed the \multimedia folder outside the container and created a link to the one inside the container, then moved the link (renamed to "\.multimedia") under the home directory tree. 

f) Then I opened Firefox on a blank page; and switched, with no problems either direction;

g) Then I opened a page that required Flash (Youtube) and started to play the Youtube. I then made the switch...and it worked. 

:guitar:

h) Then I closed Firefox and restarted it a number of times. It started normally without asking me to reboot, even on sites that use Flash. I then deleted my redundant \multimedia directory.

I think this almost settles it, though after closing Firefox normally I still got the message that "Firefox had unexpectedly closed" and asking me if I wanted to restore my last session on my next bootup the following day. That's not much of a problem (I can always say "no" if it's limited to that) but perhaps it would be of interest what might trigger Firefox to think it had crashed at the end of a session when it did not. For that reason, I'll not close this thread quite yet. Anyone knowledgeable about Firefox error messages out there?

Perhaps there is one last test--perhaps I should deliberately "crash" Firefox by closing via the system monitor and force a quit and then restart it to see if it starts normally. (As it should).

Stewart

---

