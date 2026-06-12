---
title: "Email Passwords"
date: 2018-10-16
forum: General Help
---

### Post by Y^2om&amp;#7sgP on 2018-10-16
Sorry if this is in the wrong area, please move if it is.

Here's the issue, I am on Xubuntu 18.04 and use Thunderbird for emails..Just today, it has started to ask me for mail passwords.  I have entered them, clicked the save box, close, re-open and get asked for the passwords again.

I have tried this [https://forum.manjaro.org/t/troubleshooting-firefox/37158]("https://forum.manjaro.org/t/troubleshooting-firefox/37158")  applying it to Thunderbird, and have worked through each of the suggestions, but no joy, still prompts for passwords.

I seem to recall I had this issue some while back, and a re-build of the PC did the trick, but I'd rather not unless I have to.

Can anyone shed any light please?

Thank you in advance

---

### Post by ajgreeny on 2018-10-16
I suspect your configuration folder is corrupt in some minor way so you could try closing thunderbird then renaming the hidden **~/.thunderbird** folder in your home, and finally re-starting thunderbird.

You will need to re-enter all the configuration of both thunderbird and your email accounts, but if you use IMAP that should be quick and easy.

---

### Post by Y^2om&amp;#7sgP on 2018-10-18
Thanks for the suggestion ajgreeny, but sadly my main email account is pop3, my bad I should have put that in the question, sorry  :(

---

### Post by mastablasta on 2018-10-18
pop3 is not that good sine it pulls email form the server. it was good when we were using modems on phone line and server space was small. but not so much now. backup your emails to a different folder or disk (if you use cloud, encrypt it first), remove the account (or just rename it), and create a new one.

how to backup emails on TB: [https://support.mozilla.org/sl/questions/1171392](https://support.mozilla.org/sl/questions/1171392)

---

### Post by coffeecat on 2018-10-18
Before going for a nuclear option, there may be an easier solution. Googling shows that others have experienced your problem. A couple of links for you:

[https://support.mozilla.org/en-US/questions/1163427](https://support.mozilla.org/en-US/questions/1163427)

In Ubuntu, I see that in the "Troubleshooting Information" window of Thunderbird, what that help page refers to as Profile Folder, appears as Profile Directory, and "Show Profile" as "Open Directory". Of course, this being Linux, there's a quicker way to open that folder/directory. Simply open your home folder, make hidden files/folders visible. Open the .thunderbird folder, then the *random_string*.default folder, and there you will find the referenced  "cert8.db" and "key3.db" files. Caution: I have not tried this myself.

Another link:

[https://support.mozilla.org/en-US/questions/1172201](https://support.mozilla.org/en-US/questions/1172201)

Again, a minor difference in Ubuntu. To get to the config editor, the Thunderbird menu shows options as Preferences under edit. 

A third link which really doesn't add much:

[https://support.mozilla.org/en-US/questions/1145000](https://support.mozilla.org/en-US/questions/1145000)

And a passing thought. What you describe doesn't just happen without a reason. Password managers and CCleaner are mentioned as possible culprits in those links. Of course, CCleaner is a Windows only app, but are you using something similar such as bleachbit in Ubuntu? I have no idea whether this could be the underlying issue, but worth looking into.

---

### Post by HermanAB on 2018-10-18
This may not be what you want to hear, but Tbird losing the password and asking again for it, is the main reason why I stopped using it decades ago.  At the time, i concluded that the problem is not that Tbird lost the password, but that the connection times out and a logic error in Tbird, then causes it to prompt again for the password, instead of simply re-trying later.

---

### Post by amanchesterman on 2018-10-18
+1 to HermanAB's comment. I too found that if Thunderbird can't connect to the mail server it asks for the email password again -- which is often misleading, since the stored password is probably fine.

As a first step I would forget Thunderbird for a few minutes and sign in directly to your email account using the web page instead. Check that the account is working OK using the web interface (send a couple of test messages) before you try to open Thunderbird again.

---

### Post by Y^2om&amp;#7sgP on 2018-10-19
Thanks for the suggestions all.  Away now on vacation for a week, but will be looking again when I get back

---

### Post by Y^2om&amp;#7sgP on 2018-10-31
Well, having got back from vacation, I was able to do some testing.
Tried uninstalling, re-installing Thunderbird, no joy.
Install Windows 10 and Tbird.....restored mail files and everything works fine.  Re-installed Xubuntu and also Ubuntu, after restoring mail, fails again.
Looks to be a bug there :-(
So for now I'm running Windows 10, will try 'Buntu again in a few months
Thanks for all the suggestions

---

### Post by ra7411 on 2018-10-31
I had a similar problem a few days ago, but it was only some of my Gmail accts. that were doing it. I did some "security" pest operations and the problem went away.

---

### Post by oldos2er on 2018-10-31
> **hattpa said:**
> Tried uninstalling, re-installing Thunderbird, no joy.

For what it's worth, this recently happened to me too, although I use IMAP, not POP. I had to "mv" /home/user/.thunderbird/xxxxxxxx.default to a different folder, then restarted thunderbird to create a new profile using my existing password. This finally worked.

Removing and reinstalling thunderbird won't touch your user profile, which, at least for me, seemed to be where the problem was.

---

