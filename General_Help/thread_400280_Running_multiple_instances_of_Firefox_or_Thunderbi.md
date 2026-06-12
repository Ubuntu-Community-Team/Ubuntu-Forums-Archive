---
title: "Running multiple instances of Firefox or Thunderbird"
date: 2007-04-03
forum: General Help
---

### Post by mkljun on 2007-04-03
Hi!

I just wanted to post a solution on how to run multiple instances of Firefox or Thunderbird. I found some solutions on the web on how to do it in MS Win OS. So I wrote a similar script for Linux. Executing this script brings up a Profile manager window from which another profile can be selected even if another instance of FF or TB is already running, 

# gedit start_ff_with_profiles

Paste in this code, save and exit Change the location of FF command (/usr/bin/firefox) if it resides in a different directory than mine. The similar goes for TB. Change the execute command with the TB one (/usr/bin/mozilla-thunderbird on my system).

#!/bin/sh
export MOZ_NO_REMOTE=1
/usr/bin/firefox -profilemanager
export MOZ_NO_REMOTE=0

# chmod u+x start_ff_with_profiles
# ./start_ff_with_profiles

A Profile Manager window pops up and you can start creating as many profiles as you want. And you can start a new FF with executing start_ff_with_profiles again. The only limit is that multiple instances with the same profile can not be opened. But this seams normal :).

A launcher (gnome users) can be made as well.
1. Click on the empty desktop space with mouse right button;
2. Select "Create Launcher"
3. Leave "Aplication" selected
4. Enter a name for new launcher like "Firefox"
5. Enter a command which is a full path to our "start_ff_with_profiles" file
   /path/to/start_ff_with_profiles
6. Click on OK button.

I'm using it for my home PC where me and my wife use the PC almost all day long, And as switching users take time we both use the same user space. And we need two instances of TB and FF running. 

Another example is a friend of mine who uses one profile for RSS/Newsgroups and another for email. This way the email profile is separated from Newsgroups and RSS and they do not mix up.

Hope this helps someone.

lp mk

---

### Post by mirzmaster on 2007-06-11
There is actually an easier way to launch multiple instances of Firefox:

```
/usr/bin/firefox -p -no-remote
```

Using the -no-remote argument is equivalent to setting the MOZ_NO_REMOTE env. variable.

---

### Post by yannn on 2007-07-10
i used the described method to run multiple instances of thunderbird and it works fine. i'm experiencing a (quite common) problem after changing, though:

clicking on a link in tb i get the message "Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system."

i searched for the problem but i couldn't find a solution for this specific situation. i suppose it has to do with the MOZ_NO_REMOTE variable, but i don't know. any ideas?

---

### Post by yannn on 2007-07-18
i forgot to say that the problem only occurs when firefox is already running. if not, it is opened after clicking the link in tb.

---

### Post by dagnabit dang doohickey on 2007-07-18
I run Firefox 2 and Firefox 1.5 side-by-side with no problem using launchers with the following commands:
```
firefox.two -no-remote -P Firefox-2.0
```
```
firefox.onefive -P Firefox-1.5
```
I renamed the symlinks and profiles rather obviously for no other reason than to just make them, well, obvious.
The -no-remote flag is required for FF2 when launching FF2 after FF1.5, else it just has the effect of opening a new window in FF1.5. The -no-remote flag doesn't apply to FF1.5, nor have I have any problem launching it after FF2.

---

### Post by yannn on 2007-07-28
ok, i don't quite get this. when i use the following, i can start several instances of thunderbird but i cannot open links in firefox (see problem description above):

```
export MOZ_NO_REMOTE=1
/usr/bin/mozilla-thunderbird -P <profile-name>
export MOZ_NO_REMOTE=0
```

if i start the first instance by

```
/usr/bin/mozilla-thunderbird -P <profile-1>
```

and the second using

```
export MOZ_NO_REMOTE=1
/usr/bin/mozilla-thunderbird -P <profile-2>
export MOZ_NO_REMOTE=0
```

both open up, but i can only open links from the first instance. isn't that weird?

---

### Post by mkljun on 2007-07-31
I'm experiencing the same problem. But I can live with it. 
I simply copy the address|link|URL in TB and paste it to FF. 

If you find a sollution I'll be more than glad since my digging brought me back to my post ;).

The funniest part is that I used the same solution on my sister's pc (MS Windows) and created a batch file
with following content

```

@echo off
set MOZ_NO_REMOTE=1
start "" "C:\Program Files\Mozilla Thunderbird\thunderbird.exe" -profilemanager
set MOZ_NO_REMOTE=0

```

And clicking on link in TB opens up FF normally.

lp mk

---

### Post by yannn on 2008-03-02
I'm still having the same problem (links are not opening in ff). Any more ideas on this?

---

