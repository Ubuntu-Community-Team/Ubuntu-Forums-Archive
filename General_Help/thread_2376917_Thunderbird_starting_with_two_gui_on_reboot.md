---
title: "Thunderbird starting with two gui on reboot"
date: 2017-11-07
forum: General Help
---

### Post by makem2 on 2017-11-07
Since a re-install of xubuntu (16.04) I am experiencing two thunderbird instances at each re-boot.

One, I assume the second one, complains that another is busy. If I close the one I think is the second one then at least some of the parts such as the calender may not work if I have chosen the wrong instance. I must close that gui and open thunderbird from the menu.

I always install xubuntu with it's own /home so the setting which is causing this is probably in that directory.

I could completely un-install the program but that would lose all my history would it not? Maybe I could save the .thunderbird directory and import after a re-install?

---

### Post by speartip on 2017-11-07
If your Email account is using the IMAP protocol, which most are these days, then deleting your profile (the .thunderbird folder in your home folder) will not delete your History. It will pick it up again from your email account the minute you set it up again.
 An easier way is rename the .thunderbird folder to say .thunderbird_old, then reboot & see if all is ok. You may just have a corrupt profile.

---

### Post by deadflowr on 2017-11-07
Sounds like you have both a saved session and a startup application running.
A save session will restart running apps, and the startup applications is set to start particular apps at login.
So you end up with multiple instances of an app running at login.
Look in sessions and startup, if that still exists.

---

### Post by makem2 on 2017-11-07
> **deadflowr said:**
> Sounds like you have both a saved session and a startup application running.
A save session will restart running apps, and the startup applications is set to start particular apps at login.
So you end up with multiple instances of an app running at login.
Look in sessions and startup, if that still exists.

I have an entry in Auto Start and also and entry in Session. I cleared saved sessions but it had no effect on re-boot, same dual gui appeared.

What you said makes sense but the 'session' is just an option to save a session and if I have cleared the saved sessions it shouldn't happen.

---

### Post by makem2 on 2017-11-07
> **speartip said:**
> If your Email account is using the IMAP protocol, which most are these days, then deleting your profile (the .thunderbird folder in your home folder) will not delete your History. It will pick it up again from your email account the minute you set it up again.
 An easier way is rename the .thunderbird folder to say .thunderbird_old, then reboot & see if all is ok. You may just have a corrupt profile.

I use IMAP on my travel pc an phone but on my main pc I use POP so nothing left on the server.

I am not concerned about the emails say for the last few days, it is the history over years of travel and links to information for repeat journeys I need to ensure I keep. I will have to look more closely into import options I think, In Windows I could choose what to import but never needed to check in linux. It may be just a case of saving the data from the profile directory and complete removal followed by re-install then overwrite the part of the profile with the data required.

---

### Post by makem2 on 2017-11-07
> **speartip said:**
> If your Email account is using the IMAP protocol, which most are these days, then deleting your profile (the .thunderbird folder in your home folder) will not delete your History. It will pick it up again from your email account the minute you set it up again.
 An easier way is rename the .thunderbird folder to say .thunderbird_old, then reboot & see if all is ok. You may just have a corrupt profile.

I also tried the rename and reboot method to be able to copy the data from the old file to the newly made one. After a re-boot as expected, a new instance of Thunderbird started from the beginning and asking if you would like a new email address. This when you would copy the old data to the new and re=boot. However, along with the new Thunderbird there appeared the Thunderbird Accounts page (an earlier page than the one already opened up as it did not contain the 'Want to make an new email address' option.

I deleted the new .thunderbird directory and reinstated the old one.

So, the cause of this dual gui is outside the profile in my opinion.

---

### Post by #&amp;thj^% on 2017-11-07
@makem2 when that happens try closing them with keyboard combo>>(alt+F4) then reopen thunderbird.
Fingers crossed.

---

### Post by ajgreeny on 2017-11-07
I think it would also make sense, for now at least, to remove T'Bird from your startup applications list to see if it still starts at boot or start of a new session; that will at  the very least give us more info about what part of your setup is starting T'Bird each time.

---

### Post by makem2 on 2017-11-07
> **ajgreeny said:**
> I think it would also make sense, for now at least, to remove T'Bird from your startup applications list to see if it still starts at boot or start of a new session; that will at  the very least give us more info about what part of your setup is starting T'Bird each time.

It did not start after removing it from the startup applications.

It did start extremely quickly when I then selected it.

Leaving it open and rebooting brought one instance up. If it stays that way then I will be satisfied as I always leave windows open that I regularly use (3)

---

### Post by makem2 on 2017-11-07
> **1fallen said:**
> @makem2 when that happens try closing them with keyboard combo>>(alt+F4) then reopen thunderbird.
Fingers crossed.

Having removed the startup entry from auto start I cannot now try your suggestion.

However, previously I would close both gui and the restart thunderbird when I had chosen the wrong instance to close. I started just closing both and restarting as it was quicker.

Would using the keyboard combo have had a different effect to just using the 'X' to close? If so I will replace the auto startup and try it.

---

### Post by makem2 on 2017-11-07
Since the re-install I have noticed an emty terminal window pop up and immediately close as the desktop starts. It is the first thing that appears In all the time I have use xubuntu I have never seen such a window,

I have not yet re-installed all the software I had installed previously and assume it is related to remaining settings in /home for as yet software that is not installed. I re-install as and when needed.

I doubt this will have any bearing on the dual gui.

---

### Post by #&amp;thj^% on 2017-11-07
> **makem2 said:**
> 
Would using the keyboard combo have had a different effect to just using the 'X' to close? If so I will replace the auto startup and try it.
It did for me. If I remember correctly this happened on 16.04 Mate, also using a backed up Home Directory restore.
In theory, there can be a difference. The File menu is completely under the application's control. What items appear in it and what happens if those items are invoked is application-specific. The author of the application could run completely different code when clicking Exit on the File menu than the one that would run when you use Alt+F4.
But looks like you are now satisfied by removing it from Auto Start.
All's well that ends well. :)

---

### Post by #&amp;thj^% on 2017-11-07
> **makem2 said:**
> Since the re-install I have noticed an emty terminal window pop up and immediately close as the desktop starts. It is the first thing that appears In all the time I have use xubuntu I have never seen such a window,
I doubt this will have any bearing on the dual gui.
I see that flash by also on ubuntu.
Your right about not having any bearing with the Dual UI...as I no longer use Thunderbird and I still see it flash by.
Kind regards

---

### Post by makem2 on 2017-11-07
I am thinking I can mark this thread solved with the proviso that it is necessary to leave Thunderbird open (can be minimized) before reboot to have it start up automatically. Also that the entry, if any in auto start up is unchecked.

It does solve the two instances of Thunderbird running on reboot.

---

### Post by makem2 on 2017-11-07
> **1fallen said:**
> I see that flash by also on ubuntu.
Your right about not having any bearing with the Dual UI...as I no longer use Thunderbird and I still see it flash by.
Kind regards

May I ask what you use instead of Thunderbird?

---

### Post by #&amp;thj^% on 2017-11-07
Certainly>>>Seamonkey : [https://apps.ubuntu.com/cat/applications/natty/seamonkey-browser/](https://apps.ubuntu.com/cat/applications/natty/seamonkey-browser/)
EDIT: Now I'm wondering if you also have save the current session enabled, that would explain 2 instances of thunderbird,

---

