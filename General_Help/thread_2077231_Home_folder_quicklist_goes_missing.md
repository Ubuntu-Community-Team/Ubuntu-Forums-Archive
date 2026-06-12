---
title: "Home folder quicklist goes missing"
date: 2012-10-28
forum: General Help
---

### Post by luvshines on 2012-10-28
I have been observing this defect ever since I have started using 12.04
Right-click on home folder icon in the launcher shows the different places I can choose. The moment I choose anyone of them, that folder is opened.
But now the quicklist is gone. I am only left with 2 options - 'Home Folder' and 'Unlock from Launcher'

If I logout and login again, quicklist appears again. But I can use it only once, as explained above

Any ideas how to debug/fix this ?

---

### Post by luvshines on 2012-10-29
**[color="red"]bump ??[/color]**

---

### Post by COMECON on 2012-10-29
You could try adding the **unity sru** PPA. I used to add it on 12.04 (before of 12.04.1) and lots of bugs were fixed. I'm not sure if it has a fix for this, but you could give it a try.
First, add the PPA:
```
$ sudo add-apt-repository ppa:unity-team/sru
```
Then update and upgrade:
```
$ sudo apt-get update && sudo apt-get upgrade 
```
When I used it, for some reason the changes only applied when I updated via the update manager... so after doing that you could check if you have any update available on the Update Manager.
I hope it works for you!
~comecon

---

### Post by luvshines on 2012-10-30
I tried it today. Still the old issue persists, I can use the quicklist only once :confused:

---

### Post by COMECON on 2012-10-30
Meh, I don't know any other solution at the moment... You should report a bug on [launchpad]("https://launchpad.net/unity"), maybe?

---

### Post by luvshines on 2012-11-16
Anyone ??

I am still trying to find a fix.
Saw a couple of bugs around this, commented in one of them but nothing turned out.

---

### Post by luvshines on 2013-01-11
Bumping it yet again

---

### Post by mc4man on 2013-01-11
No idea (yet?

1st. try placing a copy of nautilus-home.desktop in your home folder. Might as well use this one to start

```
mkdir -p ~/.local/share/applications && \
gedit ~/.local/share/applications/nautilus-home.desktop
```

copy & paste this in, save, log out/in. What happens?

```
[Desktop Entry]
Name=Home Folder
Comment=Open your personal folder
Exec=nautilus %U
Icon=folder
Terminal=false
StartupNotify=true
Type=Application
OnlyShowIn=GNOME;Unity;
Categories=GNOME;GTK;Core;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=nautilus
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Version=3.0.0
X-Ubuntu-Gettext-Domain=nautilus
Actions=Window;

[Desktop Action Window]
Name=Open a New Window
Exec=nautilus
OnlyShowIn=Unity;


```

---

### Post by luvshines on 2013-01-11
A bit of background on this:

I originally followed this link [http://askubuntu.com/questions/35488/what-custom-launchers-and-unity-quicklists-are-available](http://askubuntu.com/questions/35488/what-custom-launchers-and-unity-quicklists-are-available)
and added the 'Home icon quicklist' thing as explained

Then I changed the Icon to "Icon=user-home" since I wanted that icon on home folder thing

But then noticed that quicklist suffered from issue I have mentioned here. So I thought maybe the things I added from that link have messed it up.

I got rid of it(deleted it) and just changed the Icon thing in the original location /usr/share/applications/nautilus-home.desktop

So I got the home icon but the quicklist still suffers from that issue.

I have even tried dumping the original file from another Ubuntu install. Both at original and the ~/.local/applications locations, but none works

I thought maybe this launchpad bug [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/958900](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/958900) matches my case, but this has expired a couple of days ago

An interesting finding was that if from a terminal, ```
#I quit nautilus using
'nautilus -q'
#and then restart it with
'nautilus -n'
``` quicklist start working normally. That is I no longer experience the issue if I kill and restart nautilus

---

### Post by mc4man on 2013-01-11
What icon you use should have no effect on this, I've always used Icon=user-home till recently on 13.04 where using the new files icon
(in 13.04 they've decided to revert the silly decision to use 'folder' rather than 'user-home'

Could you post  your nautilus-home.desktop (preferably from  ~/.local/applications, maybe we'll try a little test with it 

Atm I don't have a 12.04 install, was thinking about putting one in..

---

### Post by luvshines on 2013-01-11
Here the file dump
```
[Desktop Entry]
Name=Home Folder
Comment=Open your personal folder
Exec=nautilus %U
Icon=user-home
Terminal=false
StartupNotify=true
Type=Application
OnlyShowIn=GNOME;Unity;
Categories=GNOME;GTK;Core;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=nautilus
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Version=3.0.0
X-Ubuntu-Gettext-Domain=nautilus
Actions=Window;

[Desktop Action Window]
Name=Open a New Window
Exec=nautilus
OnlyShowIn=Unity;
```

I guess the only difference between this and the one you posted is the Icon parameter

---

### Post by luvshines on 2013-01-11
Just to add, since respawning nautilus fixes it, for now I have added a nautilus-script which I call(from righ-click on desktop) after login
```
cat .gnome2/nautilus-scripts/quicklist_hack 
#!/bin/bash

# Redirecting my anger to null device
echo "Left with no choice but to deploy dirty hack" > /dev/null

# Kill nautilus
nautilus -q >/dev/null

sleep 2

# Respawn it with a hope that all will be OK
nautilus -n &
jobid=$(jobs -l | awk '{print $2}')

disown $jobid

exit 0
```

But I want to get rid of this

---

### Post by mc4man on 2013-01-11
I seem to remember this coming up once last year, can't find any instances though.

A couple of things to try - 
If you create a new user, login to that user - does this occur?

If you were to add another action(s) to your nautilus-home.desktop, when the default bookmarks disappear does it/they remain.

I'd try 2 new actions, one a dupe of a default like Documents, another any other folder you have.
Ex.
add action names to the Actions= line like
```
Actions=Window;Docu;Share;
```

Then add 2 new actions sections, ex. for ^
```
[Desktop Action Docu]
Name=Documents
Exec=nautilus Documents
TargetEnvironment=Unity

[Desktop Action Share]
Name=Share
Exec=nautilus  /usr/share
TargetEnvironment=Unity
```

Initially 'Documents' should show twice in quicklist, after they disappear does one remain & does Share remain?

---

### Post by luvshines on 2013-01-11
> **mc4man said:**
> Initially 'Documents' should show twice in quicklist, after they disappear does one remain & does Share remain?

Yes, it behaves exactly like that

Attaching screenshot of before/after

---

### Post by mc4man on 2013-01-11
Did you try a new user account?

---

### Post by luvshines on 2013-01-11
> **mc4man said:**
> Did you try a new user account?

Yes !! Just tried that out. It fails for new user too.
I didn't copy nautilus-desktop to the new user's home, so that must be using the system default one

---

### Post by mc4man on 2013-01-11
That's unfortunate - means nothing you've changed local to your user has caused this.

I'm putting up a 12.04 install later for something else, maybe I can see where this could be affected system-wide then.

Did you at any time on this install use a different file-manager than nautilus or different DE like xfce, ect?

---

### Post by luvshines on 2013-01-11
> **mc4man said:**
> Did you at any time on this install use a different file-manager than nautilus or different DE like xfce, ect?

Yes, I have gnome installed too but am not using it. Can purge it if required

I have about 10 more installations of 12.04 with my friends. Have checked it on about 2-3 of them, there it works fine

If there is anything which I can try out on their machines, to repeat success in creating the failure case, do let me know ;)

---

### Post by mc4man on 2013-01-11
Haven't had a chance to install 12.04 yet though may not matter in regards to your issue..

A bit curious about a thing or 2 - 
It appears you lose the 5 built-in bookmarks but not any actions. (so your .desktop is fine
 Do you also lose any added bookmarks?
To see - log in, open nautilus normally to home folder. Navigate to any folder not bookmarked, go ctrl+d. It should be added to nautilus sidebar & immediately show in quicklists. Then see if when the built-in bookmarks go away if the added one stays or also disappears

(- even though it doesn't appear to be a local issue I'd try anyway - 
open home folder & delete or rename to a .bak  - .gtk-bookmarks
Do the same for the  .config/user-dirs.dirs file

Then remove the nautilus launcher/icon from unity launcher & log out/in. Open nautilus with - Alt+F2 > nautilus & pin the icon to unity launcher. Does it behave any better?

---

### Post by luvshines on 2013-01-12
> **mc4man said:**
>  Do you also lose any added bookmarks?
Yes, any added bookmarks are being lost

> open home folder & delete or rename to a .bak  - .gtk-bookmarks
Do the same for the  .config/user-dirs.dirs file
Does it behave any better?

Nope, still the same

---

### Post by mc4man on 2013-01-12
I'll throw in a 12.04 install tommorrow & see if anything pops out.
(just to note - if you were to do a fresh install I'm 99.99% sure this wouldn't be an issue

So to recap for anyone else interested -  correct if wrong

Seems to be a system-wide issue as it affects orig. & any new user
Only affects quicklist items that are nautilus bookmarks, both the 5 built-in & any added
When first logging in all bookmarks in nautilus are properly shown in the quicklists & any would work properly when clicked on.
When clicking on any quicklist entry that corresponds to a nautilus bookmark all quicklist entries for those bookmarks disappear until nautilus is killed & restarted
A manually restarted nautilus then has no quicklist issues with bookmark entries
Clicking on a quicklist entry that corresponds to a 'Desktop action' does not remove the bookmark entries??

(as far as ?? - on a fresh login when all are there,  if you click on an entry from a Desktop action do the bookmarked entries stay? As in any of the 3 shown in 2nd screenshot in previous post.

Edit: if me I'd probably make sure there was an alt. session to log in to, then I'd completely remove 4 unity & 3 nautilus packages & do a restart. After logging in to unity-2d or Classic then re-install the 7 packages - can give a list if desired
At some point though I'd likely just copy out stuff, settings, ect & re-install

Re-edit: - could you try something sorta silly though it did resolve some odd issues in 12.04 dev
Try switching themes & then back. Ex.  - if using Ambiance then switch to Radiance in Appearances, click on Desktop, then switch back to Ambiance

---

### Post by luvshines on 2013-01-12
> **mc4man said:**
> Re-edit: - could you try something sorta silly though it did resolve some odd issues in 12.04 dev
Try switching themes & then back. Ex.  - if using Ambiance then switch to Radiance in Appearances, click on Desktop, then switch back to Ambiance

This didn't help, I tried switching themes using 'myunity'
JFYI, I am using the 'Dark ambiance theme' from this link
[http://solancer.blogspot.in/2012/04/dark-ambiance-theme-for-ubuntu-1204.html](http://solancer.blogspot.in/2012/04/dark-ambiance-theme-for-ubuntu-1204.html)

And added my own tweak(for application logos) explained in this thread
[http://ubuntuforums.org/showthread.php?t=2059642](http://ubuntuforums.org/showthread.php?t=2059642)

---

### Post by luvshines on 2013-01-12
> **mc4man said:**
> if you were to do a fresh install I'm 99.99% sure this wouldn't be an issue
I would want to avoid this for 2 reasons:
a) Using it as dev machine for office chores. Lots of installations
b) I may again end up doing the-something-silly which triggered this, unless I know what was the reason for this one

EDIT: Can I attach some sort of debugger to collect any logs which might help ?

> 
Edit: if me I'd probably make sure there was an alt. session to log in to, then I'd completely remove 4 unity & 3 nautilus packages & do a restart. After logging in to unity-2d or Classic then re-install the 7 packages
Can give this a try once I am on high speed network

---

### Post by mc4man on 2013-01-12
got 12.04 in, haven't noticed anything yet. (other than some initial wierdness with a computer:/// bookmark, not related to your issue

Will do as you've done theme-wise ect. tommorrow as it's late.
As far as any logs, not sure, you could ck. ~/.xsession-errors or dmseg in /var/log

---

### Post by luvshines on 2013-01-12
> **mc4man said:**
> Will do as you've done theme-wise ect. tommorrow as it's late.


It doesn't seem to be the theme stuff doing the mess.
I have installed a 12.04 VM and trying to repeat everything I could recall I did on my base machine
Till now, no success. I have tried:
a) Changing Icon=user-home in nautilus-home.desktop
b) Installed same theme, using myunity
c) Moved windows control to right, using ubuntu-tweak
d) Did the jig I mentioned in my thread, comment#13 [http://ubuntuforums.org/showthread.php?t=2041651&page=2](http://ubuntuforums.org/showthread.php?t=2041651&page=2), to change the login and wallpaper backgrounds separately

---

### Post by luvshines on 2013-01-12
Finally, I have located the source of error \\:D/

Comparing all the packages containing the word 'unity' on my base machine and VM, there was one extra package on the base machine
```
 unity-window-quicklists    1.0-1    quicklists to the unity launcher to allow selecting windows
```

I had installed that following the instructions given on this link
[http://www.webupd8.org/2012/06/unity-window-quicklists-switch-between.html](http://www.webupd8.org/2012/06/unity-window-quicklists-switch-between.html)

I repeated that on my VM. Installed that package and did the 'sed' fix which has been mentioned.
My VM also got screwed :)

So I simply purged the package on the base machine and things are back to normal

Just in case it helps, the file content which it adds is:```

cat /etc/xdg/autostart/unity-window-quicklists.desktop 

[Desktop Entry]
Name=Unity Window Quicklists
Comment=Helps you find windows in the Unity desktop
Exec=/usr/bin/quicklists
Terminal=false
Type=Application
Categories=
OnlyShowIn=Unity;
AutostartCondition=
NoDisplay=true
X-Ubuntu-Gettext-Domain=unity-window-quicklists
Name[en_GB]=unity-window-quicklists

# And some code(python script) as
/usr/bin/quicklists

```

I haven't been able to debug why this code messes up the functionality

**@mc4man**
I really appreciate your help so far. The tests you asked me to perform and narrowing down the scope to nail the error. I had almost given up on this issue, this was my last attempt on the 'bump' :)
*If I am not asking too much, can you confirm this issue by installing that package and see if it breaks for you too*


But the reason I installed this package was that I needed that feature of choosing the open window for the same application.

I hate the animation stuff where the desktop view is zoomed out, all the open windows for same applications are kept side by side and I have to choose based upon the content. It doesn't work well when I have many terminals or chat windows open.

Since I have now purged this package, any workaround to regain that feature ? :-k

---

### Post by mc4man on 2013-01-12
Yep - that package is from a ppa - 
[https://launchpad.net/~alanbell/+archive/unity](https://launchpad.net/~alanbell/+archive/unity)

And now I remember this package - [http://ubuntuforums.org/showthread.php?t=1942673](http://ubuntuforums.org/showthread.php?t=1942673)
(the irony is this did 'come up once last year',  - to me, forgot all about it, such is..
> There is 1 current 'giveback' I see, the nautilus 'bookmarks' quicklist entries will be disabled, except for items that are there from explicit entries in nautilus-home.desktop (default or user added


It's designed to give you active/dynamic quicklists based on open windows of any particular app
So when opening multiple windows of same app the individual window listings will show up in the quicklists.
That's why it gets rid of all the bookmarks (unless they happen to be open.

I knew this sounded familiar - used that package for a short while but stopped using 12.04 fairly soon after release

Edit: I actually found the app useful, what I did to replace the loss of the set bookmarks was to 
"returned the 'Bookmarks' to the panel menu on Desktop focus", ie. rebuild nautilus with a patched source to return that panel menu item

---

### Post by luvshines on 2013-01-13
Ah !! It's a known issue. Had been driving me crazy

> **mc4man said:**
> what I did to replace the loss of the set bookmarks was to "returned the 'Bookmarks' to the panel menu on Desktop focus", ie. rebuild nautilus with a patched source to return that panel menu item

I didn't get this part. #-o
[COLOR="blue"]Can you elaborate a bit, I would like to try it[/COLOR]

Edit: Marking this as SOLVED.

**@mc4man**
Thanks a bunch for your sustained support. I would still be waiting for the answer about the [COLOR="blue"]query above[/COLOR] :)

PS: For now, I have added indicator-places.py from this link [https://github.com/shamil/indicator-places](https://github.com/shamil/indicator-places)

---

