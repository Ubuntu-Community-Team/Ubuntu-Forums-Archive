---
title: "Software Center not loading software"
date: 2021-01-25
forum: General Help
---

### Post by joelomar on 2021-01-25
Hello - I recently formatted my computer and this is a fresh, brand new install of 20.04. When I load Software Center to search for software it just stalls and takes forever. If I go to the different categories, nothing is displayed. Happens on all of the accounts in this system. If I download a .deb, it installs OK via the CLI.

What can I do to restore this functionality?

---

### Post by CelticWarrior on 2021-01-25
Make sure your system is fully updated: ```
sudo apt update && sudo apt full-upgrade
```

Then, in the Software Center, open a category and click the big button with the 3 dots. Wait some seconds (10 or more).

---

### Post by joelomar on 2021-01-25
Well, that appears to work. I just need to go through each category and refresh. 

Any idea what happened here? Operator error? Bug? Feature?

---

### Post by Dennis N on 2021-01-25
>  If I download a .deb, it installs OK via the CLI.
What .deb did you download and install here? In Ubuntu 20.04, "Ubuntu Software" (installed as a default application) comes as a snap package only. "Software Center" could refer to a couple of applications, but no application actually has that name.

If you problem is with Ubuntu Software, you might try the suggestion here:
[Problems with Ubuntu Software]("https://ubuntuforums.org/showthread.php?t=2456992&p=14016327#post14016327")

---

### Post by joelomar on 2021-01-27
OK. Now it works, but when I try to install any software from the store I get an error message that is not that descriptive. The user is an admin.[ATTACH=CONFIG]287831[/ATTACH]

---

### Post by Dennis N on 2021-01-27
> I get an error message that is not that descriptive. The user is an admin...
I seems to be saying you are running it with administrative privileges? That can come from using sudo when starting the program in a terminal. If you did that, you shouldn't. Find the program icon with the "Show Applications" button, and start it by clicking on that. You can also search for it in the activities overview search (see screen shot), or find it in an applications menu if you have one installed.

If that's not the case, then I'm not sure of the cause.

---

### Post by joelomar on 2021-01-27
Well, I created a user that is the admin and two users that are not admins. If I'm using the non-admin users, the system is supposed (I think) to prompt for the correct admin credentials. I noticed that it doesn't happen. It just tries and it fails. If I do drop to a terminal and su to that admin user and run the install line with those credentials, it runs OK. 

I went over to the admin user profile and made one of the other users have admin rights, but it doesn't work either. When I reformatted this computer I wanted one admin account and the other two not to be as 'powerful' for security reasons. Guess it doesn't work that way.

---

