---
title: "Stop sound after Seamonkey starts"
date: 2017-02-11
forum: General Help
---

### Post by raleigh3 on 2017-02-11
Whenever I start Seamonkey I hear this irritating sound.

Is there a way to stop it ?

---

### Post by &amp;KyT$0P# on 2017-02-11
> **raleigh3 said:**
> Whenever I start Seamonkey I hear this irritating sound.
What version of SeaMonkey?
What sound?

What page(s) are opened when you start SeaMonkey?
What SeaMonkey extensions do you have?

Also, what version and flavor of Ubuntu are you using?

---

### Post by raleigh3 on 2017-02-11
> **halogen2 said:**
> What version of SeaMonkey?
What sound?

What page(s) are opened when you start SeaMonkey?
What SeaMonkey extensions do you have?

Also, what version and flavor of Ubuntu are you using?

Sounds like A quick drum sound.

Seamonkey 2.46 opens a customized yahoo search page.

I have Reminder Fox and Shockwave Flash as addons.

Using Ubuntu-Mate 16.04.

The problem is with ReminderFox extension.

It has an option to turn off a sound for my reminders.

But when I try to turn it off, it returns when I start Seamonkey.

Do you think it is some permission issue ?

---

### Post by &amp;KyT$0P# on 2017-02-11
To be clear, does your change to that setting persist after restarting SeaMonkey?  Or does it revert back to "sound on"?

If the change sticks, and the sound is playing anyway, I suggest you [contact their support]("https://addons.mozilla.org/seamonkey/addon/reminderfox/").

---

### Post by raleigh3 on 2017-02-11
The sound reverts back to sound on.

I found a workaround.

I used Audacity to record a "silent wave file."

I put it into usr/share/sounds directory.

I then choose it as a custom sound file.

---

### Post by &amp;KyT$0P# on 2017-02-11
> **raleigh3 said:**
> The sound reverts back to sound on.
Do you have a [user.js file]("http://kb.mozillazine.org/User.js_file") or [lockpref file]("http://kb.mozillazine.org/Locking_preferences")?

---

