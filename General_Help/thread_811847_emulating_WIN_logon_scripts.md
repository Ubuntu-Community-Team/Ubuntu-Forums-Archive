---
title: "emulating WIN logon scripts"
date: 2008-05-29
forum: General Help
---

### Post by SteveHillier on 2008-05-29
I have had a quick search of the forum but, as always, cannot see anything that is identical to what I am trying to do.

I am trying to get this Hardy machine to act as a workstation on my Win 2003 domain (but that is just a start - I might start promoting it wider now that MS are withdrawing XP and Vista for Business is just a pig and if I can get rid of Windows clients all well and good - stop to draw breath).

I am used to mapping drives in a logon script (batch file) along the lines of 

NET USE X: \\server\share /persistent:no

and this allows a consistent set of drive labelling across the system, but there is a further rub.

In Active Directory on the profile tab I map the user's private drive using the command 

\\server\users\%username%

which of course maps to 

U: \\server\users\fred (or bill or jim etc)

I do this this way because (from memory - I will need to check) Windows does not pass the variable %USERNAME% to the batch files.  For example I think you are not able to put up a message similar to 

Welcome Janice, you logged on today at 14:87

where Janice has been substituted for %USERNAME%

I have tried mounting volumes using the 'connect to server' command in Hardy but it maps to the \\server\users share and ignores the username bit.  Under Win 2003 these private folders are not shared only the parent directory and therefore presenting the user with all the other users private folders is not really such a good idea.

So am asking the community if anyone has done this sort of thing and if so have they any ideas they are happy to share.

---

