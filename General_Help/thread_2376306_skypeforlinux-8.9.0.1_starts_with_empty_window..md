---
title: "skypeforlinux-8.9.0.1 starts with empty window."
date: 2017-11-01
forum: General Help
---

### Post by ajgreeny on 2017-11-01
I yesterday updated my skypeforlinux from the 5.5.0.1 to the new 8.9.0.1 version on my Xubuntu 16.04 64bit system.

Whilst it seems to work fine as far as I can tell making calls (only tried the Test Call so far) it opens to an empty and inactive window when I have the "start minimised" set in the preferences, ie just the window decoration, and otherwise empty with the desktop showing through.  The window buttons (close, minimise, maximise) are inactive at that stage; the only way to get rid of that is a right click on the panel icon and chose "Open Skype", and the window then appears properly and can be closed back to the panel icon as normal, and if I disable the "Start minimised" option the window opens properly and just has to be minimised manually.

Has anyone else seen this and managed to figure out a way to overcome it? It's very annoying but not a total show-stopper for me.

I have searched the skype user forum but there is no solution shown there, though one or two other users have seen the problem in Mint and it was suggested that they purge the application and reinstall.  I tried that even renaming the skype config in my home before reinstalling but it made no difference.

I would prefer not to need skype but too many of my family abroad are confirmed skype users and to try to get them to use alternatives is just too much palaver to be bothered with so skype it has to be, for now at least.

---

### Post by monkeybrain20122 on 2017-11-01
> **ajgreeny said:**
> I 

Has anyone else seen this and managed to figure out a way to overcome it? It's very annoying but not a total show-stopper for me.


I don't have a "start minimized" option in Application Preferences. Since I disable autostart, when I start it it opens up normally, and then I click close it stay on the top panel as expected (Ubuntu 16.04 with unity)

I use Skype only for my parents, for work people are happy to us google and I have persuaded someone to try out wire lately, but haven't had a chance to use it yet. But it seems that the new version of Skype has many new features (like group video calls) which were not available on Linux before, so that is interesting, would like to have a chance to test them out, I actually like it better than the Windows version (without the ads)

---

### Post by ajgreeny on 2017-11-01
Thanks for the reply monkeybrain20122

As I said above,  "if I disable the "Start minimised" option the window opens properly and just has to be minimised manually." so that appears to be exactly the same as your situation and leads me to believe that it's the Start Minimised option that causes the problem.

Hey-ho. At least we now have a skype app that seems to be just about the equivalent of the Windows version for the first time ever; only time will tell if it gets to work properly as I would prefer with the Start Minimised enabled, but I live in hope.

---

### Post by monkeybrain20122 on 2017-11-01
> **ajgreeny said:**
> Thanks for the reply monkeybrain20122

As I said above,  "if I disable the "Start minimised" option the window opens properly and just has to be minimised manually." 

But I don't have a "start minimized" option to disable or enable. Where is yours?

---

### Post by ajgreeny on 2017-11-02
It is in the Tools menu, I think, not in the application settings at all. Top item in that menu IIRC.

---

### Post by Chanath on 2017-11-02
Start minimized starts Skype and move it to the system tray and await your action, that is, if you have it in autostart.

---

### Post by ajgreeny on 2017-11-02
> **Chanath said:**
> Start minimized starts Skype and move it to the system tray and await your action, that is, if you have it in autostart.
That's what it should do and it worked fine in skype 5.5.0.1 but has not done so in 8.9.0.1 when this is what happens.  See screenshot, as I described in the first post.

Only by using the skype panel icon to "Open Skype" can I interact with the empty skype window as that frame is totally inactive.
It appears that the "Start minimised" also makes the application fail to start properly and completely.

I have used the "Report a problem" item in the help menu so we'll see if anything comes of that; I'm not holding my breath!

---

### Post by monkeybrain20122 on 2017-11-02
> **ajgreeny said:**
> It is in the Tools menu, I think, not in the application settings at all. Top item in that menu IIRC.
Yeah it is on the tool menu, I can confirm that it opens in a transparent window if start minimized is checked.  But then since I never even realised that the option exists it is not a big issue for me. Tested with skypeforlinux 8.10 preview too and it is not fixed.

---

### Post by ajgreeny on 2017-11-02
I see someone has already told the forum for skypeforlinux that this is happening in Mint 18.2, so we are not alone.  The only suggestion was to remove skype, reboot the OS and reinstall skype, (typical Windows solution to problems I seem to remember, :lol:), so I did that but it made no difference.

As I said, it seems to work fine if not started minimised and I can then just close the active window back to the panel icon, as is supposed to happen automatically when started minimised.

---

### Post by strixtux on 2017-11-10
I replaced the latest Skype by 5.5 beta which worked fine until I rebooted. 

Then I saw what old Atarians call a curtain crash.

I am reinstalling from scratch right now.

ILOVECOMPUTERSILOVECOMPUTERSILOVECOMPUTERS....

---

### Post by monkeybrain20122 on 2017-11-10
> **strixtux said:**
> I replaced the latest Skype by 5.5 beta which worked fine until I rebooted. 

Then I saw what old Atarians call a curtain crash.

I am reinstalling from scratch right now.

ILOVECOMPUTERSILOVECOMPUTERSILOVECOMPUTERS....

Actually everything in latest skype works here in 16.04 and 17.10 except start minimized which at least for me is hardly a show stopper.  Even  messaging and sharing screen work without glitches (some people are complaining about these on Skype's forum) I don't know how you can install skype beta as there is a huge warning that the version is no longer supported at start up if you install it now.

Anyway I am switching more people to wire.

---

