---
title: "Thunderbird settings lost"
date: 2007-02-18
forum: General Help
---

### Post by mediax on 2007-02-18
I've been using Edgy happily for a few months (dual booting with Windows XP pro) with no serious problems.  However, today I booted into Ubuntu and found that Thunderbird prompted me with the New Account setup wizard.

It appears that Thunderbird has not only forgotten the details of my connection, but also the location of downloaded mail, folders etc - although the contents of my address book seem to be intact.

I've tried rebooting and shutting down my system to no avail. I'd appreciate any suggestions.

---

### Post by mogliii on 2007-02-18
Can you give more details?

Have you been using your email folder from both systems? So was/is the Thunderbird settings folder on a extra partition that could/can be accessed from Windows and Linux?

---

### Post by mediax on 2007-02-18
No - I've only been using e-mail in Linux, so it shouldn't be a Windows corruption issue.

---

### Post by mogliii on 2007-02-18
please check in your home directory for a .thunderbird folder

So should look like this: /home/yourname/.thunderbird/Profiles/

You might have to enable hidden folders in your file manager. In that folder should be another folder with a random name. Please check the size and content, if there are big files that might contain your emails. If this still exists, I first of all recommend you make a backup of the profile folder! 

After that you might have the following option: 
In Thunderbird you can set the locale folder for every mail account. So you could go there and check if the link is set right.

If nothing exists anymore, just create a new profile. That will be called, lets say "3kdi5s.defualt". After you finished to make the new account, quit thunderbird.
Now delete every file in the newly created folder (that is 3kdi5s.defualt) and copy the content of the backed up folder there. After you restart Thunderbird everything should be as usual.

Good luck, and don't forget to backup!

---

### Post by mediax on 2007-02-18
OK - I think I've got it half right!

I found the existing folder where you said (except that the thunderbird folder was called .mozilla-thunderbird, rather than just .thunderbird).

Having backed it up, I set up a new account in Thunderbird (which works fine) - but I can't find the folder for the new account!

---

### Post by mediax on 2007-02-18
Sorted it!  The problem was that Thunderbird had used the same folder and Mail folder, but created a new copy of the Local folders, etc in the Mail folder.  I redirected this to the existing data and hey presto - problem solved.

Thanks very much Mogliii - couldn't have done it without you!

---

