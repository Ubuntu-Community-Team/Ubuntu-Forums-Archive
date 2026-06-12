---
title: "NUbuntu User...  Applications Menu Items Won't Appear"
date: 2008-06-12
forum: General Help
---

### Post by casparov on 2008-06-12
Hi, Everyone...  

I have a problems w/ the menu items in Ubuntu 8.04.  Upon attempting to run a game (Home World 2 via "Play in Linux"--should NEVER have attempted it besides not having the time) my screen went black, and I had to kill the machine and restart. 

Upon restarting, everything is fine, except I cannot get my applications menu item to reveal its drop-down list.  I have tried restarting, shutting down and restarting, restarting the PC through Ubuntu's fix and repair mode, etc.  I have also done a quick search to see if anyone has an answer, and I didn't see anything quite on point (but my attempt was cursory).  

I would appreciate any insight into this problem.  For me, without that list, I am even more helpless than I normally am.

Regards and thank-you,

Casp

---

### Post by Vadi on 2008-06-12
So when you click on Applications, nothing happens?

Try doing alt+f2 and "killall gnome-panel".

---

### Post by casparov on 2008-06-12
Vadi, Thanks a million...   

Yes, nothing happens, unfortunately.  

I tried your work-around, and, while I am most grateful, it didn't seem to do the trick.

The other menus, btw, work just fine.

Regards,

Casp

---

### Post by Vadi on 2008-06-12
Try right-clicking, and selecting 'edit menus'. Do you see the accessories / games / graphics and whatnot entries in there?

---

### Post by casparov on 2008-06-12
Vadi...

Thanks so much for your following on...

That's the odd thing--the edit menu interface will not launch, either.  

I recently tried, through synaptic, reinstalling the gnome panel (and anything remotely related to it).  At this point, I am a bit lost as to what to do next.  

Is it possible to uninstall anything gnome panel related then reinstall  that.  Virtually everything else works--I just can't launch my applications.

Regards,

Casp

---

### Post by Vadi on 2008-06-13
I think I have a better idea. Right-click on the panel, and select 'Delete this panel'. Then right-click on the panel at the bottom, and select 'New panel. You'll have a blank panel on top, so you'll need to add all applets back in. Add the Menu Bar, Notification Area, Quit..., and the Clock applets.

Does it work after?

---

### Post by casparov on 2008-06-13
Vadi...  

Once again, thanks so much for your help.

I did as you suggested to no avail, unfortunately.

I wonder, should I go the route of uninstalling the gnome panel, then reinstalling?  (I don't know what happens w/o a panel--would I easily be able to reinstall it?)

Gads,

Casp

---

### Post by unutbu on 2008-06-13
casparov, it might be the case that some configuration file in ~/.gnome2 or ~/.gconf is messed up. I might be wrong about the directory. GNOME is pretty mysterious about where it keeps certain settings.

To test if one of your local config files is damaged, perhaps create a new user and see if the new user has the same problem or not.

If the new user has the same problem, then at least we'll know the problem is system-wide, and you'll probably need to remove and re-install certain packages to get it right.

If the new user has no problem, then you have two options: you can try to move ~/.gconf and/or ~/.gnome2 to directories with different names, and see if GNOME will automatically create new default ~/.gconf and ~/.gnome2 for you. Maybe that will solve the problem. 

Or, you could take a more aggressive approach which (if the new user has no problem) is guaranteed to solve your problem: just move your data over to the new user and then delete your current account. (Become the new user). If you are attached to your current user name, you could then recreate your old user name account, and move your data back there again. If you want details of how to move your stuff in a somewhat convenient manner, post.

---

### Post by casparov on 2008-06-13
Unutbu... 

Well, that was truly inspired.  

Yes, creating a new user gets rid of the problem and, no, I am not attached to the user name (though its my initials).

Now about your further instruction:  

If the new user has no problem, then you have two options: you can try to move ~/.gconf and/or ~/.gnome2 to directories with different names, and see if GNOME will automatically create new default ~/.gconf and ~/.gnome2 for you. Maybe that will solve the problem.

Or, you could take a more aggressive approach which (if the new user has no problem) is guaranteed to solve your problem: just move your data over to the new user and then delete your current account. (Become the new user). If you are attached to your current user name, you could then recreate your old user name account, and move your data back there again. If you want details of how to move your stuff in a somewhat convenient manner...


I would LOVE the details about how to become the new user.  

Thanks so much for the insightful and liberating reply.


Casp

---

### Post by unutbu on 2008-06-13
Do you have space to make a complete duplicate of your home directory? If unsure run

```
du -sh ~
```
to see how large your home directory is, and run 
```
df -h
```
to see how much space you have available on your '/' partition (or whatever partition contains your /home).

---

### Post by unutbu on 2008-06-13
Assuming you have room to make a complete duplicate of your current account, here are instructions on 'how to become the new user':

Log in to your old user account. Click System>Administration>Users and Groups. Click on the new user. Click on the Properties button, and then the 'User Privileges' tab. Enable all privileges for the new user, especially "Administer the system". That will allow the newuser to use sudo.

Open a terminal (still as the old user) and type 
```
export newuser=rfw1
export olduser=rfw
```
changing 'rfw1' and 'rfw' to whatever your new and current usernames are.
Now you can cut and paste the rest of these instructions. 

Next type
```
for group in `groups`; do echo $group; sudo gpasswd -a $newuser $group; done
```
This loops through all the groups that $olduser is a member of and makes $newuser a member of that group.

```

sudo groupadd $newuser                  # This creates the $newuser group if it does not exist already.
sudo usermod -g $newuser $newuser       # This makes sure $newuser's default group is $newuser.

```

Now we copy everything but the "dot" config files from your old user account to your new user account:
```

cd /home/$olduser
find . -print0 | grep -zZv "^\./\." | sudo cpio --null --sparse -pvd /home/$newuser

```

Change the ownership of all files in /home/$newuser to $newuser:
```

sudo chown -R $newuser:$newuser /home/$newuser      

```

That's it. Your $newuser account should work and have all the data from your old account.

I recommend that you do not erase /home/$olduser for a while (perhaps a month or two? you decide). That will give you time to make sure everything has been copied properly. This method will make you lose any GNOME configurations (custom Launchers, menu items, keyboard layouts, wall paper, font rendering options, etc.) you have made in your $olduser account; you'll have to redo those by hand.

When you are ready to remove $olduser, Click System>Administration>Users and Groups and delete $olduser. If /home/$olduser is not deleted (I'm just not sure), then run
```

sudo rm -rf /home/$olduser
```

---

### Post by casparov on 2008-06-14
Unutbu...

I can't believe you spent the time that you did in helping me out here--you are a true Linux Lion. 

Anyway, I changed to a new user and tried your instructions.  However, though I followed your directions to enable the new user w/ all privileges, it informed me at a certain step that permission was denied.

No matter, I probably did something wrong and will try again.  Unfortunately, I will defer this until tomorrow (it is 4:30 a.m.).  I was fine until it was obvious that I can't do this as quickly as you can--I have to crawl at the objective a bit. 

But I do have a quick question...  Regarding your first instruction after logging in as the new user (old user=rfw; new user=rfw1) do I hit enter after I type that instruction in terminal, or do your instructions require that they all be entered before hitting enter?  (If that makes sense)

I will be at it later today,

Casp

---

### Post by unutbu on 2008-06-14
> **casparov said:**
> 
I followed your directions to enable the new user w/ all privileges, it informed me at a certain step that permission was denied.

Hm. If it happens again, please describe at which step it happens.

> 
I was fine until it was obvious that I can't do this as quickly as you can--I have to crawl at the objective a bit. 

It's good to go slow. Understand each command before you type it (fire away with the questions and I'll try my best to answer.) Since we are copying and not erasing, this procedure should be safe. Nevertheless, it would be good to open a text editing window (e.g. gedit) and copy/paste everything you see in the terminal (your commands and the output) into the text file so you have a record of the commands you used. It could help us if something goes wrong.

> 
But I do have a quick question...  Regarding your first instruction after logging in as the new user (old user=rfw; new user=rfw1) do I hit enter after I type that instruction in terminal...

Yes. Each line ends with an implicit Enter.
For example,
```
export newuser=rfw1 [Enter]
```
 
I just created a new user on my machine to see if I could reproduce your permission problem... I couldn't. However, I did notice that your rfw1 groups may be a little different than your rfw groups. I'll edit my instructions to include how to fix that.

---

### Post by casparov on 2008-06-16
Unutbu...

Were in not for your ministrations I would be most unhappy about all this, indeed.  (You may know the feeling--there is something completely reassuring about a system that works.  Just about everything is running south for me at the moment, but if my PC works I feel like I can make everything else work, also.  Unfortunately, for me, that means that I need the help of others.  Just wish I could send it your way.) 

Anyway, this new user idea has been a savior--EVERYTHING works better within Linux w/ it.  Given this, should I successfully migrate all the previous user settings to the new user, will I wind up handicapping the new profile?  

I thought that I had better ask you this before proceeding w/ your last remarks.  (Also, I am sorry for not being here the last day--ran into a difficult weekend.)

All Regards,

Casp

---

### Post by johnc3 on 2008-06-16
it seems that if you copy the .gconf or/and .gnome2 directoies the problem isn't solved. in my case the missing application menu appeared when i was tweaking witch AWN, i still have the problem. the new user worked but i don't know witch files/directories are corrupt in the old user.

after 2 hours i found it.
EVRIKA!!!
:guitar:
the problem was that i noticed an error in ~/.xsession-errors > ** (gnome-panel:6237): WARNING **: Error loading menu layout from "/home/user/.config/menus/applications.menu": Error on line 1 char 1: Document was empty or contained only whitespace


looking at the new user created i noticed that the directory ~/.config/menus was missing but the menu was working so i deleted my "~/.config/menu" directory and voila, the menu apperead instantly.
i hope this helps, it worked for me

---

### Post by unutbu on 2008-06-16
johnc3, thanks for the information!

casparov, I would try johnc3's advice first because it is simpler and less prone to complications (like the group permissions problem).

In a terminal, try typing:
```
grep Error ~/.xsession-errors
```

If you see an error like 

> ** (gnome-panel:6237): WARNING **: Error loading menu layout from "/home/user/.config/menus/applications.menu": Error on line 1 char 1: Document was empty or contained only whitespace

then I would try johnc's advice this way:
```

cd ~/.config               # change directory
tar cf menus.tar menus     # make a tar archive of menus
rm -rf menus               # remove the menus directory

```
If you see a different error, post it.

On the other hand, you mentioned that 
"EVERYTHING works better within Linux w/ it". That's wonderful. If you still feel that way, then you could still try migrating your data as I described.

Regarding this question:
> should I successfully migrate all the previous user settings to the new user, will I wind up handicapping the new profile? 
Initially, after completing the migration procedure in my previous post, the new user should have none of the previous user's GNOME settings. As you add back the previous settings by hand, you may find that something you add may affect your machine's performance. Compiz causes some users difficulty for example. 

If you want to be cautious and methodical, take notes on every setting change you make (sort of a computer diary). Then if you later notice slow performance or something, then you can use the diary to back out of recent changes.

Also, after doing the migration to the new user (if you choose to do so), you should try to give your account a bit of a workout to make sure you are not missing any functionality you used to have. For example:

1) Play a music CD, play a DVD (if applicable)
2) Read a data CD or DVD
3) Use the sudo command
4) Install a package
5) Uninstall a package
6) Print to a printer

---

### Post by casparov on 2008-06-17
Unutbu and JohnC3...

Your know-how amazes me.

Today (Tues.) I will have some time to spend looking at your latest fix.  I don't know how in the world you guys can troubleshoot the way that you do.  I am most appreciative and thankful for your help.

(Btw--Batrista--I looked it up, JC3...  Watch out, Unutbu... Our interloping friend my be a vampire!!!!!!!!!!!!!!!!!!!!!!)  

All Regards,

Casp

---

### Post by casparov on 2008-06-17
Sorry, JC3...

I should have said Bistrita...  

I'll be back (for sure), 

Casp

---

### Post by unutbu on 2008-06-17
Casp, just in case you've copied/printed my instructions in [post #11]("http://ubuntuforums.org/showpost.php?p=5182289&postcount=11"), please note I've made some changes. Hopefully now they are a bit simpler, a bit better.

---

### Post by casparov on 2008-06-18
Unutbu...

I have reviewed your prior post #11 and have tried (first) attempting the instructions in your most recent post (following JohnC3's idea).  

[Off point: JC3 lives (by profile) in, or near, Transylvania, Romania.  I have the garlic around my neck...)

I should say, straight off, that the old user profile cannot access terminal except via alt-F2, which really doesn't allow one to see much of what is going on.  Therefore, everything I have tried under the old user is via terminal launched in this way.

Your most recent post didn't change things but didn't generate errors, either.  When I repaired to your #11 post and entered the first command indentifying the hew user I got this error: 

[HTML]Could not open location 'file:///home/rfw/export%20newuser=rfw1'[/HTML]

I consider this error important because I've got to teach myself to follow your instructions.  But I also am aware that I am not completely comprehending instructions that would be second nature to an experienced user.  But I am not giving up.

If you can hang in there a bit more I am going to try your instructions again and see if I can make more progress.  I know that I could just redo everything under the new user (the creation of which saved my Linux experience), but I really should follow through and fix things the way that you suggest.

I'll be at it again and thanks ever so much (again),

Casp

---

### Post by casparov on 2008-06-18
Unutbu...  

I should add that my old user configuration must be very lame--I cannot switch users within an existing session but must shut down to do so.  This is the case in both directions.

Regards,

Casp

---

### Post by johnc3 on 2008-06-18
yes, i am fron transylvania, no worries i won't bite. anyway deleting the ~/.config/ directory worked for me . the only thing diferent is that i lost my custom gnome menu but that cand be done in less than 1 minute. i beleve that tweaking with the menu and/or AWN and the fact that the error occuoured when  was low on hdd space (the file coudn't be written) was the problem. i strongly suggest to delete the ~/.config dir and the problem is resolved

---

### Post by unutbu on 2008-06-18
Casp,

(1) I agree with johnc3 -- try his solution before you try mine. The only thing I would do a little different is I would move the ~/.config/menu directory instead of deleting it.

(2) The error you are getting is due to Alt-F2 not being the same as a terminal. As rfw (olduser) press Alt-F2. Type ```
gnome-terminal
```. This should open up a true terminal window for you.

---

### Post by casparov on 2008-06-19
JohnC3...  Thanks for the additional information (and I hope that you didn't take offense to my vampire remarks--I find your place of origin very interesting).

Unutbu and JC3...  I am embarrassed to say that I don't know where the directory is.  Can you give me a head start from, say, the home folder, or something like that.  (I.e., I don't understand where the tilde begins: ~/.config/menu)

I know that sounds absurd, but the detail you have presented here may well help quite a few others, who, like me, took the Ubuntu bait pretty much blind. 

Unutbu...  thanks, also, for the heads up about the proper terminal shortcut.

I am going to retry things and will reply tomorrow.

I appreciate the time you both have devoted to this,

Casp

---

### Post by unutbu on 2008-06-19
No worries, Casparov. Keep asking questions in the forum and pretty soon you'll know a heck of a lot.

The tilde ~ at the beginning of a path means "starting at my home directory". So if you log in as olduser rfw, ~/.config/menu means the same thing as /home/**rfw**/.config/menu. But if you log in as newuser rfw1, the ~/.config/menu means /home/**rfw1**/.config/menu.

To try johnc3's solution, log in as rfw, open a terminal by pressing Alt-F2 and running the command gnome-terminal. Then in the terminal window type

```
cd ~/.config          
mv menus menus-old
```
This is a little different than what I suggested last time, and perhaps it is a bit easier too (one less command). This simply renames the ~/.config/menus directory as ~/.config/menus-old.

You might have to log out and log back in to see if your Applications menu works again... I don't know for sure.

If it works for a week, then you can erase ~/.config/menus-old using nautilus or by typing

```
rm -rf ~/.config/menus-old
```

---

### Post by casparov on 2008-06-20
YOU DID IT!!!!  IT WORKED!!!!!!!!   

Unutbu and JC3... 

Wow, thanks alot.  The last post from Unut did the trick and, once I logged out and in, the applications menu is back in full force.

I can't thank both of you enough, and it bugs me to death that I can't repay you.  This entire thread should be sticky somewhere--you really hounded this problem, and your troubleshooting was superb.

It is bittersweet--I wish that I could stay in touch, but you are, no doubt, breathing a sigh of relief that this one is done.  

There is abs. no way that I could have solved this, and it stood a chance of either souring me on Linux (for a while, anyway) or (worse) leading me to reinstall, something I wasn't relishing, at all.  

Damn it, you guys are great. 

All Regards,

Whit (W.)

---

### Post by casparov on 2008-06-20
Btw, "Casparov" derived from my taking up chess for a bit then discovering it took too much time.  

Beyond that, there was a sixties cartoon (I think--could have been earlier but I don't know) called "Casper, the Friendly Ghost"  Someone mentioned that I wasn't playing anymore--that I just vanished.  I replied that I had become Casparov, the Chess Ghost. 

W.  

[http://en.wikipedia.org/wiki/Casper_the_Friendly_Ghost](http://en.wikipedia.org/wiki/Casper_the_Friendly_Ghost)

---

### Post by unutbu on 2008-06-20
Casparov, I'm so glad I could help. 
If you really want to thank me, [pay it forward]("http://en.wikipedia.org/wiki/Pay_it_forward")... spread the [Ubuntu spirit]("http://en.wikipedia.org/wiki/Ubuntu_%28philosophy%29") by helping a stranger!

---

### Post by mc4man on 2008-06-20
Just to add a little info. The real culprit in most cases is the file in .config/menus - applications.menu. This file is created when you edit the application menu (actually just the act of choosing to edit menus creates it). If you try to edit the file directly or it becomes corrupted then you lose your applications drop down. It's not a necessary file for the menu to work , simply deleting it will restore access. It's recreated the next time you edit the menu.
I believe the actual menu info (as far as what's been included and or excluded) is stored somewhere else for the purpose of reverting (undo).
It all relates somehow to the inability in some cases to restore deleted menu items using revert.

---

### Post by casparov on 2008-06-21
mc4man...  

Thank-you for the added insight.  

I am going to summarize the information I received in my Google Docs Linux file, which will include your observation. 

All Regards, 

Casp

---

