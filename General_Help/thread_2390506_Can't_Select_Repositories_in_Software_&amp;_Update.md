---
title: "Can't Select Repositories in Software &amp; Updates"
date: 2018-04-29
forum: General Help
---

### Post by ndstate on 2018-04-29
Hello,

I cannot select any of the repositories via the GUI in a fresh install of 18.04. This includes Canonical Partners. The only ones that are currently selected were done via terminal. Any ideas? Thanks

[ATTACH=CONFIG]279490[/ATTACH]

---

### Post by Xian on 2018-04-29
Can you left click on the Canonical Partners repo and choose the option to Edit? 

Or does the Edit button remain greyed-out?

---

### Post by ndstate on 2018-05-02
The edit button is also greyed out.

---

### Post by deadflowr on 2018-05-02
When you select one of the entries like the Canonical Partners, what exactly happens?
(What should happen is a popup dialog box will appear and ask for your password )

---

### Post by ndstate on 2018-05-02
I cannot select any of the entries. When I try to select one the entire window goes gray.

---

### Post by PaulW2U on 2018-05-02
> **ndstate said:**
> I cannot select any of the entries. When I try to select one the entire window goes gray.
Interestingly that's what happens here too although I don't think that's always been the case. :confused:

Do you get prompted for your password  if you select any of the options on the other tabs?

If so, can you then select "Canonical Partners" if you go back to the "Other Software" tab after entering your password?

---

### Post by deadflowr on 2018-05-02
I wonder if you have Displays set up saying it has 2 monitors connected.
What happens sometimes is if your displays settings has two monitors active, then it sometimes runs dialog boxes in the second monitor.

This was something a few users ran into on 17.10.
But that was with regards to things like a Save As dialog box.
(You would click on gedit then use the save as function and the page would grey and the Save As dialog box would not show, since it would be on the other screen/monitor which was probably unplugged or turned off.)

Might be similar so check the display settings in system settings > devices.

Edit: this behavior is only on gnome-shell. (Ubuntu's default desktop)
No other desktop has this odd behavior.

---

### Post by PaulW2U on 2018-05-02
> **deadflowr said:**
> I wonder if you have Displays set up saying it has 2 monitors connected.
What happens sometimes is if your displays settings has two monitors active, then it sometimes runs dialog boxes in the second monitor.

I do have two monitors set up because I do have two monitors, both switched on.  :)

Just to clarify, I see the prompt for my password when selecting options on any tab but "Other Software" which would be a workaround for ndstate if he sees the same as I do.

Another oddity to throw into the mix - if I start "Software & Updates" from within synaptic then I can check/uncheck options on the "Other Software" tab without issue but of course I already input my password when starting synaptic. Strange.

---

### Post by ndstate on 2018-05-02
> **PaulW2U said:**
> I do have two monitors set up because I do have two monitors, both switched on.  :)

Just to clarify, I see the prompt for my password when selecting options on any tab but "Other Software" which would be a workaround for ndstate if he sees the same as I do.

Another oddity to throw into the mix - if I start "Software & Updates" from within synaptic then I can check/uncheck options on the "Other Software" tab without issue but of course I already input my password when starting synaptic. Strange.

Yes, this is what is happening on mine. Other tabs display the password prompt, if I enter it I can then edit the tab I have been having issues with. Seems to be a bug to me. What is the best way to report this? Besides us two, is anyone else having this issue?

---

### Post by PaulW2U on 2018-05-03
> **ndstate said:**
> Besides us two, is anyone else having this issue?
It looks like the issue has already been reported - [Unchecking or checkmarking sources in Software & Updates are not always possible]("https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/1759558"). I've confirmed the bug by marking it as affecting me too.

**Edit: **There seems to be a couple of duplicate bug reports. I think it's been an issue for some time. [https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/1727908](https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/1727908) is probably the bug report to watch.

---

### Post by ndstate on 2018-05-04
Thanks

---

### Post by sskayra on 2018-12-19
So... any update with this issue? I have the same problem and this is the reason why I joined the forum actually. Thanks.

---

### Post by PaulW2U on 2018-12-19
> **sskayra said:**
> So... any update with this issue?
If you mean this bug: [Software & Updates application does not permit changes on the "Other Software" tab]("https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/1727908"), unfortunately no.
Or are you experiencing something else?

---

### Post by mc4man on 2018-12-19
> **sskayra said:**
> So... any update with this issue? I have the same problem and this is the reason why I joined the forum actually. Thanks.

You'll need to use any of the workarounds, easiest is to just use a different tab to initiate authorization, then "Other" will work
(- only occurs in a ubuntu session, not an issue in a wayland session or any other session.

---

### Post by sskayra on 2018-12-24
> **PaulW2U said:**
> If you mean this bug: [Software & Updates application does not permit changes on the "Other Software" tab]("https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/1727908"), unfortunately no.
Or are you experiencing something else?

I have the same problem actually. When I try to select other options, whole window go blur/grey and doesn't allow me to do anything. When I tried to do some other operations, where it would ask my password, and when I enter my password I can select any of them without a problem. So it isn't really a problem for me anymore but kinda annoying.

---

