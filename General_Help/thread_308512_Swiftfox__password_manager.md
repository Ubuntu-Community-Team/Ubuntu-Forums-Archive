---
title: "Swiftfox  password manager"
date: 2006-11-28
forum: General Help
---

### Post by DougieFresh4U on 2006-11-28
Good Morning! :)  Password manager in Swiftfox does not seem to remember passwords. Is there a way to fix?

---

### Post by strabes on 2006-11-28
if you have more than 1 username and password combo remembered for a website, you have to type in the username, and then it will fill in the password that corresponds to it. I have run into this problem before and I finally figured out that I had to delete one of the passwords. Let me know if this helps

---

### Post by DougieFresh4U on 2006-11-28
I am the only user of this machine and I use the same p-word for every thing. (I know it's not a good Idea) and this is fresh install yesterday. I had no problem before with it.

---

### Post by scooper on 2006-11-29
You may want to check permissions on the profile directory.  I'm not sure where swiftfox places user configuration, but I think you can run this to get to the profile manager.

```
swiftfox -P
```

You can see what directories are being used for your profile(s) from this dialog.  Then I would check that your user can write to that directory and all the subdirectories, e.g. using "ls -l" from a shell.

Of course there's also the more obvious possibility that the option to save passwords is not checked.  In Windows Firefox 2.0 (where I am now) it's called "Remember passwords for sites" under the Security category in the Preferences dialog.

---

### Post by non-free on 2006-11-30
> **DougieFresh4U said:**
> Good Morning! :)  Password manager in Swiftfox does not seem to remember passwords. Is there a way to fix?

Yes, dont use it. Swiftfox is non-free anyway and takes away a freedom Firefox gives you. The right to redistribute. Thats why its not in the repositories.

---

### Post by freshofftheufo on 2006-12-01
> **non-free said:**
> Yes, dont use it. Swiftfox is non-free anyway and takes away a freedom Firefox gives you. The right to redistribute. Thats why its not in the repositories.

You didn't create that account just to bash Swiftfox did you? You seem to be ignoring everything that is carefully explained on his website.

---

### Post by DougieFresh4U on 2006-12-01
Can any one help with password manager?

---

### Post by scooper on 2006-12-01
> **DougieFresh4U said:**
> Can any one help with password manager?

Did you see my post above?  Did you check the permissions and whether or not the option is enabled?

---

### Post by non-free on 2006-12-01
> **DougieFresh4U said:**
> Can any one help with password manager?

Don't use the non free Swiftfox that takes away freedom to redistribute that Firefox gives you. The [less than one second speed difference]("http://www.apcstart.com/node/3097") isn't worth it.

---

### Post by strabes on 2006-12-01
Did you even check your passwords in the privacy settings? You might have the same password entered twice but one for [http://yoursite.com](http://yoursite.com) and one for [http://www.yoursite.com](http://www.yoursite.com) - that's a problem

---

### Post by DougieFresh4U on 2006-12-01
scooper, output from your post::dougie@DougiesToyBox:~$ swiftfox -P
bash: swiftfox: command not found
dougie@DougiesToyBox:~$ sudo apt-get swiftfox -P
Password:
E: Command line option 'P' [from -P] is not known.
dougie@DougiesToyBox:~$ sudo apt-get swiftfox -p
E: Command line option 'p' [from -p] is not known.
dougie@DougiesToyBox:~$ sudo swiftfox -P
sudo: swiftfox: command not found
dougie@DougiesToyBox:~$ sudo swiftfox -p
sudo: swiftfox: command not found
dougie@DougiesToyBox:~$ 
:::: I should say that it works for some sites but the forum here is not one of them and it worked for forum before I did re-install of Dapper this week.

---

### Post by scooper on 2006-12-02
First I'd just simply check the preference under Edit / Preferences / Security / "Remember passwords for sites".

> **DougieFresh4U said:**
> dougie@DougiesToyBox:~$ swiftfox -P
bash: swiftfox: command not found

The other things you tried with with apt-get don't make sense, you have swiftfox somewhere, and it's just a matter of finding it.  However you run it, through a menu item or panel icon, just check what path it's using to run swiftfox.  It would be in the icon properties or you could look through the menu editor (right-click the start menu to get to the editor).  When you find the path run the full path with the -P option from the command line to bring up the Profile Manager.  From there you'll be able to see where the profile is loading from, and then you can check the permissions.

Good luck.

---

### Post by DougieFresh4U on 2006-12-02
Thanks so much for giving me a lead.Ok, I found it in /opt/swiftfox/swiftfox.What should the permissions be: Read or Read and Write or some thing different

---

### Post by scooper on 2006-12-03
> **DougieFresh4U said:**
> Thanks so much for giving me a lead.Ok, I found it in /opt/swiftfox/swiftfox.What should the permissions be: Read or Read and Write or some thing different

Did you check the option first?  Sorry I wrote it second, but it's the more likely cause.

The permissions on the program and it's directory don't matter so much.  Have you found exactly where the "default" profile lives using the profile manager?  Try "/opt/swiftfox/swiftfox -P" and select "default" profile and look for the location of its directory.  It should live under your home directory.  If you do "ls -l" on the directory the third column should show your name as the owner.  Use the "chown" command to fix it if necessary.  You should have "w" set in the permissions everywhere, e.g. "drwx..." for directories and ".rw...." for files.  But it's more likely to be the wrong owner (probably).

If you don't have important data in the Firefox profile you may want to consider just creating a new one through the Profile Manager.  Assign a directory you definitely own (under your home) and things should start working.  Then you can delete or ignore the old default.

I'll keep checking this thread, but it may take me awhile to answer (as you can probably tell :))

---

### Post by NeoLithium on 2006-12-24
Well, I had the same problem, it was just something that I goofed on the first browser launch; try just doing ls -a in your /home/user director, and removing the .mozilla directory (Keep in mind this will remove your settings, passwords, bookmarks, history, etc for Mozilla browsers); but it will reset as if it was just installed for you to use. 

Solved my password problem instantly.

---

