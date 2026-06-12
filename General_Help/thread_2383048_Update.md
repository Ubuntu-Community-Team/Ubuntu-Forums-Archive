---
title: "Update"
date: 2018-01-20
forum: General Help
---

### Post by Jack_Shankle on 2018-01-20
I am sending this from a windows computer because I can't get my wife's
Ubuntu computer to update. It gives this message: "Failed to download repository
information".
I know just enough about Linuz to get me in serious trouble.
So please keep it simple with a lot of detail.
Not sure if I have this in the right place. If you move it I will not
be able to find it.
Thanks for your help.

---

### Post by yancek on 2018-01-20
Which version of Ubuntu are you using.  You might try the suggestions at the links below for some info on how to resolve the problem.

[https://ubuntuforums.org/showthread.php?t=2325039](https://ubuntuforums.org/showthread.php?t=2325039)

[https://askubuntu.com/questions/141512/how-to-resolve-failed-to-download-repository-information](https://askubuntu.com/questions/141512/how-to-resolve-failed-to-download-repository-information)

---

### Post by Impavidus on 2018-01-20
Which version? If it's 17.04, that just reached end of life. See [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by Jack_Shankle on 2018-01-20
Thank you for responding.
Yes she is using Ubuntu-mate 17.04
Now what do I do? Is there another version I can use that is a good as Ubuntu-Mate was?

I looked at the suggestions to read and they are way over my head. Have no idea how to proceed.
Since all she does is email and go on the internet once in a while, should I update or install 
from sctarch?

---

### Post by deadflowr on 2018-01-20
> Now what do I do? Is there another version I can use that is a good as Ubuntu-Mate was?
[Ubuntu-Mate 17.10]("https://ubuntu-mate.org/blog/ubuntu-mate-artful-final-release/")

---

### Post by coffeecat on 2018-01-20
> **Jack_Shankle said:**
> Is there another version I can use that is a good as Ubuntu-Mate was?

Yes, Ubuntu Mate. What the other posters were telling you was that the 17.04 release has now reached end of life. 17.10 is currently supported and you should be able to upgrade to that using the link in Impavidus's post. If you need help with that, post back and I'm sure people here will help you.

---

### Post by deadflowr on 2018-01-20
> I looked at the suggestions to read and they are way over my head. Have no idea how to proceed.
Since all she does is email and go on the internet once in a while, should I update or install 
from sctarch?

While I'm normally an advocate for doing in-place upgrades.
With EOL releases, I say go with a fresh clean install.

Remember to save a backup first. As always.
[https://help.ubuntu.com/community/BackupYourSystem]("https://help.ubuntu.com/community/BackupYourSystem")

---

### Post by grahammechanical on 2018-01-20
> "Failed to download repository information".

I am surprised nobody has explained clearly the reason for that message. Ubuntu Mate 17.04, like Ubuntu itself and other Ubuntu flavors, only had 9 months support. That support ended 13 January 2018. It is possible that the repositories from Ubuntu 17.04 and its flavors are updated from are now closed. They may even have been moved to an archive.

When Ubuntu Mate 17.10 was released (October 2017) the system should have prompted your wife to upgrade from 17.04 to 17.10. If this prompting is ignored the system will stop nagging. But all is not lost. There should be a utility that controls updates and upgrades. I do not know what it is called in Ubuntu Mate as I do not use it. I can only describe what I see with Ubuntu. 

You should find this utility in System Settings. It may be called Software & Updates. It should have a tab called Updates. Open that tab and there should be a panel labeled "Notify me of a new Ubuntu version." That should have a drop down menu. Choose the setting "For any new version."

If the utility is already set to notify for any new version, then you may have to run some commands in the terminal. This link explains it.

[https://ubuntu-mate.community/t/how-to-upgrade-ubuntu-mate-via-the-terminal/885](https://ubuntu-mate.community/t/how-to-upgrade-ubuntu-mate-via-the-terminal/885)

When we enter a command with the "sudo" prefix we will be prompted for a password. You will need your wife's user password that she uses to log in to Ubuntu Mate. So, now would be a good time for the actual user to take care of updating & upgrading for herself.

Keep in mind that towards the end of April this year Ubuntu Mate 18.04 will be released. When the system nags the user to upgrade it is best to do so before the same problem happens again.

By the way, because the next release (17.10) is still supported you do not need to do an End Of Life Upgrade. Follow the instructions in that Ubuntu Mate link. I am sure that Ubuntu Mate also has a Help document on that system.

[https://itsfoss.com/ubuntu-mate-customization/](https://itsfoss.com/ubuntu-mate-customization/)

Regards

---

### Post by Jack_Shankle on 2018-01-21
OK - I have downloaded the ISO Ubuntu 17.10.1 to the Ubuntu 17.04 and it is in the downloads
of Ubuntu. Now what do I do? I think I have to move it to a dvd but how? Remember I am a 
windows guy trying to help my wife with her Ubuntu 64-bit computer. I have no idea how to do
 the install other than wiping her computer and starting from scratch. I'm wondering what she
 will lose if I do that? She does mostly email and accesses various URLs. She has a ton of folders
and email contacts.  I assume the gmail program will be retained intact in the new install.

The only way I know how to do this is to download Ubuntu 17.10.1 in windows and move it to a dvd 
with a iso program that I have in windows.
Please help me.
Thank you

---

### Post by ian-weisser on 2018-01-21
Backup data: Backup the entire contents of her home directory, including hidden files: /home/<her_username>.
This will preserve her email and contacts and the rest, which are stored in some of those hidden files.

Set your calendar: Ubuntu releases every 6 months in April/October. Each release is supported for only 9 months.
That's a three-month window to do the release-upgrade. The 17.04-to-17.10 window ended a week ago.
Ubuntu, by default, is set to remind her to do the release-upgrade once every day during that three-month window.
A release-upgrade typically takes about 45 minutes, and can be done quietly in the background. Really.

Remember that Ubuntu is not selling anything. There are fewer system pop-ups than in Windows...but those few alerts are actually important. Get out of the habit of clicking past them.

You CAN [release-upgrade Ubuntu without reinstalling]("https://help.ubuntu.com/community/EOLUpgrades"). It's fairly easy for skilled users. Remember to use sudo when editing source files.
However, for most unskilled users, reinstalling may be easier.

Note that during a reinstall, Ubuntu will try to preserve users' /home directory (including email, contact, etc) as long as you don't reformat the data out of existence.
Backups are definitely your friend.

---

### Post by dragonfly41 on 2018-01-21
If you are at this stage more comfortable using Windows you might find Rufus helps
to answer your question ..

 > Now what do I do? I think I have to move it to a dvd but how? 
Remember I am a windows guy

[https://rufus.akeo.ie/](https://rufus.akeo.ie/)

---

### Post by Jack_Shankle on 2018-01-22
I am sorry but IMHO you have made Ubuntu 17.10.1 a BIG piece of commercial junk like Windows 10.
It would not let me use the settings from Ubuntu 17.04. I hate Firefox and Thunderbird. Not able
to install gmail which UMHO is great for email.
Now I have to go distro hunting to find a decent simple distro for my wife.
Sorry to burst your bubble.

---

### Post by coffeecat on 2018-01-22
> **Jack_Shankle said:**
> I am sorry but IMHO you have made Ubuntu 17.10.1 a BIG piece of commercial junk like Windows 10.

Who are you addressing?

The forum members, staff included, are all volunteers, overwhelmingly ordinary users such as yourself. The forum membership does not develop Ubuntu. Forum staff are not employed by Canonical.

In support threads please confine yourself to requests for help, or help for others, not rhetorical statements.

---

### Post by vasa1 on 2018-01-22
> **Jack_Shankle said:**
> I am sorry but IMHO you have made Ubuntu 17.10.1 a BIG piece of commercial junk like Windows 10.
It would not let me use the settings from Ubuntu 17.04. I hate Firefox and Thunderbird. Not able
to install gmail which UMHO is great for email.
Now I have to go distro hunting to find a decent simple distro for my wife.
Sorry to burst your bubble.
Weren't you interested in Ubuntu Mate and not Ubuntu? If so, visit [https://ubuntu-mate.org/download/](https://ubuntu-mate.org/download/).

Nobody "installs" gmail. It's a website accessible from any competent browser: [https://mail.google.com](https://mail.google.com).

---

### Post by Jack_Shankle on 2018-01-22
I am not addressing any member of this forum. I am strictly complaining about
Ubuntu 17.10.1. I will never let my wife use it.
So it's distro hunting again.

---

### Post by slickymaster on 2018-01-22
> **Jack_Shankle said:**
> I am not addressing any member of this forum. I am strictly complaining about
Ubuntu 17.10.1. I will never let my wife use it.
So it's distro hunting again.

With that remark and since plenty of good advises has been given, thread closed.

---

