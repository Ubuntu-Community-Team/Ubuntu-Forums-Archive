---
title: "Clock: &quot;Adjust Date and Time&quot; causes Bug Buddy to appear."
date: 2006-11-06
forum: General Help
---

### Post by fuzzy_umbra on 2006-11-06
Hello,
When I am logged in as the non-root user I used to install Ubuntu, and I right click on the clock in the Panel and select "Adjust Date and Time", the bug buddy appears.
I filled in my email address and allowed it to send, and it showed me a link to a bug, number 351603, filed in August.
When I am logged in as root, it works fine.
Any ideas about how I can remedy this?  Is there something more sinister going on, or is it just a bug in the clock app.?
I just installed Ubuntu today, so if people advise to reinstall, no problem.
Thanks,
- Rob

P.S. I am using the Edgy Ubuntu.

---

### Post by hikaricore on 2006-11-06
You may want to try logging in a different user and see if this affects that user as well.  Open a terminal and type:

```
sudo adduser someotherusername
```
^Where someotherusername is whatever you want this user to be called.

Then go through the process of setting a password and such, after a few steps there will be a new user created.

Once this is complete log out from the system menu and login as your newly created user.  If this issue happens to that user as well, you may want to reinstall if you can't find any other solution.  But if that user has no trouble, it could very easily be something that isn't quite right with your main user's Gnome configuration.  You may want to look around for a way of *resetting* or removing the config files for your main user's Gnome.  :)

Hope this helps, just offering some ideas.

*I once had a gnome config problem that caused my Xserver to reboot my system everytime I logged in to my main account, after removing the config files which basicly reset it, the problem was gone.  I never could figure out what was causing it*

---

### Post by fuzzy_umbra on 2006-11-06
Hello,
Well, some interesting things happened.  I added the user and checked all of the checkboxes on the permissions tab, including 'Administer the System'.  I logged in as the new user, and was denied permission to change the clock, edit any settings, etc...  (I double, triple checked, that all of the checkboxes were selected.)  So I logged out, logged in as root, and deleted the original user.  I tinkered with the permissions of the new user some more, to no avail.  I logged in as root again, tried to adjust the clock, and then the crash occurred!  This is odd, since the crash was not occurring previously as root.
So I reinstalled Ubuntu.  I added a new user, with all permission checkboxes selected, and was able to adjust system settings as that new user, unlike before. The clock does not crash as any user.  So it looks like something got into A Very Bad State.  I had installed a lot of the software in Applications > Add/Remove.  Maybe something went wrong with one of them?  I am going to install them one at a time and keep checking the clock.  I'll post again if I am able to repro. the issue.
Thanks,
- Rob

---

### Post by hikaricore on 2006-11-06
Good to hear you got it working.  Sorry you had to go through and reinstall to solve it tho.

Installing new applications can sometimes be the root of the problem, if such and such and app decides that your version of such and such a library is out of date and needs to update it without you knowing it did so, suddenly main system components that worked flawlessly before are now trying to use a library they weren't inteneded for (a good example is libc6, unless there is a specific ubuntu update released for libc6 never replace it hehe).  :)  Now normally this isn't the case but it has happened to me before.  Just be sure to watch what you install and if you track it down to a specific app be sure to contact the authors and let them know their libraries could be causing issues with certain distributions as maybe they overlooked it and release something with an older version.

Good luck.

--Aaron

---

### Post by Hamal on 2006-11-08
I can confirm this problem and have a possible solution, although my situation could be unique.

Basically I went to System -> Administration -> Language Support and changed my language to English/Australian (yes, I live in Australia - yes, the Ubuntu install defaulted to English/US).

This resolved the issue for me, although as I said my problem may have been unique. Basically, I did a clean install of Ubuntu 6.10 while still keeping my home partition from Dapper. I assume this created a conflict in the configuration files somewhere.

I'm happy now though. My date/time format is set correctly (dd/mm/yyyy - crazy Americans) and I can access my time and date settings. Gnucash now also defaults to the AUD currency and Australian date format.

---

### Post by bollix47 on 2006-11-08
I too had this problem and after following the steps that Hamal suggested the problem was resolved.

Thanks.

---

### Post by the.phantom on 2006-11-08
i am a newbie and had the same trouble 

but found i could go to 
system/admin/time and date and set it correctly
without a but report request
hope this might help a bit?

fresh install of 6.10

---

### Post by ~LoKe on 2006-11-08
I've been getting a lot of Bug Buddy's lately.  Usually closing a window while doing something else causes it.

---

### Post by Mykewl on 2006-11-26
I had the same problem. in my case
system/admin/time and date worked.

---

### Post by Mykewl on 2006-11-26
I tried right clicking the clock again.
This time it worked :D

---

### Post by pagaboy on 2006-11-29
I've got this problem as well.  I suspect one thing though - have we all been using Gnucash?

---

