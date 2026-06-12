---
title: "I can't log in"
date: 2014-08-06
forum: General Help
---

### Post by eli_fabrikant on 2014-08-06
Hallo dear people,
my ubuntu 13.10 won't log me into a session all of a sudden. When I turn the computer on all looks OK untill it reaches the screen where I can choose between logging in with my user name, or going to a guest session or a remote login. When I type in my password it just doesn't react, it doesn't take me to desktop like always. The bar into which I just typed my password disappears but nothing happens. When I press ESC the password bar appears again. When I type in a wrong password it reacts and says I've typed in a wrong password. When I try logging in as a guest, it also ignores my requests and just stays in this screen, unresponsive.
I thought it was the fault of one of the recent updates that I made, but when I tried to choose a previous 13.10 version through the GRUB menu, the same happens everytime. I tried doing dkpg and apt-get update through the safe mode, but that didn't help either.
I'm lost ! Any suggestions ??
Thanks so much !
Eli

---

### Post by Bashing-om on 2014-08-06
eli_fabrikant; Hey !

> 
 I tried doing dkpg and apt-get update through the safe mode, but that didn't help either.
I'm lost ! Any suggestions ??
Thanks so much !


Release 13.10 is End_Of_Life and has no support, the software repository has been turned away, and no longer exists as you know it.

There is no point now in attempting to fix this old install ;
The better thing at this time is to do a fresh clean install of a supported release ( 12.04, 14.04 ).

Else:
There does exist a means to upgrade on-line, if that is required.
see:
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

[INDENT][INDENT]my little bit to try and help
[/INDENT][/INDENT]

---

### Post by eli_fabrikant on 2014-08-07
Hallo again,

Bashing-Om, thanks for your help. I wouldn't mind doing a fresh install or an upgrade, but I can't manage that.
 I can't use the update manager to do that because I can't log in.
 I can't do it through a terminal as well. I can only get to a command line either before booting, through the GRUB menu  (logged as root , there I can't seem to do any operations like apt-get. maybe because I'm not connected to the internet at that stage ?) or through the safe mode where I can only get a command line through choosing the 'Drop to root shell prompt'. Same problem there.

How do I fresh install or upgrade without being logged in ? Is it possible ?
Otherwise, the only option that is left is to format the computer and force a new install, but then I will loose all of my data...

Any ideas ??
thanks again !
Eli

---

### Post by Bashing-om on 2014-08-07
eli_fabrikant; Weeelllll.

What results when at the normal login screen;
You press the keycombo ctl_alt+F1 .
Are you now at a text terminal ?
Can you log into the system from this prompt ? -> enter your "username" followed by your password ( no response to the screen when pass word entered; enter password blindly).

If you are able to get to this point, we can advise you on making that  on-line upgrade to release 12.04 ( then onto 14.04 if desired); as a GUI is not required to make that upgrade happen.

Else: we will have to work to get you to this point .
the tutorial:
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)
still applies.

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]all things are possible
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by eli_fabrikant on 2014-08-08
Dear Bashing-om,

this simple yet genius command ctrl_alt_F1 did take me to the terminal and from there I could do a regular upgrade. Thanks so much !
one little point though, the tutorial to which you refered me is out of date. It suggest a command called aptitude, which my terminal doesn't recognise.

many many thanks again !!!
Eli

---

### Post by Bashing-om on 2014-08-08
eli_fabrikant; Great !

Things are looking up !
Yeah, somewhat dated, as all things 'buntu - fast moving target ! Aptitude - though a great tool - is no longer installed by default ( a steep learning curve). It is but one other interface into the package management system .

If this matter is now at an end:

Please mark this thread solved;
 aides others seeking the solution, 
helps keep the forum clean and 
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Then I will say
[INDENT][INDENT][INDENT]happy trails to you
[/INDENT][/INDENT][/INDENT]

---

