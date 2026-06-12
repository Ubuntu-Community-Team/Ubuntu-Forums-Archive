---
title: "How do I stop daily software updates?"
date: 2014-05-14
forum: General Help
---

### Post by ExNASATerry on 2014-05-14
I think I've had this problem in every version of Ubuntu I've run (starting 5 years ago with 9.04). I set the Software Updates to "Weekly" or "Every 2 weeks" and it still wants to update every single day.


I inevitably end up turning them off entirely; not an optimal solution.


So, how do I set the updates to be weekly or bi-weekly?

---

### Post by monkeybrain20122 on 2014-05-14
Maybe security updates? And what's wrong with running daily updates? It is not like in Windows that you have to reboot a hundred times, it is unintrusive and all you need to do is to push a button. Personally I manual update with synaptic everyday.

---

### Post by MartyBuntu on 2014-05-14
You don't have to accept the update just because you get the notification...

---

### Post by pretty_whistle on 2014-05-14
Weird that it is checking daily instead of what you set it to.  Maybe going into settings and setting it again would work....but it sounds like you have and it's not working.  Am I right?

I have mine set to never check automatically for updates so I cant offer anything else on your issue.  :(

---

### Post by mastablasta on 2014-05-15
mine is not checked automatickly on notebook. otherwise it's check. if it's not working when you change it to check every two weeks then it must be a bug/error.

---

### Post by slickymaster on 2014-05-15
> **ExNASATerry said:**
> I think I've had this problem in every version of Ubuntu I've run (starting 5 years ago with 9.04). I set the Software Updates to "Weekly" or "Every 2 weeks" and it still wants to update every single day.


I inevitably end up turning them off entirely; not an optimal solution.


So, how do I set the updates to be weekly or bi-weekly?

Hi ExNASATerry, welcome to the forums.

Regarding your question, and please don't take me wrong, but I'm assuming that you did already defined how often you’d like the update manager to check for updates via the drop-down menu in the Updates tab of the Software Sources, right?

---

### Post by ExNASATerry on 2014-05-15
> **slickymaster said:**
> Hi ExNASATerry, welcome to the forums.

Regarding your question, and please don't take me wrong, but I'm assuming that you did already defined how often you’d like the update manager to check for updates via the drop-down menu in the Updates tab of the Software Sources, right?

Yes, under Software Sources | Updates | "Automatically check for updates" the options are "Daily, Every two days, Weekly, Every two weeks, and Never." I have mine set to Never (which works), because "Weekly" and "Every two weeks" do not. And never have, going back to 9.04, if I remember correctly.

As to "why": it doesn't matter. The options are there; they should work or be removed.

---

### Post by btindie on 2014-05-16
I've got exactly the same problem. Mine's set to 'Never' yet it starts every time I turn my laptop on and I find it infuriating. I prefer to do it manually using apt-get.

Running 12.04.4

---

### Post by pretty_whistle on 2014-05-16
Software Updater can be uninstalled since it's not working right.  If I were having problems I'd just remove it.  Some dont know it can be uninstalled but it can.

Hope that helps.

---

### Post by mcduck on 2014-05-16
The updates are supposed to be checked daily, no matter what option you select, as any important security updates are displayed to the user as soon as possible.

The option sets how often the update manager will display available updates to the user (as long as they are only normal, low-priority updates).

Of course if the Update manager actually pops up every day regardless of what the option is set to, and you don't have any PPA or other third-party repository that might be sending daily security updates, then something is broken. But at least update manager process running daily regardless of the option is working as intended...

---

### Post by monkeybrain20122 on 2014-05-16
Use lubuntu. Update manager never starts there because of a bug. :)

---

### Post by bapoumba on 2014-05-16
> **monkeybrain20122 said:**
> Use lubuntu. Update manager never starts there because of a bug. :)
:lol:

---

