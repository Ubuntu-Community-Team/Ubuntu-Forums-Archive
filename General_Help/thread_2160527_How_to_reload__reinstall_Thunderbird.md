---
title: "How to reload / reinstall Thunderbird"
date: 2013-07-07
forum: General Help
---

### Post by Gordonisnz on 2013-07-07
QUERY1 : How / who do we contact to get a new sub-forum added to this website ?


[LIST]
[*][Forum]("http://ubuntuforums.org/index.php")
[*][The Ubuntu Forum Community]("http://ubuntuforums.org/forumdisplay.php?f=130")
[*][Ubuntu General Support  ]("http://ubuntuforums.org/forumdisplay.php?f=327")
[*](NEW FORUM)
[/LIST]

MAIN QUERY :-

Hello.

Recently - we (a number of us) are getting similar errors / problems when trying to access emails on a particular website/domain (thunderbird). We cant send emails.

the latest error message i'm getting is :-  An error occurred while sending mail. The mail server responded:  Temporary local problem - please try later. Please check the message and try again.


QUERY: what is the command line i use to totally remove Thunderbird from my system (NOTHING kept), and then the command line to re-install thunderbird (I've saved my passwords & i'll re-add those later.

Will re-installing my thunderbird help in the above error message ?

UBUNTU: Release 12.04 (precise) 64-bit
GNOME 3.4.2

---

### Post by Zill on 2013-07-07
> **Gordonisnz said:**
> ...How / who do we contact to get a new sub-forum added to this website ?...
[Forum Feedback & Help]("http://ubuntuforums.org/forumdisplay.php?f=48")

> **Gordonisnz said:**
> ...Recently - we (a number of us) are getting similar errors / problems when trying to access emails on a particular website/domain (thunderbird). We cant send emails.

the latest error message i'm getting is :-  An error occurred while sending mail. The mail server responded:  Temporary local problem - please try later. Please check the message and try again...
Looks to me like the clue is in the error message. ;-)  If there is a problem with the mail server then this has nothing to do with Ubuntu or Thunderbird.  The mail server is run by either your ISP or a third-party such as Google.
> **Gordonisnz said:**
> ...what is the command line i use to totally remove Thunderbird from my system (NOTHING kept), and then the command line to re-install thunderbird (I've saved my passwords & i'll re-add those later...
```
sudo apt-get purge thunderbird
rm ~/.thunderbird -r
sudo apt-get install thunderbird
```
> **Gordonisnz said:**
> ...Will re-installing my thunderbird help in the above error message ?
Probably not!

---

